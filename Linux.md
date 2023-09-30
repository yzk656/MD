# Linux

## Linux入门

1. cd 文件名：进入某个文件‘

2. 回退

   ```
   cd ..                  返回上一级目录
   
   cd ../..               返回上两级目录
   
   cd或cd ~           返回home目录
   
   cd - 目录名       返回指定目录
   ```

   

3. 显示当前文件下的绝对路径：PWD

   ```
   [yangzhenkun@localhost work1]$ pwd
   /home/yangzhenkun/Study/home/guestuser1/work1
   ```

4. 创建文件

   Linux创建文件可以使用的命令有：**vi/vim、touch、echo**。

   ```
   yangzhenkun@localhost work1]$ touch file1.txt
   ```

5. cp 用于复制文件或目录。

   参数说明：

   -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合。
   -d：复制时保留链接。这里所说的链接相当于Windows系统中的快捷方式。
   -f：覆盖已经存在的目标文件而不给出提示。
   -i：与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖。
   -p：除复制文件的内容外，还把修改时间和访问权限也复制到新文件中。
   -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
   -l：不复制文件，只是生成链接文件。

   案例1：

   ```
   cp flags.c flags_checkered.c
   //复制 flags.c 到flags_checkered.c 文件，当前文件同属于同一目录下
   ```

   ```
   [yangzhenkun@localhost guestuser1]$ cp -r work1/. work2   [把work1下面的文件复制到work2文件]
   ```

   

6. 修改密码：[yangzhenkun@localhost ~]$ passwd

7. 列出所有目录：[yangzhenkun@localhost ~]$ ls -l【**注意**：这里的条目以d.....开头代表目录。例如，`usr`、`cjavapy`、`python`和`java`是目录，其余的条目是文件。】

8. 清屏：clear

## Linux文件管理

1. 显示更多信息：[yangzhenkun@localhost ~]$ ls -l

2. 元字符：元字符在Linux中有特殊的含义。例如，`*`和`?`元字符。`*`用于匹配`0`个或多个字符，问号(`?`)用于匹配单个字符。

   ```
   [yangzhenkun@localhost ~]$ ls Stud*
   home  Software
   [yangzhenkun@localhost ~]$ ls Stud?
   home  Software
   ```

3. 列出隐藏文件：

   ```
   [yangzhenkun@localhost ~]$ ls -a
   .   .bash_history  .bash_profile  .cache   .dbus      .ICEauthority  .local    .pki     Study  公共  视频  文档  音乐
   ..  .bash_logout   .bashrc        .config  .esd_auth  .lesshst       .mozilla  .redhat 
   ```

4. 在Linux系统上创建文件[yangzhenkun@localhost ~]$ vi temp_file

   1）按下esc键以退出编辑模式。

   2）按两个键Shift + ZZ就可以保存并且退出vi

   3）现在，将在当前目录中创建一个具有filename的文件。

   编辑文件的话：直接通过vi temp_file打开文件直接编辑就行

5. 显示文件内容

   [yangzhenkun@localhost ~]$ cat temp_file
   hello Linux;

   带行号的显示：

   [yangzhenkun@localhost ~]$ cat -b temp_file
        1	hello Linux;

6. 复制文件

   [yangzhenkun@localhost ~]$ cp temp_file text1
   [yangzhenkun@localhost ~]$ cat text1
   hello Linux;

   在当前目录下创建文件副本

   [yangzhenkun@localhost ~]$ cp temp_file copy_file

   [yangzhenkun@localhost ~]$ cat copy_file
   hello Linux;

7. 文件重命名

   [yangzhenkun@localhost ~]$ mv copy_file new_file
   [yangzhenkun@localhost ~]$ cat -b new_file
        1	hello Linux;

8. 删除文件

   [yangzhenkun@localhost ~]$ rm new_file
   [yangzhenkun@localhost ~]$ cat new_file
   cat: new_file: 没有那个文件或目录

9. 删除文件夹

   在 Linux 系统中删除文件，最常用的命令就是 rm 命令。这个命令相信大家都已经很熟悉了，我们来简单回顾一些 rm 命令的例子。

   > $ rm -f testfile1

   -f 选项在上面的命令中，表示将在不要求确认的情况下强行删除文件。

   > $ rm -rf testdirectory

    这个命令将删除名为 testdirectory 的目录以及该目录中的所有内容（使用的 -r 选项是递归删除文件）。
   而删除目录，我们还有另一个命令，那就是 rmdir ，但是它只有在目录为空时才会删除该目录。

   > $ rmdir testdirectory

## Linux目录管理

1. home目录

   进入主目录：cd ~

   进入其他用户的主目录：cd ~username

   返回**上一次的工作目录**：cd -

   返回上一级目录：cd ..

2. 绝对/相对路径

   目录以根(`/`)在顶部的层次结构排列。任何文件在层次结构中的位置都由其路径名描述

   路径名的元素之间用"`/`"分隔。路径名是绝对的，它是与根相关的，则绝对路径总是以`/`开头。

   绝对文件名如下，

   ```、
   /etc/passwd
   /users/levi/cjavapy
   /dev/vda1/python
   ```

   确定当前位置

   ```
   [yangzhenkun@localhost Study]$ pwd
   /home/yangzhenkun/Study
   ```

   列出当前目录的文件

   ```
   [yangzhenkun@localhost Study]$ ls
   home  Software
   ```

3. 创建目录

   ```
   [yangzhenkun@localhost guestuser1]$ mkdir temp_file
   [yangzhenkun@localhost guestuser1]$ ls
   temp_file  work1  work2
   ```

   创建多个文件夹

   ```
   [yangzhenkun@localhost guestuser1]$ mkdir temp_file1 temp_file2
   ```

   切换用户

   命令： su 指定要切换的用户，如：

   su            # 默认切换到 root 用户上

   su root        # 切换到 root 用户

   su taita       i# 切换到 taitai 用户上

   ```
   [root@localhost ~]# su yangzhenkun
   [yangzhenkun@localhost root]$ 
   ```

   改变当前目录

   ```
   [root@localhost ~]# su yangzhenkun
   [yangzhenkun@localhost root]$ cd ~
   [yangzhenkun@localhost ~]$ 
   ```

​	进入某个文件夹不需要使用**/**

```
[yangzhenkun@localhost ~]$ cd Study/home/
[yangzhenkun@localhost home]$ 
```

==最终==

在当前文件夹下创建1个多级文件夹【前提是必须存在路径上的目录】

```
[root@localhost guestuser1]# mkdir temp_file/temp1
[root@localhost guestuser1]# ls temp_file
temp1
```

4. 删除目录

   ```
   [root@localhost guestuser1]# rmdir temp_file/temp1
   [root@localhost guestuser1]# ls temp_file
   [root@localhost guestuser1]# 
   ```

   rmdir:目录为空时，才能删除目录

   ```
   [root@localhost guestuser1]# rmdir temp_file
   rmdir: 删除 "temp_file" 失败: 目录非空
   
   
   [root@localhost guestuser1]# rmdir temp_file1
   [root@localhost guestuser1]# [temp_file1是个空文件夹]
   ```

   

   rm：直接删除目录，无序确认【需要添加-rf】

   ```
   [root@localhost guestuser1]# rm -rf temp_file
   [root@localhost guestuser1]# 
   ```

5. 创建父目录【多级文件夹】

   ```
   [root@localhost guestuser1]# mkdir -p temp_file/temp1
   [root@localhost guestuser1]# 
   ```

6. 切换目录

   ```
   [root@localhost guestuser1]# cd temp_file/temp1
   [root@localhost temp1]# 
   ```

7. 重命名目录【多级目录一样也可以】

   ```
   [root@localhost guestuser1]# mv temp_file/temp1 temp_file/temp
   [root@localhost guestuser1]# 
   ```

8. 目录（.）和（..）

   目录列表中(`.`)表示当前工作目录，目录列表中(`..`)表示当前工作目录之上一级的目录，通常称为父目录。

   如果输入命令显示当前工作目录`/`文件的列表，并使用`-a`选项列出所有文件，使用`-l`选项提供长列表，如果如下：

   ```
   $ ls -la
   drwxrwxr-x    4    levi   class   2121  Jul 11 17.03 .
   drwxr-xr-x    60   root              1036  Jul 12 11:08 ..
   ----------    1    levi   class   5210  May 1 08:27 .bash_profile
   -rwxr-xr-x    1    levi   class   1247 May 12 13:42 config
   $
   ```

## Linux文件权限和访问模式（Read、Write、Excute）

> 文件权限和访问模式

Linux中每个文件都拥有下面三种权限：

**所有者权限(Owner)**：所有者的权限决定了文件的所有者可以对文件执行什么操作。

**组权限(Group)**：组权限决定了文件所属组中的用户可以对文件执行什么操作。

**其他权限(Other)**:其他用户可以进行的操作。

文件访问模式

1）Read

授予读取(即查看文件内容)的能力。

2）Write

授予修改或删除文件内容的功能。

3）Execute

具有执行权限的用户可以将文件作为程序运行。

目录访问模式

1）Read

对目录的访问意味着用户可以读取目录的内容。用户可以查看目录中的文件名。

2）Write

访问意味着用户可以从目录中添加或删除文件。

3）Execute

执行目录实际上没有意义，因此可以将其视为遍历权限。

用户必须对bin目录执行访问才能执行ls或cd命令。

> 查看文件和目录权限

显示文件的各种信息

```
[yangzhenkun@localhost ~]$ ls -l
总用量 8
drwxr-xr-x. 4 yangzhenkun yangzhenkun 34 9月   4 21:41 Study
-rw-rw-r--. 1 yangzhenkun yangzhenkun 13 9月   5 11:19 temp_file
-rw-rw-r--. 1 yangzhenkun yangzhenkun 13 9月   5 11:45 text1
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 公共
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 模板
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 视频
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 图片
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 文档
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 下载
drwxr-xr-x. 2 yangzhenkun yangzhenkun  6 8月  28 10:50 音乐
drwxr-xr-x. 3 yangzhenkun yangzhenkun 15 8月  29 10:03 桌面


第一栏一共十个：其中第一个是文件类型；2-4：拥有者权限 5-7所属组权限 8-10：其他人权限
对于第一个字符: d:目录 -：文件 1：连接文件 b:设备文件 c：设备文件中串行端口设备，如键盘、鼠标
```

> 修改权限

修改文件或目录权限，使用`chmod` (change mode)命令。使用`chmod`有两种方式：符号模式和绝对模式。

对于初学者来说，修改文件或目录权限最简单的方法是使用符号模式。使用符号权限，可以使用下表中的操作符添加、删除或指定所需的权限。

| chmod操作符 | 描述                           |
| ----------- | ------------------------------ |
| +           | 向文件或目录添加指定的权限。   |
| -           | 从文件或目录中移除指定的权限。 |
| =           | 设置指定的权限。               |

注意：

在修改权限时，如果使用su -:就会进入系统目录下的root模式

​										  su：就会进入到当前目录下的root模式

> 使用chmod绝对模式修改权限

使用`chmod`命令修改权限的第二种方法是使用一个数字来指定文件的每一组权限。

每个权限都被分配一个值，如下表所示，每个权限集的总和为该集提供一个数字。



| 八进制权限表示                                   | 字符串 |
| ------------------------------------------------ | ------ |
| 无权限                                           | ---    |
| 运行权限                                         | --x    |
| 写权限                                           | -w-    |
| 执行和写入权限: 1 (execute) + 2 (write) = 3      | -wx    |
| 读权限                                           | r--    |
| 读和执行权限: 4 (read) + 1 (execute) = 5         | r-x    |
| 读写权限: 4 (read) + 2 (write) = 6               | rw-    |
| 所有权限: 4 (read) + 2 (write) + 1 (execute) = 7 | rwx    |

```
$ chmod 755 myfile
$ ls -l myfile
-rwxr-xr-x  1 levi   users 1024  Nov 9 11:12  myfile
$ chmod 743 myfile
$ ls -l myfile
-rwxr---wx  1 levi   users 1024  Nov 9 11:12  myfile
$ chmod 043 myfile
$ ls -l myfile
----r---wx  1 levi   users 1024  Nov 9 11:12  myfile
```

> 修改==文件==属性主和属组

**chown**：`chown`命令代表“change owner”，用于修改文件的所有者。

**chgrp**：c`hgrp`命令是“change group”的缩写，用于修改文件所属的组。

```
[yangzhenkun@localhost ~]$ chown yangzhenkun Study
```

2）修改所属组的权限(属组)

`chgrp`命令改变文件的组所有权。基本语法如下所示，

```
chgrp group filelist
```

group可以是系统中的组名，也可以是组的GID (group ID)。

```
chgrp admin myfile
```

将给定文件的组更改为admin组。

> SUID和SGID文件权限

SUID 是 Set User ID, SGID 是 Set Group ID的意思。

例如，使用`passwd`命令修改密码时，新密码保存在“`/etc/shadow`”文件中。

作为普通用户，出于安全考虑，没有对该文件的读写权限，但在修改密码时，需要对该文件具有写权限。这意味着`passwd`程序必须给额外的权限，以便您可以写入`/etc/shadow`文件。

1）SUID

任何用户执行设置有该权限的文件后，不再以用户自己的身份作为进程的属主，而是以该执行文件的属主作为进程的属主。这种权限的实质就是让执行该文件的用户，在进程运行过程中被授予文件属主的身份。

```
[root@localhost temp_file]# cd /etc
[root@localhost etc]# cd group
bash: cd: group: 不是目录
[root@localhost etc]# cat group
```

![image-20220908172648575](https://cdn.jsdelivr.net/gh/yzk656/image/202212242025127.png)

## Linux环境变量

Linux中环境变量包括系统级和用户级，系统级的环境变量是每个登录到系统的用户都要读取的系统变量，而用户级的环境变量则是该用户使用系统时加载的环境变量。所以管理环境变量的文件也分为系统级和用户级的.



> 系统级

## Linux基本实用程序（打印文件、email发送邮件）

打印文件和发送邮件作为 Linux 的基本实用程序。具体包括pr、lp、lpr、lpstat、lpq、lprm和mail等命令，本文主要介绍相关命令的使用，以及相关的示例。

> 打印文件

在Linux系统上打印文件之前，需要重新格式化它，以调整页边距，突出显示一些单词，等等。大多数文件也可以在不重新格式化的情况下打印，但原始打印输出可能不突出主题。

许多版本的Linux都包含两种功能强大的文本格式化程序，即`nroff`和`troff`。

> PR命令

r命令对终端屏幕或打印机上的文件进行少量格式化。例如，如果文件中有一长串名称，可以在屏幕上将其格式化为两列或更多列。

```
pr 选项 文件名
```

**注意**：`pr`只在屏幕上或打印副本上改变文件的格式;不会修改原始文件。、

```
  +首页[:末页], --pages=首页[:末页]
            在指定的首页/末页处开始/停止打印
  -列数, --columns=列数
            输出指定的列数。如果指定了-a 选项，则从上到下列印。
            程序会自动在每一页均衡每列占用的行数。
  -a, --across        设置每列从上到下输出，配合"-列数"选项一起使用
  -c, --show-control-chars
            使用头标(^G)和八进制反斜杠标记
  -d, --double-space    加倍输出空白区域(不是在所有pr版本都支持)
  -D, --date-format=格式
            使用遵循指定格式的页眉日期
  -e[字符[宽度]], --expand-tabs[=字符[宽度]]
            扩展输入的字符(制表符) 到制表符宽度(8)
  -F, -f, --form-feed    使用出纸页页标代替新行作为页面间的分隔符
            (使用-F 选项时报头为3 行,不使用时为5 行)
  -h, --header=页眉    在页眉中使用居中的指定字符代替文件名
            -h "" 输出一个空行，不要使用 -h""
  -i[字符[宽度]], --output-tabs[=字符[宽度]]
            使用指定字符(或制表符)代替空格不足到指定制表符宽度(默认8)
  -J, --join-lines    合并整个行，关闭-W 选项的行截断，不使用栏调整，使用
                --sep-string[=字符串] 设置分隔符
  -l, --length=页长
            使用指定页长的行数(默认66)
            (默认文本行数为56，当启用-F 时为 63)
  -m, --merge        在同一行显示所有文件，每个文件占用一栏，分割行，但是当
            使用-J 时将行合并到完整长度
  -n[分隔符[位数]], --number-lines[=分隔符[位数]]
            显示行号，使用指定(默认5) 位数，后接分隔符(默认TAB)
            默认从输入文件的第一行开始计数
  -N, --first-line-number=数字
            从首页的首行以指定数字开始计数(参看"+首页")
  -o, --indent=缩进量
            将每行缩进(默认0)个空格，不影响-w 或-W 参数，
            缩进亮的值将被加入页面宽度
  -r, --no-file-warnings
            当文件无法打开时忽略警告
  -s[CHAR], --separator[=CHAR]
            由单个字符分隔各列，未附加-w 时默认为制表符，否则为空。
            另外除非-w 选项被指定，否则"-s[CHAR]"会屏蔽三个列相关
            的截行选项(-COLUMN|-a -COLUMN|-m)
  -S字符串, --sep-string[=字符串]
            使用指定的字符串分栏，不使用-S 则使用默认的制表符
            TAB 作为分隔符，与-J 和空格一起使用(等于-S" ")对
            分栏选项无影响
  -t, --omit-header    忽略页眉和页脚
  -T, --omit-pagination
            按照输入文件中的设置忽略页眉和页脚并除去所有分页记号
  -v, --show-nonprinting
            使用八进制反斜杠标记
  -w, --width=页面宽度
            为多栏页面输出将设置为指定的字符数(默认72)，
            仅当-s[char] 选项不启用时有效(即保持默认值 72)。
  -W, --page-width=页宽
            总是将页宽设置为指定的(默认72)字符数，
            除非-J 选项启用总是截断行，此参数与-S 或-s 冲突
      --help        显示此帮助信息并退出
      --version        显示版本信息并退出
```

> Linux修改文件内容

在/opt/hello/world.txt文件中增加一行  hello linux world !

方法一：
命令是：vi，vim

vi 编辑器，相当于记事本，有编辑功能，但较弱
vim 复杂的编辑器，相当于windows的 editplus, notepad++ 等

------------------------

步骤：

1、执行 vi world.txt  进入编辑器（默认命令模式），

2、点击a或i进入编辑模式，敲入内容：hello linux world !
3、然后按键盘上的esc键退出编辑模式（进入到命令模式），

4、最后敲冒号：，

5、再敲wq保存并退出。

-------
wq解释为：write quite
不想保存，q
强制退出 q!

显示ip地址

```
hostname -I
```

## shell

![image-20221007233052701](https://cdn.jsdelivr.net/gh/yzk656/image/202212242025973.png)

![image-20221007234051089](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221007234051089.png)

![image-20221007234203370](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221007234203370.png)

echo 命令是Linux中最基本和最常用的命令之一。 传递参数给 echo 将打印到标准输出。 echo 通常在shell脚本中用于打印消息或输出其他命令的结果。 echo 是一个内置shell命令。

![image-20221007235930250](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221007235930250.png)

cat 命令是Linux中最常用的命令之一， cat 命令的名称来自于concatenate。 它可以读取和连接文件，并将其内容写入到标准输出。 如果未指定文件名或指定连字符 - 作为参数，则从标准输入读取内容，即复制标准输入到标准输出。 cat 最常用于打印/查看一个或多个文本文件的内容。

![image-20221008000129488](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008000129488.png)

![image-20221008000518098](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008000518098.png)

![image-20221008000525160](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008000525160.png)

`.`代表当前路径

```
./hello.sh
```

curl 是用于在本地计算机与远程服务器之间传输数据的命令行工具。 使用curl时您可以使用HTTP，HTTPS， SCP ， SFTP和FTP等协议下载或上传数据。 Curl提供了许多选项，使您可以恢复上传/下载，限制带宽，代理支持，用户身份验证等。 curl命令已预装在大多数Linux发行版中。

![image-20221008001710438](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008001710438.png)

![image-20221008070809045](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008070809045.png)

显示颜色

![image-20221008074147014](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008074147014.png)

![image-20221008074205811](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008074205811.png)

![image-20221008075433287](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008075433287.png)

bash -n查找语法错误，不能查找命令错误

变量设置颜色

![image-20221008080141496](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008080141496.png)

![image-20221008080201648](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008080201648.png) 

查找命令：man -bash

然后使用  /random进行查找

随机颜色：[]:代表算数运算

![image-20221008081055566](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008081055566.png)

![image-20221008081126906](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008081126906.png)

变量代替代码

![image-20221008081903903](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008081903903.png)

![image-20221008081918993](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008081918993.png)

```
 | bash
----------------------Host systeminfo--------------------
HOSTNAME:     localhost.localdomain
IPADDR:       192.168.157.131 192.168.122.1 
OSVERSION:    CentOS Linux 7 (Core)
KERNEL:       3.10.0-1160.76.1.el7.x86_64
CPU:         
MEMORY:       1.8G
DISK:         20G
---------------------------------------------------------

```

脚本运行

![image-20221008083135834](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008083135834.png)

### 输入输出重定向

重定向一般通过在命令间插入特定的符号来实现。特别的，这些符号的语法如下所示:

```
command1 > file1
```

上面这个命令执行command1然后将输出的内容存入file1。

注意任何file1内的已经存在的内容将被新内容替代。如果要将新内容添加在文件末尾，请使用>>操作符。

输出重定向会覆盖文件内容，请看下面的例子：

```
$ echo "菜鸟教程：www.runoob.com" > users
$ cat users
菜鸟教程：www.runoob.com
$
```

如果不希望文件内容被覆盖，可以使用 >> 追加到文件末尾，例如：

```
$ echo "菜鸟教程：www.runoob.com" >> users
$ cat users
菜鸟教程：www.runoob.com
菜鸟教程：www.runoob.com
$
```

*需要注意的是文件描述符 0 通常是标准输入（STDIN），1 是标准输出（STDOUT），2 是标准错误输出（STDERR）。*

查找bin下是否有bash

![image-20221008150855557](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008150855557.png)

![image-20221008151432765](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008151432765.png)

执行1：

![image-20221008151625510](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008151625510.png)

![image-20221008151704033](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008151704033.png)

第二种：

![image-20221008151831913](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008151831913.png)

![image-20221008152035529](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008152035529.png)

第三种

![image-20221008152337441](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008152337441.png)

![image-20221008152449483](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008152449483.png)

父-子shell

![](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008153823259.png)

![image-20221008170420347](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008170420347.png)

### 变量

![image-20221008153523151](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008153523151.png)

su与su -的区别

su为switch user，即切换用户的简写。

su是最简单的身份切换名，用su我们能够进行不论什么用户的切换，一般都是su – username，然后输入password就ok了，可是root用su切换到其它身份的时候是不须要输入password的。

如果不指定USERNAME（用户名），默认即为root，所以切换到root的身份的命令即为：su -root或su -，su root 或su。

**su –**

su -，su -l或su –login 命令改变身份时，也同时变更工作目录，以及HOME，SHELL，USER，LOGNAME。此外，也会变更PATH变量。用su -命令则默认转换成成root用户了。

而不带参数的“su命令”不会改变当前工作目录以及HOME,SHELL,USER,LOGNAME。只是拥有了root的权限而已。

**注意：**su -使用root的密码,而sudo su使用用户密码

![image-20221008155759132](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008155759132.png)

![image-20221008160543239](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008160543239.png)

父bash中定义的变量在子bash中找不到，因此可以用变量提升：export

![image-20221008160747196](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008160747196.png)

![image-20221008161120621](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008161120621.png)

也就是值传递，而不是引用传递

将变量其放进文件里【在一个新的子bash中使用my_var,用的是全局变量的值】

![image-20221008162050596](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162050596.png)

![image-20221008162036579](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162036579.png)

新设置变量

![image-20221008162519373](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162519373.png)

![image-20221008162458066](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162458066.png)

在子bash中是找不到new_var

![image-20221008162727379](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162727379.png)

在父bash中能够找到

![image-20221008162750314](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221008162750314.png)

提升变量后使用子bash也能看到

![image-20221008162858578](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026934.png)

数值运算

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026047.png)

常量

![image-20221008163420985](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026448.png)

撤销变量

![image-20221008163622904](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026871.png)

![image-20221008163702759](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026216.png)

执行命令都在/bin目录下面就可以调用文件时直接执行

![image-20221008164059097](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026351.png)

PATH下面的文件是可以直接运行的，因此将scripts的路径添加进PATH后，就可以直接运行hello.sh

![image-20221008164412924](https://cdn.jsdelivr.net/gh/yzk656/image/202212242026913.png)

![image-20221008164701442](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031233.png)

使用特殊变量

![image-20221008165052108](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031288.png)

![image-20221008165054772](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031773.png)

对于双引号里面的会判断$n是不是变量，如果使用单引号，就会当成字符串

![image-20221008165938760](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031373.png)

bashname：获取当前文件的名称

$#:计算参数个数

![image-20221008180520894](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031806.png)

![image-20221008180523268](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031406.png)

![image-20221008180550095](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031726.png)

![image-20221008180744971](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031222.png)

![image-20221008191623525](https://cdn.jsdelivr.net/gh/yzk656/image/202212242031534.png)

![image-20221008191604852](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032412.png)

![image-20221008191806086](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032225.png)

![image-20221008191828607](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032350.png)

表达式：expr

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032961.png)

简写

![image-20221008194209692](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032981.png)

麻烦点的

![image-20221008194445286](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032719.png)

括号可以直接+

![image-20221008194645703](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032239.png)

通过参数进行求和

![image-20221008195014522](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032631.png)

![image-20221008195027316](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032743.png)

不同的命令要有空格

因此对于等号旁边要有空格

![image-20221008195623490](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032976.png)

### 条件判断

![image-20221008195821112](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032544.png)

【】：也是一个命令。两个命令之间要有空格【空格：进行条件判断】

![image-20221008200033261](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032968.png)

![image-20221008200217561](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032384.png)

![image-20221008200354938](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032985.png)

![image-20221008200441646](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032447.png)

rm指令

  -f, --force  忽略不存在的文件，从不给出提示。

  -i, --interactive 进行交互式删除

  -r, -R, --recursive  指示rm将参数中列出的全部目录和子目录均递归地删除。

  -v, --verbose  详细显示进行的步骤

​    --help   显示此帮助信息并退出

​    --version 输出版本信息并退出

![image-20221008204404097](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032121.png)

![image-20221008204629434](https://cdn.jsdelivr.net/gh/yzk656/image/202212242032440.png)

![image-20221008205037780](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033904.png)

### 流程控制

![image-20221008211659408](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033369.png)

![image-20221008211826809](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033753.png)

![image-20221008212247249](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033638.png)

![image-20221008212301699](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033416.png)

通过if语句实现三元运算符

![image-20221008212704530](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033577.png)

简写：一个方括号

![image-20221008212845649](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033010.png)

双分支

![image-20221008213905951](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033146.png)

![image-20221008213923605](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008213923605.png)

![image-20221008214412248](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033441.png)

![image-20221008214434056](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033649.png)

![image-20221008214731325](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033514.png)

case

![image-20221008215345206](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033266.png)

![image-20221008215416600](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033371.png)

循环

![image-20221008215508204](https://cdn.jsdelivr.net/gh/yzk656/image/202212242033530.png)

![image-20221008221202367](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034684.png)

对于运算（（））可以不用空格

![image-20221009074411160](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034282.png)

![image-20221008221215914](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034616.png)

对于双小括号就可以直接使用运算符了“如>=”

![image-20221008222615192](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034562.png)

![image-20221008222848042](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008222848042.png)

对于花括号：{}：

{1..100}:1-100

![image-20221008223219211](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034194.png)

不加‘’

![image-20221008224300540](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034694.png)

![image-20221008224308196](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034963.png)

加上双引号

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034810.png)

![image-20221008224450774](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034154.png)



![image-20221008224650008](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034380.png)

![image-20221008233330751](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034146.png)

![image-20221008233347556](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008233347556.png)

通过let简写

![image-20221008233622094](https://cdn.jsdelivr.net/gh/yzk656/image/202212242034269.png)

![image-20221008233629093](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008233629093.png)

### read读取控制台输入

![image-20221008233707049](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035084.png)

![image-20221008235834448](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035299.png)

![image-20221008235846943](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221008235846943.png)

### 函数

![image-20221008235945554](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035620.png)

![image-20221009001647525](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035429.png)

![image-20221009001629440](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221009001629440.png)

 ![image-20221009075021716](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221009075021716.png)

修改parameter.sh文件

![image-20221009075216059](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035699.png)

![image-20221009075300344](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035994.png)

![image-20221009075400047](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035194.png)

![image-20221009075502813](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035786.png)

只是切割掉最后一个\之后的

![image-20221009081458636](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035248.png)

![image-20221009081501960](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035204.png)

![image-20221009082659472](https://cdn.jsdelivr.net/gh/yzk656/image/202212242035619.png)



![image-20221009083644090](https://cdn.jsdelivr.net/gh/yzk656/image/202212242036792.png)

![image-20221009083704230](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037535.png)

如果是想要返回值

![image-20221009084125248](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037729.png)

![image-20221009084139404](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221009084139404.png)

由于上面方法的输出值只能是0~255：解决办法

将函数用$提取出来

![image-20221009084513632](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037575.png)

![image-20221009084550865](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037919.png)

### 综合应用案例

![image-20221009084749636](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037078.png)

### Linux tar 命令

Linux tar（英文全拼：tape archive ）命令用于备份文件。

tar 是用来建立，还原备份文件的工具程序，它可以加入，解开备份文件内的文件。

![image-20221009095414113](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037455.png)

![image-20221009095546428](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037999.png)

定时任务

![image-20221009104705568](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037887.png)

![image-20221009104738208](https://cdn.jsdelivr.net/gh/yzk656/image/202212242037765.png)

查看定时任务是否生效

![image-20221009105004438](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038218.png)

### 正则表达式

![image-20221009105122849](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038576.png)

以a开头

![image-20221009105634194](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038328.png)

![image-20221009105700658](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038111.png)

以某个字符结尾

![image-20221009105805776](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038767.png)

匹配空行

![image-20221009110111410](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038096.png)

通过-n可以显示行号

`.`字符

![image-20221009110431873](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038792.png)

`.*`是不限制字符个数

![image-20221009110554202](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038496.png)

![image-20221009110604285](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038696.png)

如果不是`.`就是某个字符出现0~n次

![image-20221009110729062](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038095.png)

![image-20221009111051524](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038177.png)

![image-20221009111218456](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038241.png)

不加`，`也行

![image-20221009111343803](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038809.png)

![image-20221009111503737](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038031.png)

查找关键字

![image-20221009111643093](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038243.png)

对于`*`:出现0~n次

对于`+`:出现1-n次

对于`?`：出现0-1次

 花括号对于shell属于扩展部分，需要加上E

![image-20221009114144152](https://cdn.jsdelivr.net/gh/yzk656/image/202212242038288.png)

### 文本处理工具

![image-20221009114548783](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039593.png)

### Linux ：输入/输出重定向 >, 1>, 2>, &>, >> , <<

对于一个`>`是覆盖 

![image-20221009141915204](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221009141915204.png)

对于`>>`是拼接

![image-20221009142002223](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039318.png)

`2>`错误输出重定向

![image-20221009142417708](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039761.png)

标准错误输出到回收站

![image-20221009142550587](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039435.png)

`&>`正确、错误都会进行存放并且覆盖

![image-20221009142834020](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039258.png)

`>> file 2>&1`:追加进，正确或者错误输出

![image-20221009143138236](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039147.png)

`bc`是linux中的计算器

![image-20221009143527627](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039407.png)

`<`：输入重定向

![image-20221009143720098](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039436.png)

![image-20221009143742568](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039106.png)

两者结合

![image-20221009144104424](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039314.png)



## less指令

![image-20221009165811070](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039988.png)

`n` – 重复上一个搜索。`N` – 反向重复先前的搜索。`g` – 转到文件的第一行。`Ng` – 转到文件中的第N行。`G` – 转到文件的最后一行。`p` – 转到文件开头。

修改时间

date -s 时间









# School_Linux

文件前面有点的是隐藏文件

![image-20220829100859772](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039034.png)

文本模式切换：ctrl+alt+f1~f6

进入终端：ctrl+alt+f2~f6

退出终端：ctrl+alt+f1

注销linux终端用户：exit

文本模式下达指令

1. command   [-option]   parameter1   parameter2

   命令              选项           参数1               参数2

2. command：指令名称cd

3. 按enter执行命令

4. 注意：Linux中英文大小写不一样的，和Windows不同

5. ls：列出自己目录下的所有文件

6. ls -al：显示所有文件，包括隐藏文件

7. 显示支持的语言
   [yangzhenkun@localhost ~]$ locale
   LANG=zh_CN.UTF-8
   LC_CTYPE="zh_CN.UTF-8"
   LC_NUMERIC="zh_CN.UTF-8"
   LC_TIME="zh_CN.UTF-8"
   LC_COLLATE="zh_CN.UTF-8"
   LC_MONETARY="zh_CN.UTF-8"
   LC_MESSAGES="zh_CN.UTF-8"
   LC_PAPER="zh_CN.UTF-8"
   LC_NAME="zh_CN.UTF-8"
   LC_ADDRESS="zh_CN.UTF-8"
   LC_TELEPHONE="zh_CN.UTF-8"
   LC_MEASUREMENT="zh_CN.UTF-8"
   LC_IDENTIFICATION="zh_CN.UTF-8"
   LC_ALL=

   

   如果出现乱码，就修改语言为英文

   LANG=en_US.utf8

   export LC_ALL=en.utf8

   

8. 基础命令的操作

   1. 显示日期和时间：date

   2. [yangzhenkun@localhost ~]$ date +%Y%m%d
      20220829

   3. [yangzhenkun@localhost ~]$ date +%H:%M
      10:45

   4. [yangzhenkun@localhost ~]$ cal
            八月 2022     
      日 一 二 三 四 五 六
          1  2  3  4  5  6
       7  8  9 10 11 12 13
      14 15 16 17 18 19 20
      21 22 23 24 25 26 27
      28 29 30 31

   5. 显示整年的日历:cal 2022

   6. 显示某月的日历：

      [yangzhenkun@localhost ~]$ cal 10 2022

   7. 计算器命令：[yangzhenkun@localhost ~]$ bc
   
        退出计算器：quit 
        
        bc命令预设只输出整数(整数相除)，如果输出小数，使用scale=位数
        
   8. 重要的几个热键【tab、ctrl-c、ctrl-d】
   
        1. tab：具有命令补全与文件补齐的功能
        2. cal为例
             1. ca 【tab】 【tab】：引出ca引导的命令单词
             2. yangzhenkun@localhost ~]$ ca
                  cacertdir_rehash     cal                  capsh
                  cache_check          ca-legacy            captoinfo
                  cache_dump           calibrate_ppa        case
                  cache_metadata_size  caller               cat
                  cache_repair         canberra-boot        catchsegv
                  cache_restore        canberra-gtk-play    catman
                  cache_writeback      cancel               
                  cairo-sphinx         cancel.cups    
        3. tab在一串指令的第一个词后面，则为命令补全
        4. tab在一串指令的第二个词后面，则为文件补全
   
   9. ctrl-c：中断目前程序
   
   10. ctrl-d：退出文本终端
   
   11. shift+paggeup/pagedown：往前/后翻页
   
   12. 错误信息的查看
   
   13. Linux的在线求助：man page与infopage
   
         --help在线求助说明
   
         date --help
   
         关键字要与help之间有空格
   
   14. man page：man是manual操作说明的简写
   
         1. man date:查看使用说明
         2. /date:查找特定的关键字
         3. 可以直接输入q直接退出
         4. 常用快捷键
              1. 空格键：向下翻页
              2. pagup：向上翻页
              3. home：去到下一页
              4. end：去到最后一页
              5. /string:向下搜索string这个歌字符串
              6. ？string：向上搜索string这个字符串
              7. q退出
   
   15. 搜索特殊指令、文件mange
   
         [yangzhenkun@localhost ~]$ man -f man
         man (1)              - 格式化并显示在线帮助手册页
         man (7)              - 格式化手册页的宏
         man (1p)             - display system documentatio
   
          
   
         man 1 man：直接进行查看1
   
         还有另个与1manpage有关的指令：whatis ; man-f;apropos;man -k
   
         [yangzhenkun@localhost ~]$ whatis date
         date (1)             - 打印或设置系统日期和时间
         date (1p)            - write the date and time
         [yangzhenkun@localhost ~]$ man 1 date
   
   16. 命令使用顺序：dat tab tab->--help去查找基本用法->用man去查询指定用法
   
   17. infopage与manpage相似，他是以一个段落一个段落显示的，类似于超链接在 不同页面中进行跳转
   
         File：来自哪个文件
   
         Node：属于的top节点
   
         Next：下一个节点的名称：按n去到下一个节点
   
         up：回到上一个节点，按u回到上一层
   
   
   ==常用快捷键==[info page进入实验]
   
   空格键：向下翻页
   
   Page down：向下翻页
   
   tab：在node节点之间移动，有node的地方会以*显示
   
   enter：当光标在node上时，按enter可以进入node
   
   ![image-20220901141525947](https://cdn.jsdelivr.net/gh/yzk656/image/202212242039035.png)
   
   其他有用文件：位置/user/share/doc
   
   对man、info、、user、share、doc总结：
   
   在终端机模式中忘记某些参数，使用--help进行查询
   
   当你不知道有任何不知道的命令和文件时，使用man或info来查询
   
   如果你想知要假设一些其他的服务，或者利用一组软件来达成某项功能时，请使用/user/share/doc来查询该服务
   
   linux文件对于中文文件·很少，可以使用翻译软件践行解读
   
   18. 超简单文书编译器：nano
   
       1. nano text进入，上三角代表`ctrl`
       2. 组合键：
          1. ctrl-G：取得联机帮助
          2. X：离开nano软件
          3. O：存储文件
          4. R：读入文件
          5. W：写入文件
          6. C：输入目前所在行和列的信息
          7. _:输入行号
          8. Y：矫正语法功能的开启与关闭
          9. M：支持鼠标移动光标的功能
   
   19. ![image-20220901143855428](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040275.png)
   
       1. ![image-20220901143912663](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040563.png)
   
       2. [yangzhenkun@localhost ~]$ sync
          [yangzhenkun@localhost ~]$ shutdown
          Must be root.
   
       3. su -:切换成root用户
   
       4. ![image-20220901145054838](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040068.png)
   
          1. -c：取消关机指令
          
          2. [yangzhenkun@localhost ~]$ /sbin/shutdown -h 10 'i will shutdown after 10 min'
             Must be root.
             [yangzhenkun@localhost ~]$ su -
             密码：
             上一次登录：四 9月  1 14:41:57 CST 2022pts/0 上
             [root@localhost ~]# /sbin/shutdown -h 10 'i will shutdown after 1o minuate'
             Shutdown scheduled for 四 2022-09-01 14:58:51 CST, use 'shutdown -c' to cancel.
             [root@localhost ~]# 
             Broadcast message from root@localhost.localdomain (Thu 2022-09-01 14:48:51 CST):
          
             i will shutdown after 1o minuate
             The system is going down for power-off at Thu 2022-09-01 14:58:51 CST!
   
   
             Broadcast message from root@localhost.localdomain (Thu 2022-09-01 14:49:51 CST):
       
             i will shutdown after 1o minuate
             The system is going down for power-off at Thu 2022-09-01 14:58:51 CST!
       
             shut
             bash: shut: 未找到命令...
             [root@localhost ~]# shutdown -c
       
             Broadcast message from root@localhost.localdomain (Thu 2022-09-01 14:50:27 CST):
       
             The system shutdown has been cancelled at Thu 2022-09-01 14:51:27 CST!
   
   20. 重新启动，关机：reboot，halt，poweroff
   
       1. reboot：系统重启
       2. halt：系统停止，屏幕可能会保留系统已经停止的信息
       3. poweroff：系统关机
   21. 实际使用管理工具：systemctl
   
       1. init：有六个等级，0是关机；6是重新启动
       2. 管理员常用的关机指令：systemctl
       2. ![image-20220904152503177](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040683.png)
   
   ==回顾==
   
   ![image-20220904153629181](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040939.png)
   
   > Linux文件权限与目录配置
   
   linux文件可存取身份分为三个类别，分别是：ower、group、others，且三者身份个头reader、write、excute等权限
   
   1. 使用者和群组
   
      文件拥有者：只有你有权限看这个文件，其他人看不到
   
      群组概念：是最有用的功能之一，假设有两个专题组，一个是project_a,成员class_1、class_2、class_3；另一个project_b，成员class_4、class_4、class_6；两组缴纳同一份报告，每组组员之间修改相互的数据，但是其他组成员不能看到，teacher账号是两个专题的老师，teacher可以看两个专题的内容
   
   2. 
   
   ![image-20220904155743959](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040602.png)
   
   ![image-20220904155841869](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040787.png)
   
   ![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040308.png)
   
   3. linux文件权限的概念
   
      Linux文件的属性：
   
      ```
      [root@localhost ~]# ls -al
      总用量 36
      dr-xr-x---.  5 root root  225 9月   4 16:04 .
      dr-xr-xr-x. 17 root root  224 8月  28 10:59 ..
      -rw-------.  1 root root 1919 8月  28 10:48 anaconda-ks.cfg
      -rw-------.  1 root root   94 9月   1 14:53 .bash_history
      -rw-r--r--.  1 root root   18 12月 29 2013 .bash_logout
      -rw-r--r--.  1 root root  176 12月 29 2013 .bash_profile
      -rw-r--r--.  1 root root  176 12月 29 2013 .bashrc
      drwx------.  4 root root   31 9月   1 14:41 .cache
      drwxr-xr-x.  3 root root   18 9月   1 14:41 .config
      -rw-r--r--.  1 root root  100 12月 29 2013 .cshrc
      drwx------.  3 root root   25 8月  28 10:49 .dbus
      -rw-r--r--.  1 root root 1967 8月  28 10:49 initial-setup-ks.cfg
      -rw-r--r--.  1 root root  129 12月 29 2013 .tcshrc
      -rw-------.  1 root root  132 9月   4 16:04 .xauthT00aN9
      【权限】	  【连结】【拥有者】【群组】  【文件容量】【修改日期】【档名】
      ```
   
      su空格 -：切换成root用户
   
      **第一栏**：
      
      drwx------：共有十个字符
      
      ​	第一个字符代表这个文件是（目录、文件、链接等等）
      
      当为d时，则是目录
      
      当为-，则是文件
      
      当为l时，连接档
      
      当为b时，表示文件里面可供存储的接口设备
      
      当为c时，表示为装置文件里面的串行端口设备
      
      接下来的字符中，以三个为一组，均为rwx三个参数的组合，r:read，w：write，x：excute
      
      3）Execute
      
      具有执行权限的用户可以将文件作为程序运行。
      
      第一组为文件拥有者可具备的权限
      
      第二组为加入群组的账号的权限
      
      第三组非本人呢且没有加入本群组之其他账号的权限
      
      
      
      **第二栏**表示有多少档名连接此节点
      
      每个档名都会连接到一个i-node
      
      **第三栏**表示这个文件（或目录的拥有者账号）
      
      **第四栏**表示这个文件所属的群组
      
      **第五栏**这个文件的大小默认以bytes单位
      
      **第六栏**文件的建档日期或者是近日的修改的文件
      
      注意：如果要显示完整的时间格式，可以利用==ls==的选项：ls -1--full-time
      
      ```
      YLRA
      [root@localhost ~]# ls -1 --full-time
      总用量 8
      -rw-------. 1 root root 1919 2022-08-28 10:48:05.842156682 +0800 anaconda-ks.cfg
      -rw-r--r--. 1 root root 1967 2022-08-28 10:49:49.913010771 +0800 initial-setup-ks.cfg
      
      ```
      
      如果让系统语系变成英文的话，可以修改系统配置文件/etc/locale.confi
      
      **第七栏**文件的档名
      
      > Linux文件权限的重要性
      
      系统保护功能：
      
      团队开发软件和数据共享功能
      
      未将权限设定妥当的危害
      
      
      
      ## 第五课
      
      >  如何更改文件的属性和权限
      
      几个常用的群组、拥有者、各种身份的权限修改指令
      
      charp：改变文件属性
      
      chown：改变文件的拥有者
      
      chmod：改变文件的权限，suid；sgid；sbit等等属性
      
      **改变所属群组**：charp：charp group的缩写；同时也要记得，要被改变的组名必须要在ect/group 文件内才行，否则会显示错误
      
      参数选项：-R：进行递归的2持续变更，也是连同次目录下的所有文件、目录都更新成这个群组之一
      
      ```
      [root@localhost ~]# chgrp users initial-setup-ks.cfg
      [root@localhost ~]# ls -l
      总用量 8
      -rw-------. 1 root root  1919 8月  28 10:48 anaconda-ks.cfg
      -rw-r--r--. 1 root users 1967 8月  28 10:49 initial-setup-ks.cfg
      
      ```
      
      ```
      root@localhost ~]# chgrp testing initial-setup-ks.cfg
      chgrp: 无效的组："testing"   [发生错误信息，找不到这个组]
      ```
      
      **改变文件拥有者**：chown
      
      注意：用户必须已经存在系统中的账号，也就是/etc/passwd这个文件中有记录的用户名才能改变
      
      格式：chown【-R】 账号名称 文件目录
      
      ​			chown 【-R】账号名称：组名：文件或目录
      
      例子
      
      ```
      [root@localhost ~]# ls -l
      总用量 8
      -rw-------. 1 root root  1919 8月  28 10:48 anaconda-ks.cfg
      -rw-r--r--. 1 root users 1967 8月  28 10:49 initial-setup-ks.cfg
      [root@localhost ~]# chown bin initial-setup-ks.cfg
      [root@localhost ~]# ls -l
      总用量 8
      -rw-------. 1 root root  1919 8月  28 10:48 anaconda-ks.cfg
      -rw-r--r--. 1 bin  users 1967 8月  28 10:49 initial-setup-ks.cfg
      [root@localhost ~]# chown root:root initial-setup-ks.cfg
      [root@localhost ~]# ls -l
      总用量 8
      -rw-------. 1 root root 1919 8月  28 10:48 anaconda-ks.cfg
      -rw-r--r--. 1 root root 1967 8月  28 10:49 initial-setup-ks.cfg
      
      ```
      
      建议用    ==：==   将使用者和群组隔开
      
      修改群组
      
      ```
      root@localhost ~]# chown .sshd initial-setup-ks.cfg
      [root@localhost ~]# ls -l
      总用量 8
      -rw-------. 1 root root 1919 8月  28 10:48 anaconda-ks.cfg
      -rw-r--r--. 1 root sshd 1967 8月  28 10:49 initial-setup-ks.cfg
      ```
      
      
      
      通过cp指令来说明何时使用chown和chgrp指令
      
      将.bashrc这个文件拷贝为.bashrc.txt,档名且要给bin这个人。现使用cp指令说明
      
      格式：cp来源文件 目标文件
      
      首先将.bashrc这个文件拷贝成.bashrc_txt
      
        ```
        [root@localhost ~]# cp .bashrc .bashrc_test
        [root@localhost ~]# ls -al.bashrc*
        ls：无效选项 -- .
        Try 'ls --help' for more information.
        [root@localhost ~]# ls -al .bashrc*
        -rw-r--r--. 1 root root 176 12月 29 2013 .bashrc
        -rw-r--r--. 1 root root 176 9月   6 15:48 .bashrc_test
        ```
      
      
      
      改变权限：chmod
      
      权限修改有两种：一种是数字，另一种是符号进行权限变更
      
      数字类型改变文件权限：Linux基本权限有九个，分别是owner/group/others  三种身份各有自己的read/write/excute权限；文件的权限字符为：【-**rwx**rwx**rwx**】，这九个权限三个为一组。咱们可以使用数字代表各个权限：
      
      R：4
      
      W：2
      
      X：1
      
      
      
      每种身份（owenr、group、others），各个是哪个权限（r/w/x）分数是需要累加的
      
      规则：
      
      owner=rwx=4+2+1=7
      
      group=rwx=4+2+1=7
      
      others=---=0+0+0=0
      
      所以咱们设定权限的变更时，权限数字就是770，指令语法：chmod 【-R】 xyz 文件或目录
      
      选项与参数：
      
      xyz：就是刚刚咱们提到的数字类型的权限属性，为rwx属性数值的相加
      
      -R：进行递归的持续变更，以及链条所有文件都会变更
      
      
      
      将.bashrc这个文件的权限都设定为启用
      
      ```
      [root@localhost ~]# ls -al .bashrc
      -rw-r--r--. 1 root root 176 12月 29 2013 .bashrc
      [root@localhost ~]# chmod 777 .bashrc
      [root@localhost ~]# ls -al .bashrc
      -rwxrwxrwx. 1 root root 176 12月 29 2013 .bashrc
      [root@localhost ~]# 
      ```
      
      若将权限变成【-rwxr-xr--】：权限数值是4+2+1=7；4+0+1=5；4+0+0=4
      
      ```
      [root@localhost ~]# chmod 754 .bashrc
      [root@localhost ~]# ls -al .bashrc
      -rwxr-xr--. 1 root root 176 12月 29 2013 .bashrc
      [root@localhost ~]# 
      ```
      
      如果不想让其他人看到一些文件：【-rwxr-x---】，下达指令 7 5 0
      
       
      
      
      
      ## 第六课
      
      符号类型改变文件权限
      
      九个权限分别是1.user 2.group 3.others三种身份，咱们可以由u g o来代表三种身份权限，a代表all即全部身份，那么读写的权限就可以写成rwx可以写成下面方式
      
      ![image-20220908141632473](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040268.png)
      
      ![image-20220908141701208](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040788.png)
      
      ```
      [root@localhost yangzhenkun]# chmod u=rwx,go=rx .bashrc
      [root@localhost yangzhenkun]# ls -l .bashrc
      -rwxr-xr-x. 1 yangzhenkun yangzhenkun 231 4月   1 2020 .bashrc
      [root@localhost yangzhenkun]# 
      ```
      
      ```
      [root@localhost yangzhenkun]# chmod u=rwx,g=rx,o=r .bashrc
      [root@localhost yangzhenkun]# ls -l .bashrc
      -rwxr-xr--. 1 yangzhenkun yangzhenkun 231 4月   1 2020 .bashrc
      
      ```
      
      为每个人都添加写的权限
      
      ```
      [root@localhost yangzhenkun]# chmod a+w .bashrc
      [root@localhost yangzhenkun]# ls -l .bashrc
      -rwxrwxrw-. 1 yangzhenkun yangzhenkun 231 4月   1 2020 .bashrc
      
      ```
      
      ![image-20220908142921106](https://cdn.jsdelivr.net/gh/yzk656/image/202212242040452.png)
      
      > 目录与文件的权限之意
      
      1. 权限对文件的重要性
      
         文件的实质是含有数据的，包括一般文本文件，数据库内容文件，二进制可执行文件，因此权限对于文件来说：
      
         R：可以读取文件的实际内容，如1读取文件的文字内容
      
         W：可以编辑、新增、或者修改文件内容
      
         X：可以被系统执行的权限
      
      注意：rwx对文件只有读写执行权限，只是针对内容而言，没有删除权限，与文档名是否尊在没有关系
      
      > 权限对目录的重要性
      
      文件是存放实际数据的，目录主要记录文件名列表，文件名与列表有强烈关系
      
      ![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242042992.png)
      
      ![image-20220908144604608](https://cdn.jsdelivr.net/gh/yzk656/image/202212242042206.png)
      
      先用root身份建立所需要的文件和目录环境
      
      ![image-20220908162728527](https://cdn.jsdelivr.net/gh/yzk656/image/202212242042353.png)
      
      ![image-20220908150227608](https://cdn.jsdelivr.net/gh/yzk656/image/202212242042998.png)
      
      > mkdir和touch的区别
      
      **touch是新建文件，而mkdir是新建目录**。
      
      ```
      [root@localhost temp_file]# mkdir testing
      [root@localhost temp_file]# touch testing/testing
      [root@localhost temp_file]# chmod 600 testing/testing
      [root@localhost temp_file]# ls -ald testing/testing
      -rw-------. 1 root root 0 9月   8 16:33 testing/testing
      ```
      
      
      
      ## 第七课
      
      用户操作功能与权限
      
      /dir1/file1
      
      /dir2
      
      ![image-20220912100755877](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043657.png)
      
      ![image-20220912100951735](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043327.png)
      
      Linux文件类型：
      
      普通文件呢、目录文件、链接文件、设备文件、套接字、管道
      
       ![image-20220913164117626](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043136.png)
      
      ![image-20220913164132137](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043298.png)
      
      ![image-20220913164140257](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043179.png)
      
      ![image-20220913164146807](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043363.png)
      
      ![image-20220913164158729](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043729.png)
      
      ![image-20220913164204878](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043088.png)
      
      ![image-20220913164248391](https://cdn.jsdelivr.net/gh/yzk656/image/202212242043797.png)
      
      ![image-20220913164359589](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220913164359589.png)
      
      
      
      ![image-20220913164411103](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045412.png)
      
      ![image-20220913164428257](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045234.png)
      
      ![image-20220913164457344](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045763.png)
      
      ![image-20220913164527439](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045819.png)
      
      ![image-20220913164549412](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045148.png)
      
      ![image-20220913164631189](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045323.png)
      
      
      
      2. 针对==fhs==，各家都有不同，差异也是有限，主要包括这些：
         1. /bin->/user/bin
         2. /sbin->/user/sbin
         3. /lib->user/lib
         4. .lib64->user/lib64
         5. /var/lock->/run/lock
         6. var/run->/run





## 第八次课

目录树（directory tree）

​	目录树的特点：

​	目录的起始点为根目录（/root）

​	每一个目录不只能使用本地端的文件系统，也可以使用网络上的文件系统

​	每一根文件在次目录中的文件名是独一无二的

 

绝对路径与相对路径：

​	绝对路径：由根目录（/）开始写起的文件名或目录名称

​	相对路径：相对于目前路径的文件名写法

​	. :代表当前目录

​	..：代表上一层目录

centos的观察

​	LSB标准：lsb_release

重点回顾：

​	Linux的每一个文件中，可以分别给予使用者、群组、其他人三种身份个别的rwx权限。群组最有用的功能之一，当团队开发资源时，每个账号都可以支持多个群组

​	利用ls -l显示文件属性中，每一个字节是文件1的权限，第一个位置是文件类型，接下来三个为1组，为使用者、群组、其他人的权限，权限有rwx三种

​	![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045699.png)

   



> Linux文件与目录管理

![image-20220913184438805](https://cdn.jsdelivr.net/gh/yzk656/image/202212242045691.png)

## 第九次课

> 绝对路径

[root@localhost ~]# cd /home/yangzhenkun
[root@localhost yangzhenkun]# ls
Study  temp_file  text1  公共  模板  视频  图片  文档  下载  音

> 相对路径

[root@localhost yangzhenkun]# cd ..
[root@localhost home]# ls -l
总用量 4
drwx------. 19 yangzhenkun yangzhenkun 4096 9月  15 13:52 yang

回到自己的家目录

[root@localhost yangzhenkun]# cd ~
[root@localhost ~]# 



深度：/->home->yangzhenkun->Study.音乐



回到上一层目录

[root@localhost /]# cd -
/root

[root@localhost ~]# 



真实路径pwd -P【大写的P】

[root@localhost mail]# pwd -P
/var/spool/mail

[root@localhost mail]# pwd
/var/mail



建立1个新的目录：mkdir 【-mp】 目录名称

-m：配置文件的权限，直接设定，不需要看预设权限

-p：帮助你直接将所需的目录递归的建立起来



建立1个目录

[root@localhost tmp]# mkdir test



[root@localhost tmp]# mkdir test1/test2/test3/test4【尝试建立多个目录】
mkdir: 无法创建目录"test1/test2/test3/test4": 没有那个文件或目录【只能建立已有目录】

[root@localhost tmp]# mkdir -p test1/test2 test3/test4【使用-p可以建立多层目录】
[root@localhost tmp]# 



[root@localhost tmp]# mkdir -m 771 test2【配置权限时需要添加m指令】

==注意==：如果没有使用-m来强制他的属性，系统就会默认给一个属性



删除目录：rmdir

格式：mkdir [-p] 目录名称

-p：连同上一层一同删除

[root@localhost tmp]# rmdir -p test1/test2
[root@localhost tmp]# 



![](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220915144822518.png)



root身份

/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin
[root@localhost tmp]# exit
登出

普通身份

[yangzhenkun@localhost ~]$ echo $PATH
/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/home/yangzhenkun/.local/bin:/home/yangzhenkun/bin
[yangzhenkun@localhost ~]$ 



![image-20220915145726252](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046155.png)

![image-20220915150739502](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046908.png)

![image-20220915150802751](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220915150802751.png)

```
[root@localhost ~]# mv /bin/ls /root 【移动】

【下面试错】
[root@localhost ~]# mv root/ls /bin
mv: 无法获取"root/ls" 的文件状态(stat): 没有那个文件或目录
[root@localhost ~]# exit
登出
[yangzhenkun@localhost ~]$ su ~
su: user /home/yangzhenkun does not exist
[yangzhenkun@localhost ~]$ su -
密码：
上一次登录：四 9月 15 14:49:45 CST 2022pts/0 上
bash: ls: command not found...
Similar command is: 'lz'
[root@localhost ~]# mv root/ls /bin
mv: 无法获取"root/ls" 的文件状态(stat): 没有那个文件或目录
[root@localhost ~]# ls
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost ~]# bash l1
bash: l1: 没有那个文件或目录
[root@localhost ~]# bash ls
ls: ls: 无法执行二进制文件
[root@localhost ~]# bash.ls
bash: bash.ls: 未找到命令...
[root@localhost ~]# cd root
-bash: cd: root: 没有那个文件或目录
[root@localhost ~]# cd /root
[root@localhost ~]# ls -al
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost ~]# ls -l
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost ~]# cd ..
[root@localhost /]# cd bin
[root@localhost bin]# ls -al
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost bin]# ls -l
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost bin]# cd ..
[root@localhost /]# ls -bin
bash: ls: 未找到命令...
相似命令是： 'lz'
[root@localhost /]# exit
登出
[yangzhenkun@localhost ~]$ su -
密码：
上一次登录：四 9月 15 14:54:11 CST 2022pts/0 上
bash: ls: command not found...
Similar command is: 'lz'
[root@localhost ~]# ls -bin
bash: ls: 未找到命令...
相似命令是： 'lz'

【用绝对文件定制该文件】
[root@localhost ~]# /root/ls
anaconda-ks.cfg  initial-setup-ks.cfg  ls
[root@localhost ~]# /ls
-bash: /ls: 没有那个文件或目录
[root@localhost ~]# ./ls
anaconda-ks.cfg  initial-setup-ks.cfg  ls
[root@localhost ~]# PATH="$(PATH):/root"

【加入PATH变量】
bash: PATH: 未找到命令...
[root@localhost ~]# PATH="${PATH}:/root"
[root@localhost ~]# ls
anaconda-ks.cfg  initial-setup-ks.cfg  ls

【撤销移动失败】
[root@localhost ~]# mv /root/ls /bin
bash: mv: 未找到命令...
[root@localhost ~]# exit
登出
[yangzhenkun@localhost ~]$ su -
密码：
上一次登录：四 9月 15 15:01:34 CST 2022pts/0 上
bash: ls: command not found...
Similar command is: 'lz'
[root@localhost ~]# ls
bash: ls: 未找到命令...
相似命令是： 'lz'

【上网搜的】
[root@localhost ~]# export PATH=/bin:/usr/bin:$PATH
[root@localhost ~]# ls
bash: ls: 未找到命令...
相似命令是： 'lz'


【撤销移动成功】
[root@localhost ~]# mv /root/ls /bin
[root@localhost ~]# ls
anaconda-ks.cfg  initial-setup-ks.cfg
[root@localhost ~]# su -
上一次登录：四 9月 15 15:10:58 CST 2022pts/0 上
[root@localhost ~]# exit
登出
[root@localhost ~]# exit
登出
[yangzhenkun@localhost ~]$ su -
密码：
上一次登录：四 9月 15 15:14:47 CST 2022pts/0 上
[root@localhost ~]# ls
anaconda-ks.cfg  initial-setup-ks.cfg
[root@localhost ~]#
```





## 第十次课

> 文件与目录的管理

​	文件与目录的检视

​		ls：格式：ls  【】 文件名或目录名称

​		ls 【--full-time】文件名或目录名称

​	具体选项及参数

​	-a：全部文件，连同隐藏档

​	-A：全部文件，连同隐藏档。但不包括.与..这两目录

​	-d：仅列出目录本身，而不是列出目录内的文件数据

​	-f：仅列出结果，而不进行排序

​	![image-20220919101547557](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220919101547557.png)

​	-full-time:已完整实践模式输出

​	列出文件目录

```
[root@localhost ~]# ls -al
总用量 44
dr-xr-x---.  5 root root  261 9月  19 10:20 .
dr-xr-xr-x. 18 root root  241 9月   5 13:03 ..
-rw-------.  1 root root 1919 8月  28 10:48 anaconda-ks.cfg
-rw-------.  1 root root 3826 9月  15 15:20 .bash_history
-rw-r--r--.  1 root root   18 12月 29 2013 .bash_logout
-rw-r--r--.  1 root root  176 12月 29 2013 .bash_profile
-rwxr-xr--.  1 root root  176 12月 29 2013 .bashrc
-rw-r--r--.  1 root root  176 9月   6 15:48 .bashrc_test
drwx------.  4 root root   31 9月   1 14:41 .cache
drwxr-xr-x.  3 root root   18 9月   1 14:41 .config
-rw-r--r--.  1 root root  100 12月 29 2013 .cshrc
drwx------.  3 root root   25 8月  28 10:49 .dbus
-rw-r--r--.  1 root sshd 1967 8月  28 10:49 initial-setup-ks.cfg
-rw-r--r--.  1 root root  129 12月 29 2013 .tcshrc
-rw-------.  1 root root  804 9月   8 17:54 .viminfo
-rw-------.  1 root root  132 9月  19 10:20 .xauthqi4DLe

```

完整呈现文件的修改时间

```
[root@localhost ~]# ls -al --full-time
总用量 44
dr-xr-x---.  5 root root  261 2022-09-19 10:20:51.668450746 +0800 .
dr-xr-xr-x. 18 root root  241 2022-09-05 13:03:48.834372693 +0800 ..
-rw-------.  1 root root 1919 2022-08-28 10:48:05.842156682 +0800 anaconda-ks.cfg
-rw-------.  1 root root 3826 2022-09-15 15:20:24.480690032 +0800 .bash_history
-rw-r--r--.  1 root root   18 2013-12-29 10:26:31.000000000 +0800 .bash_logout
-rw-r--r--.  1 root root  176 2013-12-29 10:26:31.000000000 +0800 .bash_profile
-rwxr-xr--.  1 root root  176 2013-12-29 10:26:31.000000000 +0800 .bashrc
-rw-r--r--.  1 root root  176 2022-09-06 15:48:19.218089459 +0800 .bashrc_test
drwx------.  4 root root   31 2022-09-01 14:41:57.517196674 +0800 .cache
drwxr-xr-x.  3 root root   18 2022-09-01 14:41:57.531196675 +0800 .config
-rw-r--r--.  1 root root  100 2013-12-29 10:26:31.000000000 +0800 .cshrc
drwx------.  3 root root   25 2022-08-28 10:49:21.714009224 +0800 .dbus
-rw-r--r--.  1 root sshd 1967 2022-08-28 10:49:49.913010771 +0800 initial-setup-ks.cfg
-rw-r--r--.  1 root root  129 2013-12-29 10:26:31.000000000 +0800 .tcshrc
-rw-------.  1 root root  804 2022-09-08 17:54:39.683781675 +0800 .viminfo
-rw-------.  1 root root  132 2022-09-19 10:20:51.668450746 +0800 .xauthqi4DLe

```

![image-20220919102754973](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046675.png)

复制删除移动的命令：cp、rm、mv

cp ：除了单纯的复制文件以外，还有建立连接档、比对两个文件新旧进行更新、复制整个目录等等

mv：移动文件目录，他可以直接拿来进行更名

rm：移除

cp：

格式：cp 【-adfiprsu】来源文件 目标文件

![image-20220919104147095](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046716.png)

```
[root@localhost ~]# cp ~/.bashrc /tmp/bashrc
[root@localhost ~]# cp -i ~/.bashrc /tmp/bashrc
cp：是否覆盖"/tmp/bashrc"？ y
```

## 第十一课

-s：复制成为符号的连接文件

[root@localhost ~]# cp -s /tmp/bashrc bashrc_slink
[root@localhost ~]# ls -l bashrc_slink
lrwxrwxrwx. 1 root root 11 9月  20 15:30 bashrc_slink -> /tmp/bashrc
[root@localhost ~]# 

```
[yangzhenkun@localhost guestuser1]$ cp -s work2/temp_file2 work1/temp_file2_link
cp: "work1/temp_file2_link"：只能于当前目录中创建相对的符号链接
```



-l：进行硬是连接连接档，而非复制文件本身

[root@localhost ~]# cp -l /tmp/bashrc bashrc_hsink

[root@localhost ~]# ls -l bashrc_hsink
-rwxr-xr--. 2 root root 176 9月  19 10:43 bashrc_hsink

![image-20220920154102587](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046132.png)

[root@localhost ~]# cp -u ~/.bashrc /tmp/bashrc
[root@localhost ~]# ls -al /tmp/bashrc
-rwxr-xr--. 2 root root 176 9月  19 10:43 /tmp/bashrc

-d是复制源文件

[root@localhost ~]# cp bashrc_slink bashrc_slink_1
[root@localhost ~]# cp -d bashrc_slink bashrc_slink_2

[root@localhost ~]# ls -l bashrc_slink*
lrwxrwxrwx. 1 root root  11 9月  20 15:30 bashrc_slink -> /tmp/bashrc
-rwxr-xr--. 1 root root 176 9月  20 15:44 bashrc_slink_1
lrwxrwxrwx. 1 root root  11 9月  20 15:45 bashrc_slink_2 -> /tmp/bashrc



注意复制的属性和权限特性

是否需要完整的保留来源文件的信息

来源文件是否为连接档

来源文件是否为特殊文件

来源文件是否为目录

普通用户不能那个随意修改文件的拥有者和群组



rm移除文件或目录

rm [-fir] 文件或目录

-f：就是忽略不存在的文件，不会出现警告信息

-i：互动模式，在删除前会询问使用者是否动作

-r：递归删除！常用在目录的删除，这个动作很危险

[root@localhost ~]# cd .tmnp
-bash: cd: .tmnp: 没有那个文件或目录
[root@localhost ~]# cd /tmp
[root@localhost tmp]# rm -i bashrc
rm：是否删除普通文件 "bashrc"？y

通配符*

rm: 无法删除"bashrc*": 没有那个文件或目录
[root@localhost tmp]# ls -l bashrc

![image-20220920160259108](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046332.png)

[root@localhost tmp]# rm ./-aaa-
rm：是否删除普通空文件 "./-aaa-"？y

## 第十二课

mv

![image-20220920161021829](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046228.png)

更新名称

[root@localhost tmp]# mv mvtest mvtest2
[root@localhost tmp]# ls-l

![image-20220922141849711](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046227.png)

多个文件移动

```
[root@localhost tmp]# cp ~/.bashrc bashrc1
[root@localhost tmp]# cp ~/.bashrc bashrc2
[root@localhost tmp]# mv bashrc1 bashrc2 mvtest2
[root@localhost tmp]# ls -al mvtest2
总用量 12
drwxr-xr-x.  2 root root   36 9月  22 14:20 .
drwxrwxrwt. 26 root root 4096 9月  22 14:20 ..
-rwxr-xr--.  1 root root  176 9月  22 14:20 bashrc1
-rwxr-xr--.  1 root root  176 9月  22 14:20 bashrc2


cp也可以直接作为创建文件
```

![image-20220922142210287](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046091.png)

![image-20220922142324630](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220922142324630.png)

![image-20220922142643784](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046421.png)

![image-20220922142931404](https://cdn.jsdelivr.net/gh/yzk656/image/202212242046581.png)

![image-20220922143116240](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220922143116240.png)

![image-20220922143548680](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047701.png)

![image-20220922143727068](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220922143727068.png)

```
[root@localhost ~]# cat /etc/issue
\S
Kernel \r on an \m

```

```
[root@localhost ~]# cat -n /etc/issue
     1	\S
     2	Kernel \r on an \m
     3	

```

断行字符$

```
[root@localhost ~]# cat -A /etc/man_db.conf
# $
#$
# This file is used by the man-db package to configure the man and cat paths.$
# It is also used to provide a manpath for those without one by examining$
# their PATH environment variable. For details see the manpath(5) man page.$
#$
# Lines beginning with `#' are comments and are ignored. Any combination of$
# tabs or spaces may be used as `whitespace' separators.$
#$
# There are three mappings allowed in this file:$
# --------------------------------------------------------$
# MANDATORY_MANPATH^I^I^Imanpath_element$
# MANPATH_MAP^I^Ipath_element^Imanpath_element$
# MANDB_MAP^I^Iglobal_manpath^I[relative_catpath]$
#---------------------------------------------------------$
# every automatically generated MANPATH includes these fields$
#$
#MANDATORY_MANPATH ^I^I^I/usr/src/pvm3/man$
#$
MANDATORY_MANPATH^I^I^I/usr/man$
MANDATORY_MANPATH^I^I^I/usr/share/man$
MANDATORY_MANPATH^I^I^I/usr/local/share/man$
#---------------------------------------------------------$
# set up PATH to MANPATH mapping$
# ie. what man tree holds man pages for what binary directory.$
#$
#^I^I*PATH*        ->^I*MANPATH*$
#$
MANPATH_MAP^I/bin^I^I^I/usr/share/man$
MANPATH_MAP^I/usr/bin^I^I/usr/share/man$
MANPATH_MAP^I/sbin^I^I^I/usr/share/man$
MANPATH_MAP^I/usr/sbin^I^I/usr/share/man$
MANPATH_MAP^I/usr/local/bin^I^I/usr/local/man$
MANPATH_MAP^I/usr/local/bin^I^I/usr/local/share/man$
MANPATH_MAP^I/usr/local/sbin^I^I/usr/local/man$
MANPATH_MAP^I/usr/local/sbin^I^I/usr/local/share/man$
MANPATH_MAP^I/usr/X11R6/bin^I^I/usr/X11R6/man$
MANPATH_MAP^I/usr/bin/X11^I^I/usr/X11R6/man$
MANPATH_MAP^I/usr/games^I^I/usr/share/man$
MANPATH_MAP^I/opt/bin^I^I/opt/man$
MANPATH_MAP^I/opt/sbin^I^I/opt/man$
#---------------------------------------------------------$
# For a manpath element to be treated as a system manpath (as most of those$
# above should normally be), it must be mentioned below. Each line may have$
# an optional extra string indicating the catpath associated with the$
# manpath. If no catpath string is used, the catpath will default to the$
# given manpath.$
#$

```

![image-20220922144738288](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220922144738288.png)

```
[root@localhost ~]# tac /etc/issue

Kernel \r on an \m
\S

```

![image-20220922144850782](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047943.png)

![image-20220922145432509](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047117.png)

```
[root@localhost ~]# nl /etc/issue
     1	\S
     2	Kernel \r on an \m



[root@localhost ~]# nl -b a /etc/issue
     1	\S
     2	Kernel \r on an \m
     3	


[root@localhost ~]# nl -b a -n rz /etc/issue
000001	\S
000002	Kernel \r on an \m
000003	
[root@localhost ~]# nl -b a -n rz -w 3 /etc/issue
001	\S
002	Kernel \r on an \m
003	

```

## 第18课

![image-20220926101159728](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047637.png)

![image-20220926101506794](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047525.png)

![image-20220926102429237](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047895.png)

![image-20220926102458883](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047454.png)

![image-20220926103502747](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047661.png)



```
默认显示10行


[root@localhost ~]# head /etc/man_db.conf
# 
#
# This file is used by the man-db package to configure the man and cat paths.
# It is also used to provide a manpath for those without one by examining
# their PATH environment variable. For details see the manpath(5) man page.
#
# Lines beginning with `#' are comments and are ignored. Any combination of
# tabs or spaces may be used as `whitespace' separators.
#
# There are three mappings allowed in this file:




打印指定行数
# 
#
# This file is used by the man-db package to configure the man and cat paths.
# It is also used to provide a manpath for those without one by examining
# their PATH environment variable. For details see the manpath(5) man page.
#
# Lines beginning with `#' are comments and are ignored. Any combination of
# tabs or spaces may be used as `whitespace' separators.
#
# There are three mappings allowed in this file:
# --------------------------------------------------------
# MANDATORY_MANPATH			manpath_element
# MANPATH_MAP		path_element	manpath_element
# MANDB_MAP		global_manpath	[relative_catpath]
#---------------------------------------------------------
# every automatically generated MANPATH includes these fields
#
#MANDATORY_MANPATH 			/usr/src/pvm3/man
#
MANDATORY_MANPATH			/usr/man


如果后面100行都不要，只打印前面几行
[root@localhost ~]# head -n -100 /etc/man_db.conf
# 
#
# This file is used by the man-db package to configure the man and cat paths.
# It is also used to provide a manpath for those without one by examining
# their PATH environment variable. For details see the manpath(5) man page.
#
# Lines beginning with `#' are comments and are ignored. Any combination of
# tabs or spaces may be used as `whitespace' separators.
#
# There are three mappings allowed in this file:
# --------------------------------------------------------
# MANDATORY_MANPATH			manpath_element
# MANPATH_MAP		path_element	manpath_element
# MANDB_MAP		global_manpath	[relative_catpath]
#---------------------------------------------------------
# every automatically generated MANPATH includes these fields
#
#MANDATORY_MANPATH 			/usr/src/pvm3/man
#
MANDATORY_MANPATH			/usr/man
MANDATORY_MANPATH			/usr/share/man
MANDATORY_MANPATH			/usr/local/share/man
#---------------------------------------------------------
# set up PATH to MANPATH mapping
# ie. what man tree holds man pages for what binary directory.
#
#		*PATH*        ->	*MANPATH*
#
MANPATH_MAP	/bin			/usr/share/man
MANPATH_MAP	/usr/bin		/usr/share/man
MANPATH_MAP	/sbin			/usr/share/man


```



```
默认显示末位10行
[root@localhost ~]# tail /etc/man_db.conf
# formatted for a terminal of the given width, regardless of the width of
# the terminal actually being used. This should generally be within the
# range set by MINCATWIDTH and MAXCATWIDTH.
#
#CATWIDTH	0
#
#---------------------------------------------------------
# Flags.
# NOCACHE keeps man from creating cat pages.
#NOCACHE


指定行数
[root@localhost ~]# tail -n 20 /etc/man_db.conf
#
#---------------------------------------------------------
# Range of terminal widths permitted when displaying cat pages. If the
# terminal falls outside this range, cat pages will not be created (if
# missing) or displayed.
#
#MINCATWIDTH	80
#MAXCATWIDTH	80
#
# If CATWIDTH is set to a non-zero number, cat pages will always be
# formatted for a terminal of the given width, regardless of the width of
# the terminal actually being used. This should generally be within the
# range set by MINCATWIDTH and MAXCATWIDTH.
#
#CATWIDTH	0
#
#---------------------------------------------------------
# Flags.
# NOCACHE keeps man from creating cat pages.
#NOCACHE



前100行数据
[root@localhost ~]# tail -n +100 /etc/man_db.conf
#---------------------------------------------------------
# Section names. Manual sections will be searched in the order listed here;
# the default is 1, n, l, 8, 3, 0, 2, 5, 4, 9, 6, 7. Multiple SECTION
# directives may be given for clarity, and will be concatenated together in
# the expected way.
# If a particular extension is not in this list (say, 1mh), it will be
# displayed with the rest of the section it belongs to. The effect of this
# is that you only need to explicitly list extensions if you want to force a
# particular order. Sections with extensions should usually be adjacent to
# their main section (e.g. "1 1mh 8 ...").
#
SECTION		1 1p 8 2 3 3p 4 5 6 7 9 0p n l p o 1x 2x 3x 4x 5x 6x 7x 8x
#
#---------------------------------------------------------
# Range of terminal widths permitted when displaying cat pages. If the
# terminal falls outside this range, cat pages will not be created (if
# missing) or displayed.
#
#MINCATWIDTH	80
#MAXCATWIDTH	80
#
# If CATWIDTH is set to a non-zero number, cat pages will always be
# formatted for a terminal of the given width, regardless of the width of
# the terminal actually being used. This should generally be within the
# range set by MINCATWIDTH and MAXCATWIDTH.
#
#CATWIDTH	0
#
#---------------------------------------------------------
# Flags.
# NOCACHE keeps man from creating cat pages.
#NOCACHE




持续侦测messages内容：ctrl+c退出
[root@localhost ~]# tail -f /var/log/messages
Sep 26 11:44:46 localhost systemd: Starting Network Manager Script Dispatcher Service...
Sep 26 11:44:46 localhost dhclient[4067]: bound to 192.168.157.128 -- renewal in 883 seconds.
Sep 26 11:44:46 localhost dbus[694]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 26 11:44:46 localhost systemd: Started Network Manager Script Dispatcher Service.
Sep 26 11:44:46 localhost nm-dispatcher: req:1 'dhcp4-change' [ens33]: new request (4 scripts)
Sep 26 11:44:46 localhost nm-dispatcher: req:1 'dhcp4-change' [ens33]: start running ordered scripts...
Sep 26 11:47:36 localhost kernel: perf: interrupt took too long (33480 > 33267), lowering kernel.perf_event_max_sample_rate to 5000
Sep 26 11:50:01 localhost systemd: Created slice User Slice of root.
Sep 26 11:50:01 localhost systemd: Started Session 12 of user root.
Sep 26 11:50:01 localhost systemd: Removed slice User Slice of root.
^C

```



```
使用ascll码显示
[root@localhost ~]# od -t c /usr/bin/passwd



以八进制显示
[root@localhost ~]# od -t oCc /etc/issue
0000000 134 123 012 113 145 162 156 145 154 040 134 162 040 157 156 040
          \   S  \n   K   e   r   n   e   l       \   r       o   n    
0000020 141 156 040 134 155 012 012
          a   n       \   m  \n  \n

```



![image-20220926121314096](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047446.png)

```
多条指令用分号隔开
[root@localhost ~]# date;ls -l /etc/man_db.conf;ls -l --time=atime /etc/man_db.conf; \ls -l --time=ctime /etc/man_db.conf
2022年 09月 26日 星期一 12:17:48 CST
-rw-r--r--. 1 root root 5171 10月 31 2018 /etc/man_db.conf        mtime
-rw-r--r--. 1 root root 5171 9月  25 21:41 /etc/man_db.conf		 atime
-rw-r--r--. 1 root root 5171 8月  28 10:40 /etc/man_db.conf		 ctime

```





## 第19课

![image-20220927153451038](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047952.png)

```
创建文件
[yangzhenkun@localhost tmp]$ touch testtouch
[yangzhenkun@localhost tmp]$ ls -l testtouch
-rw-rw-r--. 1 yangzhenkun yangzhenkun 0 9月  27 15:33 testtouch


注意：ll指令代表（ll=ls -l）
[root@localhost ~]# date;ll bashrc;ll --time=atime bashrc;ll --time=ctime bashrc
2022年 09月 27日 星期二 15:40:12 CST
-rwxr-xr--. 1 root root 176 12月 29 2013 bashrc   mtime
-rwxr-xr--. 1 root root 176 9月  27 15:36 bashrc  atime
-rwxr-xr--. 1 root root 176 9月  27 15:37 bashrc  ctime


//修改时间从新测评
[root@localhost ~]# touch -d 2 days ago bashrc
[root@localhost ~]# date;ll bashrc;ll --time=atime bashrc;ll --time=ctime bashrc
2022年 09月 27日 星期二 15:45:37 CST
-rwxr-xr--. 1 root root 176 9月  27 02:00 bashrc
-rwxr-xr--. 1 root root 176 9月  27 02:00 bashrc
-rwxr-xr--. 1 root root 176 9月  27 15:45 bashrc

修改时间
[yangzhenkun@localhost work2]$ touch -d '20000112' temp_file


```

![image-20220927153848388](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047920.png)

![image-20220929140327416](https://cdn.jsdelivr.net/gh/yzk656/image/202212242047751.png)

| 简名  | 全名        | 中文     | 作用                                                       |
| :---- | :---------- | :------- | :--------------------------------------------------------- |
| atime | Access Time | 访问时间 | 最后一次访问文件（读取或执行）的时间                       |
| ctime | Change Time | 变化时间 | 最后一次改变文件（属性或权限）或者目录（属性或权限）的时间 |
| mtime | Modify Time | 修改时间 | 最后一次修改文件（内容）或者目录（内容）的时间             |



![image-20220927154513896](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048085.png)



![image-20220927154811168](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048456.png)

![image-20220927154933161](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048599.png)

![image-20220927155313553](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048678.png)

![image-20220927160118824](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048054.png)

![![image-20220927160531350](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048774.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048394.png)

```
[root@localhost ~]# umask
0022
[root@localhost ~]# touch test1
[root@localhost ~]# mkdir test2
[root@localhost ~]# ll -d test*
-rw-r--r--. 1 root root 0 9月  27 16:07 test1
drwxr-xr-x. 2 root root 6 9月  27 16:07 test2

```

![image-20220927160937729](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048985.png)



## 第20课

![image-20220929141104484](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048064.png)

```
[root@localhost ~]# umask 002
[root@localhost ~]# touch test3
[root@localhost ~]# mkdir test4
[root@localhost ~]# ll -d test[34]
-rw-rw-r--. 1 root root 0 9月  29 14:09 test3
drwxrwxr-x. 2 root root 6 9月  29 14:09 test4
```

![image-20220929141621702](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048679.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048020.png)

![image-20220929143233970](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048704.png)

```
+i属性

[root@localhost ~]# touch attrtest
[root@localhost ~]# chattr +i attrtest
[root@localhost ~]# rm attrtest
rm：是否删除普通空文件 "attrtest"？y
rm: 无法删除"attrtest": 不允许的操作
[root@localhost ~]# chattr -i attrtest
[root@localhost ~]# rm attrtest
rm：是否删除普通空文件 "attrtest"？y
[root@localhost ~]# 



[root@localhost ~]# touch attrtest
[root@localhost ~]# chattr +ais attrtest
chattr: 不支持的操作 while setting flags on attrtest
[root@localhost ~]# chattr +aiS attrtest
[root@localhost ~]# lsattr attrtest
--S-ia---------- attrtest



```



![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048304.png)

![image-20220929145038397](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048983.png)

![image-20221003110655861](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048481.png)

![image-20221003110943527](https://cdn.jsdelivr.net/gh/yzk656/image/202212242048175.png)

![image-20221003111223476](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049488.png)

```
[root@localhost ~]# cd /tmp
[root@localhost tmp]# touch test
[root@localhost tmp]# chmod 4755 test
[root@localhost tmp]#  ll test
-rwsr-xr-x. 1 root root 0 10月  3 11:13 test


7:s s t都有
[root@localhost tmp]# chmod 7666 test;ll test
-rwSrwSrwT. 1 root root 0 10月  3 11:13 test


[root@localhost tmp]# chmod u=rwxs,go=x test;ll test
-rws--x--x. 1 root root 0 10月  3 11:13 test
 
```

![image-20221003112751105](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221003112751105.png)

![image-20221003115413788](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049002.png)

```
[root@localhost tmp]# file ~/.bashrc
/root/.bashrc: ASCII text

[root@localhost tmp]# file /usr/bin/passwd
/usr/bin/passwd: setuid ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.32, BuildID[sha1]=dee1b9ab6618c6bfb84a14f85ba258c742cf4aec, stripped

```

![image-20221003115718636](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049735.png)

![image-20221003115943655](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049328.png)

![image-20221003120053914](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221003120053914.png)

```
[root@localhost tmp]# which ifconfig
/sbin/ifconfig

```

![image-20221003120136321](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049760.png)

![image-20221003120230021](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049560.png)



文档名的搜寻

![image-20221003120413145](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049033.png)



![image-20221003104324821](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049960.png)

![image-20221003104631901](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049288.png)

![image-20221003104751733](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049810.png)

![image-20221003104952724](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049329.png)

![image-20221004152915897](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049473.png)

```
[root@localhost tmp]# locate -l 5 passwd
/etc/passwd
/etc/passwd-
/etc/pam.d/passwd
/etc/security/opasswd
/usr/bin/gpasswd
[root@localhost tmp]# 



[root@localhost tmp]# locate -S
数据库 /var/lib/mlocate/mlocate.db:
	19,841 文件夹
	197,424 文件
	10,624,934 文件名中的字节数
	4,751,164 字节用于存储数据库
[root@localhost tmp]# 


```

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049963.png)

![image-20221004153810726](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049314.png)

![image-20221004154114123](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049514.png)

![image-20221004154554335](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049408.png)

![image-20221004154800035](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049776.png)

![image-20221004155319229](https://cdn.jsdelivr.net/gh/yzk656/image/202212242049489.png)

![image-20221004155440305](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221004155440305.png)

![image-20221004155555367](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221004155555367.png)

```
[root@localhost ~]# find / -nouser
find: ‘/proc/4181’: 没有那个文件或目录
find: ‘/proc/4233/task/4233/fd/5’: 没有那个文件或目录
find: ‘/proc/4233/task/4233/fdinfo/5’: 没有那个文件或目录
find: ‘/proc/4233/fd/6’: 没有那个文件或目录
find: ‘/proc/4233/fdinfo/6’: 没有那个文件或目录
find: ‘/run/user/1000/gvfs’: 权限不够
^[OP[root@localhost ~]# ^C

```

![image-20221004160437852](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050057.png)

![image-20221004160507049](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050193.png)

![image-20221004160625932](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050336.png)

![image-20221004160757844](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050883.png)

![image-20221004160909594](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050295.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050667.png)

![image-20221006141857041](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050265.png)

## 第21课

![image-20221006142854896](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050107.png)

![image-20221006143123773](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050963.png)

重点回顾

![image-20221006144033715](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050634.png)

![image-20221006144339840](https://cdn.jsdelivr.net/gh/yzk656/image/202212242050321.png)

![image-20221006144549667](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051388.png)

![image-20221006144710805](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051395.png)

![image-20221006145034536](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051045.png)

## 第22次课

> vi与vim

![image-20221010100442843](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051588.png)

![image-20221010102344011](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051062.png)

![image-20221010102356343](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051779.png)

![image-20221010103437002](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051436.png)

![image-20221010103820044](https://cdn.jsdelivr.net/gh/yzk656/image/202212242051756.png)

![image-20221010104616204](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052202.png)

![image-20221010104902422](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052580.png)

## 第23次课

删除、复制、粘贴

xX：在第一列中，x为向后删除一个字符，X为向前删除一个字符

nx：n为数字，连续向后删除n个字符

dd：删除游标所在那一列

ndd：n为数字，删除光标所在向下的n列

d1G：删除光标所在第一列的所有数据

dG：删除光标所在最后一列的所有数据

d$：删除游标所在的最后一个字符

d0：删除游标所在处，到该列的最前面一个字符

nyy：n为数字，复制光标所在的向下n列

yy：复制游标所处的那一列

![image-20221011152928939](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052108.png)

![image-20221011153343880](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052813.png)

![image-20221011153622071](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221011153622071.png)



![image-20221011154242407](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052252.png)

![image-20221011154311220](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20221011154311220.png)

![image-20221011154622726](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052065.png)



暂存档

![image-20221011155620095](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052966.png)



模拟断电操作

![image-20221011155938815](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052773.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052261.png)



## 第24次课

![image-20221013141555263](https://cdn.jsdelivr.net/gh/yzk656/image/202212242052421.png)

![image-20221013141921297](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053950.png)

```
[root@localhost temp]# alias
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'

```

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053988.png)

![image-20221013144355471](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053134.png)

![image-20221013144735479](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053990.png)

# 常用Linux指令

## 2023-03-28

>  清空文件内容

```java
> file_name
```

> 创建sh文件

```java
touch file_name.sh
```

> 运行sh文件

```java
sh file_name
```

> 修改但不保存

```java
:q!
```

> 删除文件

```java
rm -f file_name
```

> 读取文件

```java
cat file_name
```

> 修改文件权限

```java
r w e(执行)  owner group others
4 2 1  

chmod xxx file_name    
```

























































​		
