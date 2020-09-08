# 什么是Unix/Linux？
Unix操作系统是介于计算机器和用户之前的程序。
计算机程序用于分配用户资源并协调计算机内部操作，在这里称为**操作系统**或者**内核**。
用户通过**shell**来与内核交流。**shell**是命令行解释器，它将用户输入的命令转换成内核听得懂的语言。
- Unix是开发于AT&T公司 Ken Thompson, Dennis Ritchie, Douglas McIlroy, and Joe Ossanna at Bell Labs.
- Unix有好几款衍生品，包括 Solaris Unix, AIX, HP Unix 和 BSD。 其中Linux是在开源操作系统中最流行的。
- 一个用户可以运行多个应用在同一时间，因此Unix是一个多任务环境

# Unix 架构
下面这张图是Unix系统的架构
<img src="./resources/linux/unix_architecture.jpg"/>
基本主要概念：
- Kernel内核是操作系统的核心。它与硬件和大多数任务交互，如内存管理、任务调度和文件管理。
- Shell是处理请求的实用程序。当您在终端上输入命令时，shell将解释该命令并调用您想要的程序。shell对所有命令使用标准语法。C Shell、Bourne Shell和Korn Shell是最著名的Shell，它们可用于大多数Unix变体。
- 您可以在日常活动中使用各种命令和实用程序。cp、mv、cat和grep等是命令和实用程序的几个示例。有超过250个标准命令以及许多其他通过第三方软件提供的命令。所有命令都带有各种选项。
- Unix中的所有数据都被组织成文件。然后将所有文件组织到目录中。这些目录被进一步组织成称为文件系统的树形结构。

## 登录Unix
```shell
login:

login : amrood
amrood's password:
Last login: Sun Jun 14 09:32:32 2009 from 62.61.164.73
$
```
您将获得一个命令提示符(有时称为$ prompt)，您可以在其中键入所有命令。例如，要检查calendar，需要输入cal命令，如下所示:

```shell
 $cal
   September 2020
Su Mo Tu We Th Fr Sa
       1  2  3  4  5
 6  7  8  9 10 11 12
13 14 15 16 17 18 19
20 21 22 23 24 25 26
27 28 29 30
```

### 简单功能
#### 更改密码
所有Unix系统都需要密码，以帮助确保您的文件和数据仍然是您自己的，并确保系统本身不受黑客和黑客的攻击。以下是更改密码的步骤-

步骤1-要开始，请在命令提示符下键入密码，如下所示。

步骤2-输入您的旧密码，您当前正在使用的密码。

步骤3-输入您的新密码。始终保持足够复杂的密码，以便没人能猜到。但是请确保记住。

步骤4-您必须通过再次输入密码来验证密码。

$ passwd
更改密码
（当前）Unix密码：******
新的UNIX密码：*******
重新输入新的UNIX密码：*******
passwd：所有身份验证令牌已成功更新

$
注意-我们在此处添加了星号（*），只是为了显示您需要在系统上输入当前密码和新密码的位置。键入时不会显示任何字符。

#### 列出目录和文件
Unix中的所有数据都组织成文件。所有文件都组织在目录中。这些目录被组织成称为文件系统的树状结构。

您可以使用ls命令列出目录中所有可用的文件或目录。以下是将ls命令与-l选项一起使用的示例。

$ ls -l
总计19621
drwxrwxr-x 2 amrood amrood 4096 12月25日09:59 UML
-rw-rw-r-- 1 amrood amrood 5341 12月25日08:38 uml.jpg
drwxr-xr-x 2 amrood amrood 4096 2006年2月15日univ
drwxr-xr-x 2 root root 4096 2007年12月9日urlspedia
-rw-r--r-- 1个根目录276480 2007年12月9日urlspedia.tar
drwxr-xr-x 8 root root 4096 2007年11月25日usr
-rwxr-xr-x 1根目录3192 2007年11月25日webthumb.php
-rw-rw-r-- 1个amrood amrood 20480 2007年11月25日webthumb.tar
-rw-rw-r-- 1个amrood amrood 5654 2007年8月9日yourfile.mid
-rw-rw-r-- 1个amrood amrood 166255 2007年8月9日yourfile.swf

$
在这里，以d .....开头的条目代表目录。例如，uml，univ和urlspedia是目录，其余条目是文件。

#### 你是谁？
*登录系统后，您可能会想知道：我是谁？*

找出“你是谁”的最简单方法是输入whoami命令-

$ whoami
 

$
在您的系统上尝试。此命令列出与当前登录名关联的帐户名。您也可以尝试由我命令谁来获取有关您自己的信息。

#### 谁登录？
有时您可能想知道谁同时登录了计算机。

根据您希望了解其他用户的多少，可以使用三个命令来获取此信息：用户，用户和w。

```shell
$users
 ty tele

$who
amrood ttyp0 10月8日14:10（limbo）
bablu ttyp2 10月4日09:08（calliope）
qadir ttyp4 10月8日12:09（dent）

$
```
在系统上尝试使用w命令检查输出。这列出了与登录系统的用户相关联的信息。

注销
完成会话后，您需要注销系统。这是为了确保没有其他人访问您的文件。

#### 登出

只需在命令提示符下键入logout命令，系统就会清理所有内容并断开连接。

#### 系统关机
通过命令行正确关闭Unix系统的最一致的方法是使用以下命令之一-

###### 命令与说明
1. halt

立即关闭系统

2. init 0

在关闭之前，使用预定义的脚本关闭系统电源以同步和清理系统

3. init 6

通过完全关闭然后重新启动系统来重新启动系统

4. poweroff

通过关闭电源关闭系统

5. reboot

重新启动系统

6. shutdown

关闭系统

通常，您必须是超级用户或root（Unix系统上最特权的帐户）才能关闭系统。但是，在某些独立的或个人拥有的Unix机器上，管理用户（有时是普通用户）可以这样做。