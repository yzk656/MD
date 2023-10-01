查看工作区状态：

```java
git status
```

将所有文件提交到暂存区

```
git add -A
```

将暂存区的文件提交到本地仓库

```java
git commit -m ‘first commit’
```

将本地仓库提交到远程仓库

```java
git push origin master
```

如果本地仓库中部分文件删除，导致远程仓库和本地仓库代码不一致

```
git pull -rebase ori
```

## fatal: Authentication failed for 'https://github.com/yzk656/MD.git/'

这个错误消息表明在尝试克隆 GitHub 仓库时出现了身份验证问题，并且指示不再支持使用密码身份验证。GitHub 于 2021 年 8 月 13 日停止了对密码身份验证的支持，因此你需要使用个人访问令牌（Personal Access Token）来进行身份验证。

要解决这个问题，你可以按照以下步骤使用个人访问令牌来进行克隆操作：

1. **生成个人访问令牌**：

   在 GitHub 上生成一个个人访问令牌，以便用于身份验证。要生成令牌，请执行以下步骤：

   - 登录到你的 GitHub 帐户。
   - 点击右上角的用户头像，然后选择 "Settings"（设置）。
   - 在左侧导航栏中，选择 "Developer settings"（开发者设置）。
   - 在 "Personal access tokens"（个人访问令牌）部分，点击 "Generate token"（生成令牌）。
   - 在生成令牌页面上，选择所需的权限和范围，然后点击 "Generate token"（生成令牌）。
   - 将生成的令牌复制到剪贴板。请注意，生成的令牌只会显示一次，所以确保在复制之前将其保存在安全的位置。

2. **使用个人访问令牌进行克隆**：

   打开命令行终端，并运行以下命令来使用个人访问令牌进行克隆操作。将 `<personal-access-token>` 替换为你生成的个人访问令牌，并 `<repository-url>` 替换为要克隆的仓库的 URL：

   ```bash
   git clone https://<personal-access-token>@github.com/yzk656/MD.git
   ```

   例如：

   ```bash
   git clone https://your-personal-access-token@github.com/yzk656/MD.git
   ```

3. 这将使用个人访问令牌来进行身份验证，并允许你成功克隆 GitHub 仓库。

请确保在复制个人访问令牌时将其保存在安全的地方，并不要分享或泄露给他人，因为它允许访问你的 GitHub 账户。使用个人访问令牌是一种更安全和推荐的方式，以满足 GitHub 的新的身份验证标准。

例子：

```js
git clone https://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@github.com/yzk656/MD.git
```

