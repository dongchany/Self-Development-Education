Unix / Linux中的AWK命令
Awk是一种脚本语言，用于处理数据和生成报告.awk命令编程语言无需编译，并且允许用户使用变量，数字函数，字符串函数和逻辑运算符。

Awk是一种实用程序，使程序员能够以语句的形式编写微小但有效的程序，这些语句定义了将在文档的每一行中搜索的文本模式，以及在文件中找到匹配项时应采取的措施。 Awk主要用于模式扫描和处理。它搜索一个或多个文件以查看它们是否包含与指定模式匹配的行，然后执行关联的操作。

Awk是开发商名称的缩写-Aho，Weinberger和Kernighan。

AWK可以做什么？

1. AWK操作：
（a）逐行扫描文件
（b）将每个输入行拆分为字段
（c）在匹配的行上执行操作



2.适用于：
（a）转换数据文件
（b）生成格式化的报告

3.编程构造：
（a）格式化输出行
（b）算术和字符串运算
（c）条件循环

句法：

awk选项'selection _criteria {action}'输入文件>输出文件
选项：

-f program-file：从文件中读取AWK程序源
                  程序文件，而不是从
                  第一个命令行参数。
-F fs：将fs用作输入字段分隔符
样例命令

例：
对于以下所有情况，将以下文本文件视为输入文件。

$cat> employee.txt
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000 
1. Awk的默认行为：默认情况下，Awk打印指定文件中的每一行数据。

$ awk'{print}'employee.txt
输出：

```
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000 
```
在上面的示例中，没有给出任何模式。因此，这些动作适用于所有行。不带任何参数的动作打印默认情况下会打印整行，因此它会打印文件的所有行而不会失败。

2.打印匹配出来的格式

$ awk'/ manager / {print}'employee.txt
输出：
```
ajay manager account 45000
varun manager sales 50000
amit manager account 47000 
```
在上面的示例中，awk命令显示与“ manager”匹配的所有行。

3.将行拆分为字段：对于每个记录（即行），awk命令默认情况下将由空格字符分隔的记录拆分并将其存储在$ n变量中。如果该行有4个单词，它将分别存储在$ 1，$ 2，$ 3和$ 4中。 $ 0代表整行。

$ awk'{print $ 1，$ 4}'employee.txt
输出：
```
ajay 45000
sunil 25000
varun 50000
amit 47000
tarun 15000
deepak 23000
sunil 13000
satvik 80000 
```

在上面的示例中，$ 1和$ 4分别表示Name和Salary字段。

Awk中的内置变量

Awk的内置变量包括字段变量-$ 1，$ 2，$ 3等（$ 0是整行），这些变量将一行文本分成单个单词或称为字段的段。

NR：NR命令保留输入记录数的当前计数。请记住，记录通常是行。 Awk命令对文件中的每个记录执行一次模式/操作语句。



NF：NF命令对当前输入记录中的字段数进行计数。

FS：FS命令包含字段分隔符，用于分隔输入行上的字段。默认值为“空白”，表示空格和制表符。可以将FS重新分配给另一个字符（通常在BEGIN中）以更改字段分隔符。

RS：RS命令存储当前记录分隔符。由于默认情况下，输入行是输入记录，因此默认记录分隔符是换行符。

OFS：OFS命令存储输出字段分隔符，当Awk打印它们时，它将分隔字段。默认值为空格。每当打印的多个参数用逗号分隔时，它将在每个参数之间打印OFS的值。

ORS：ORS命令存储输出记录分隔符，当Awk打印它们时，它将分隔输出行。默认值为换行符。 print会在任何打印结束时自动输出ORS的内容。

例子：

NR内置变量的使用（显示行号）

```
$ awk '{print NR,$0}' employee.txt 
```
输出：
```
1 ajay manager account 45000
2 sunil clerk account 25000
3 varun manager sales 50000
4 amit manager account 47000
5 tarun peon sales 15000
6 deepak clerk sales 23000
7 sunil peon sales 13000
8 satvik director purchase 80000 
```