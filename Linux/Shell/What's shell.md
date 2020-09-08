# 什么是Shell 脚本
Shell脚本是一种设计为由Unix / Linux Shell运行的计算机程序，它是以下之一：

- The Bourne Shell
- The C Shell
- The Korn Shell
- The GNU Bourne-Again Shell
Shell是命令行解释器，由Shell脚本执行的典型操作包括文件操作，程序执行和打印文本。

扩展Shell脚本
Shell脚本具有几个必需的构造，这些构造告诉外壳环境做什么和何时进行。当然，大多数脚本比上面的脚本更复杂。

毕竟，shell是一种真正的编程语言，其中包含变量，控制结构等。无论脚本变得多么复杂，它仍然只是顺序执行的命令的列表。

以下脚本使用read命令，该命令从键盘获取输入并将其分配为变量PERSON的值，最后将其打印在STDOUT上。
```shell
＃！/ bin / sh

＃作者：DongChan
＃版权（c）tomyyear@gmail.com
＃脚本如下：

echo “你叫什么名字？”
read PERSON
read “你好，$ PERSON”
```
这是脚本的示例运行-

```shell
$ ./test.sh
你叫什么名字？
DongChan
你好，DongChan
$
```
