# Shell 变量
在本章中，我们将学习如何在Unix中使用Shell变量。变量是我们为其分配值的字符串。分配的值可以是数字，文本，文件名，设备或任何其他类型的数据。

变量不过是指向实际数据的指针。 Shell使您可以创建，分配和删除变量。

##  变量名
变量名称只能包含字母（a到z或A到Z），数字（0到9）或下划线字符（_）。

按照惯例，Unix shell变量将以大写字母命名。

以下示例是有效的变量名称-

_ALI
TOKEN_A
VAR_1
VAR_2
以下是无效变量名称的示例-

2_VAR
-VARIABLE
VAR1-VAR2
VAR_A！
之所以不能使用其他字符，例如！，*或-，是因为这些字符对Shell具有特殊的含义。

## 定义变量
变量定义如下-

variable_name =变量值
例如-

NAME =“DongChan”
上面的示例定义了变量NAME，并为其分配了值“DongChan”。这种类型的变量称为标量变量。标量变量一次只能保存一个值。

Shell使您可以将所需的任何值存储在变量中。例如-

VAR1 =“DongChan”
VAR2 = 100
访问值
要访问存储在变量中的值，请在其名称前加上美元符号（$）-

例如，以下脚本将访问已定义变量NAME的值并将其打印在STDOUT上-

```shell
＃！/ bin / sh

NAME =“DongChan”
echo $NAME
```
上面的脚本将产生以下值-

```shell
DongChan
```

## 只读变量
Shell提供了一种使用只读命令将变量标记为只读的方法。将变量标记为只读后，其值将无法更改。

例如，以下脚本在尝试更改NAME的值时生成错误-

```shell
＃！/ bin / sh

NAME =“ Zara Ali”
readonly NAME
NAME =“ Qadiri”
```
上面的脚本将产生以下结果-

```shell
/ bin / sh：NAME: This variable is read only.
```
## 取消设定变数
取消设置或删除变量将指示外壳程序从其跟踪的变量列表中删除该变量。取消设置变量后，将无法访问该变量中的存储值。

以下是使用unset命令取消定义的变量的语法-
```shell
unset variable_name
```
上面的命令取消设置已定义变量的值。这是一个简单的示例，演示命令如何工作-
```shell
＃！/ bin / sh

NAME =“DongChan”
unset NAME
echo $ NAME
```
上面的示例不打印任何内容。您不能使用unset命令取消设置标记为只读的变量。

## 变量类型
当Shell运行时，存在三种主要类型的变量-

- 局部变量-局部变量是存在于Shell当前实例中的变量。它不适用于由外壳程序启动的程序。它们在命令提示符下设置。

- 环境变量-环境变量可用于Shell的任何子进程。某些程序需要环境变量才能正常运行。通常，shell脚本仅定义其运行的程序所需的那些环境变量。

- Shell变量-Shell变量是Shell设置的特殊变量，shell要求Shell变量才能正常运行。这些变量中的一些是环境变量，而另一些是局部变量。