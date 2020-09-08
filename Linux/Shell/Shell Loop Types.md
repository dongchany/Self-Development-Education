# 重复执行，你愿意负责的行为
在本章中，我们将讨论Unix中的Shell循环。循环是功能强大的编程工具，使您能够重复执行一组命令。在本章中，我们将研究以下可供Shell程序员使用的循环类型-

while循环
for循环
直到循环
选择循环
您将根据情况使用不同的循环。例如，while循环执行给定命令，直到给定条件保持为真为止；直到直到给定条件变为true为止，直到执行循环。

掌握良好的编程习惯后，您将获得专业知识，从而根据情况开始使用适当的循环。在这里，while和for循环在大多数其他编程语言（例如C，C ++和PERL等）中可用。

嵌套循环
所有循环都支持嵌套概念，这意味着您可以将一个循环放入另一个类似的或不同的循环中。根据您的要求，此嵌套最多可以无限次。

这是嵌套while循环的示例。其他循环可以基于编程要求以类似的方式嵌套-

循环嵌套
可以将while循环用作另一个while循环主体的一部分。

句法
```
while command1 ; # this is loop1, the outer loop
do
   Statement(s) to be executed if command1 is true

   while command2 ; # this is loop2, the inner loop
   do
      Statement(s) to be executed if command2 is true
   done

   Statement(s) to be executed if command1 is true
done
```
例
这是循环嵌套的简单示例。让我们在您用来计数到9的循环内添加另一个倒数循环-

```shell
#!/bin/sh

a=0
while [ "$a" -lt 10 ]    # this is loop1
do
   b="$a"
   while [ "$b" -ge 0 ]  # this is loop2
   do
      echo -n "$b "
      b=`expr $b - 1`
   done
   echo
   a=`expr $a + 1`
done
```
这将产生以下结果。重要的是要注意echo -n在这里是如何工作的。在这里，-n选项使echo避免打印换行符。
```
0
1 0
2 1 0
3 2 1 0
4 3 2 1 0
5 4 3 2 1 0
6 5 4 3 2 1 0
7 6 5 4 3 2 1 0
8 7 6 5 4 3 2 1 0
9 8 7 6 5 4 3 2 1 0
```