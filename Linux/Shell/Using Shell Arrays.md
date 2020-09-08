# 使用shell 数组
在本章中，我们将讨论如何在Unix中使用shell数组。 Shell变量足以容纳单个值。这些变量称为标量变量。

Shell支持另一种类型的变量，称为数组变量。这可以同时保存多个值。数组提供了一种对一组变量进行分组的方法。您可以使用存储所有其他变量的单个数组变量来代替为所需的每个变量创建新名称。

命名数组时，适用于Shell变量的所有命名规则都适用。

## 定义数组值
数组变量和标量变量之间的差异可以解释如下。

假设您试图将各个学生的姓名表示为一组变量。每个单独的变量都是标量变量，如下所示-
```
NAME01 =“ Zara”
NAME02 =“ Qadir”
NAME03 =“ Mahnaz”
NAME04 =“ Ayan”
NAME05 =“雏菊”
```
我们可以使用单个数组来存储所有上述名称。以下是创建数组变量的最简单方法。这有助于为其一个索引分配一个值。

array_name [index] = value
这里array_name是数组的名称，index是您要设置的数组中项目的索引，value是您要为该项目设置的值。

例如，以下命令-
```
NAME [0] =“ Zara”
NAME [1] =“ Qadir”
NAME [2] =“ Mahnaz”
NAME [3] =“ Ayan”
NAME [4] =“雏菊”
```
如果您使用的是ksh shell，则这是数组初始化的语法-

设置-A array_name value1 value2 ... valuen
如果您使用的是bash shell，则这是数组初始化的语法-

array_name = {value1 ... valuen）
访问数组值
设置任何数组变量后，可以按以下方式访问它：

$ {array_name [index]}
这里array_name是数组的名称，而index是要访问的值的索引。以下是了解概念的示例-

```shell
#!/bin/sh

NAME[0]="Zara"
NAME[1]="Qadir"
NAME[2]="Mahnaz"
NAME[3]="Ayan"
NAME[4]="Daisy"
echo "First Index: ${NAME[0]}"
echo "Second Index: ${NAME[1]}"
```

```
$./test.sh
First Index: Zara
Second Index: Qadir
```
您可以通过以下方式之一访问数组中的所有项目：

$ {array_name [*]}
$ {array_name [@]}
这里array_name是您感兴趣的数组的名称。以下示例将帮助您理解概念-

```shell
#!/bin/sh

NAME[0]="Zara"
NAME[1]="Qadir"
NAME[2]="Mahnaz"
NAME[3]="Ayan"
NAME[4]="Daisy"
echo "First Method: ${NAME[*]}"
echo "Second Method: ${NAME[@]}"
```
上面的示例将产生以下结果-

```
$./test.sh
First Method: Zara Qadir Mahnaz Ayan Daisy
Second Method: Zara Qadir Mahnaz Ayan Daisy
```