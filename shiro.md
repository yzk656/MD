![image-20230913072446367](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130724460.png)

![image-20230913072558520](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130725672.png)

![image-20230913072700232](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130727317.png)

![image-20230913073452570](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130734650.png)

## 登录认证

![image-20230913073628642](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130736690.png)

![image-20230913073636524](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130736581.png)

![image-20230913073743034](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130737141.png)

```java
package com.yzk.shiro;

import org.apache.shiro.SecurityUtils;
import org.apache.shiro.authc.*;
import org.apache.shiro.config.IniSecurityManagerFactory;
import org.apache.shiro.mgt.SecurityManager;
import org.apache.shiro.subject.Subject;

public class ShiroRun {
    public static void main(String[] args) {
        //1. 获取SecurityManger
        IniSecurityManagerFactory factory=new IniSecurityManagerFactory("classpath:shiro.ini");
        SecurityManager securityManager = factory.getInstance();
        SecurityUtils.setSecurityManager(securityManager);
        //2. 获取Subject对象
        Subject subject = SecurityUtils.getSubject();
        //3. 创建token对象，web应用用户名和密码从页面传递
        AuthenticationToken token=new UsernamePasswordToken("zhangsan1","z3");
        //4. 完成登录
        try {
            subject.login(token);
            System.out.println("登录成功");
        } catch (UnknownAccountException e) {
            e.printStackTrace();
            System.out.println("用户不存在");
        }catch (IncorrectCredentialsException e){
            e.printStackTrace();
            System.out.println("密码错误");
        }catch (AccountException e){
            e.printStackTrace();
        }
    }
}
```

![image-20230913080111591](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130801673.png)

## 授权

![image-20230913080231560](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130802656.png)

![image-20230913080310572](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130803621.png)

![image-20230913080336965](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130803008.png)

![image-20230913080342229](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130803263.png)

![image-20230913080355299](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130803334.png)

![image-20230913080518142](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130805212.png)

![image-20230913080437007](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309130804125.png)

## 加密

```java
package com.yzk.shiro;

import org.apache.shiro.crypto.hash.Md5Hash;

public class ShiroMD5 {
    public static void main(String[] args) {
        String password = "z3";
        Md5Hash md5Hash = new Md5Hash(password);
        System.out.println(md5Hash);

        /*带盐加密*/
        Md5Hash md5Hash1 = new Md5Hash(password, "salt");
        System.out.println(md5Hash1);

        /*多次加密*/
        Md5Hash md5Hash2 = new Md5Hash(password, "salt",3);
        System.out.println(md5Hash2);
    }
}
```

## SpringBoot整合



```
/**
 * 由于这里是跳转页面，因此要去掉responsebody，也就是restController改为controller
 */
 
 @Controller
@RequestMapping("/user")
public class UserController {

    @GetMapping("/userLogin")
    public String UserLogin(String name, String pwd, HttpSession session){
       //获取subject对象
        Subject subject = SecurityUtils.getSubject();
        //封装请求数据到token
        UsernamePasswordToken token = new UsernamePasswordToken(name, pwd);
        try {
            //调用login
            subject.login(token);
            session.setAttribute("user",token.getPrincipal().toString());
            return "main";
        } catch (AuthenticationException e) {
            e.printStackTrace();
            return "登录失败";
        }
    }


    @GetMapping("/login")
    public String login(){
        return "login";
    }
}
```

## anon

在这段代码中，"anon" 是一个 Shiro 框架中用于配置权限的特殊字符串，表示匿名用户可以访问的资源，即不需要进行身份认证就可以访问的资源。

在 Shiro 中，您可以通过配置路径定义来指定哪些路径需要进行身份认证，哪些路径可以匿名访问。通过将路径和相应的权限要求关联起来，Shiro 可以根据用户的身份和权限来控制对这些资源的访问。

在您的示例中，"/user/userLogin" 和 "/login" 这两个路径被配置为 "anon"，这意味着任何用户，无论是否已经进行了身份认证，都可以访问这两个路径的资源而无需登录或提供任何身份验证凭据。通常，这些路径可能用于用户登录页面或其他不需要身份验证的公共页面。

## 多个realm代码实现

![image-20230915080844672](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309150808773.png)

![image-20230915080932036](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309150809093.png)

![image-20230915081136692](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309150811778.png)

![image-20230915081452369](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309150814458.png)

## 过滤器配置

是的，这段代码是用于配置Shiro的过滤器链（filter chain）的部分代码。在Shiro中，过滤器链用于定义不同URL路径的访问规则，包括哪些路径需要进行认证（登录）以及哪些路径可以匿名访问。

让我解释一下这段代码的作用：

1. `DefaultShiroFilterChainDefinition` 是一个用于定义Shiro过滤器链的类。

2. `definition.addPathDefinition("/user/userLogin", "anon")` 和 `definition.addPathDefinition("/user/login", "anon")` 配置了两个路径 `/user/userLogin` 和 `/user/login`，这些路径被设置为 "anon"，表示它们是匿名访问的，不需要进行认证，即不需要登录就可以访问。

3. `definition.addPathDefinition("/**", "authc")` 配置了通配符路径 `"/**"`，表示所有的路径都需要进行认证（authc），也就是说，用户需要登录才能访问应用程序的其他路径。

4. `definition.addPathDefinition("/**", "user")` 配置了通配符路径 `"/**"`，表示所有的路径都会触发一个名为 "user" 的过滤器。通常情况下，这是用于实现"rememberMe"功能的过滤器，以便保持用户的登录状态。

总之，这段代码配置了一个通用的过滤器链，规定了哪些路径需要认证登录，哪些路径可以匿名访问，并且添加了一个用于保持用户登录状态的过滤器。您可以根据您的应用程序需求进行进一步的定制和扩展。



## 安全管理器什么时候会被调用

这个安全管理器通常会在您的应用程序启动时被调用和配置。具体来说，它被用来设置Shiro的安全策略和认证/授权规则，以确保在用户访问应用程序时提供安全性和身份验证支持。

以下是一般的流程：

1. **Shiro配置类**：这段代码通常位于您的Shiro配置类中，该配置类可能使用Spring的 `@Configuration` 注解进行标记，以便在应用程序启动时被Spring容器加载和初始化。

   ```java
   @Bean
   public DefaultWebSecurityManager defaultWebSecurityManager() {
       // ... 这里的代码
   }
   ```

   这个方法名 `defaultWebSecurityManager()` 可能是通过注解 `@Bean` 暴露为Spring Bean 的，因此Spring会在应用程序启动时调用该方法以创建和配置 `DefaultWebSecurityManager` 对象。

2. **配置安全策略**：在 `defaultWebSecurityManager()` 方法中，您创建了 `DefaultWebSecurityManager` 对象，并配置了安全策略。这包括设置密码加密算法、定义认证和授权规则、配置"rememberMe"管理器等。

3. **设置Realm**：您将自定义的 `myRealm` 对象与 `DefaultWebSecurityManager` 相关联。`myRealm` 通常包含了用于验证和授权的逻辑，因此 `DefaultWebSecurityManager` 将使用它来执行认证和授权操作。

4. **设置"rememberMe"管理器**：您还设置了"rememberMe"管理器，以启用"rememberMe"功能。

一旦安全管理器被配置和创建，它将在整个应用程序的生命周期内保持活动状态，并在每次用户请求需要进行认证和授权的资源时被调用。当用户访问受保护的资源时，Shiro会使用安全管理器来执行相关的认证和授权逻辑，以验证用户的身份并控制其访问权限。

总之，安全管理器是Shiro中的关键组件，用于管理应用程序的安全性和身份验证。它通常在应用程序启动时被初始化，然后在整个应用程序的生命周期内用于处理安全相关的操作。

## 这段cookie信息是保存在服务器端了吗

不，这段代码中配置的Cookie信息并没有保存在服务器端。相反，它们是用于在客户端（通常是浏览器）上创建和管理Cookie的设置。

具体来说，这段代码配置了"rememberMe"功能所需的Cookie属性，如名称、路径、过期时间等。当用户登录时，Shiro会生成一个"rememberMe" Cookie，并将其发送到用户的浏览器，以便在用户下次访问应用程序时记住其登录状态。这个Cookie会在用户的浏览器中存储，而不是在服务器端。

服务器端通常不会保存"rememberMe" Cookie的具体信息，而是依靠浏览器在每次请求时发送该Cookie，然后由Shiro解析和验证该Cookie以维护用户的登录状态。Cookie中包含的信息是经过加密的，以确保安全性。

总之，这段代码配置的Cookie信息是用于在用户的浏览器中创建和管理Cookie，以实现"rememberMe"功能，而不是在服务器端保存Cookie信息。服务器端主要用于处理和验证这些Cookie。

## 授权，角色认证

![image-20230915204142312](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309152041416.png)

![image-20230915204156827](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309152041886.png)

![image-20230915204321912](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309152043008.png)

![image-20230915204412659](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309152044719.png)

## 前端页面授权

![image-20230916005202204](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309160052307.png)

![image-20230916010907844](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309160109910.png)

![image-20230916010933053](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309160109822.png)

![image-20230916011023202](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309160110270.png)

![image-20230916011056472](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309160110513.png)

## shiro过滤器链

在Apache Shiro中，`DefaultShiroFilterChainDefinition`对象用于配置URL路径的访问规则，这些规则定义了哪些URL路径需要进行认证，哪些URL路径可以匿名访问，以及哪些URL路径需要进行用户身份验证。Shiro会按照配置规则逐一匹配URL路径，然后根据第一个匹配的规则来执行相应的操作。所以在配置过滤器链时，确实有顺序要求。

根据你提供的配置代码，你的过滤器链中有一些顺序要求：

1. `/user/userLogin` 和 `/user/login` 这两个路径被配置为可以匿名访问（"anon"），这意味着不需要认证即可访问。这两个规则应该在下面的规则之前。

2. `/logout` 路径被配置为执行注销操作（"logout"），这也是一个特殊的规则，通常应该放在匿名访问规则之后。

3. `/login.html` 被配置为可以匿名访问（"anon"），这也应该在下面的规则之前。

4. 最后，`/**` 被配置为需要进行用户身份验证（"authc"）和存在用户（"user"）。这两个规则是通配规则，匹配所有未被上述规则匹配的URL路径。所以它们应该放在最后。

总的来说，规则的配置顺序应该是：

1. `/user/userLogin` 和 `/user/login`：匿名访问规则
2. `/logout`：注销规则
3. `/login.html`：匿名访问规则
4. `/**`：用户身份验证规则和存在用户规则

确保按照这个顺序配置过滤器链，以确保规则按照期望的方式触发和执行。

## 会话管理

![image-20230916113225495](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161132592.png)

![image-20230916113506928](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161135016.png)

![image-20230916113513992](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161135035.png)

![image-20230916113613864](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161136939.png)
