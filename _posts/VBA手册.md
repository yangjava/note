# VBA手册

[TOC]

# VBA概述

**VBA**代表**Visual Basic for Applications**，这是一种来自Microsoft的事件驱动编程语言，现在主要与Microsoft Office应用程序(如MSExcel，MS-Word和MS-Access)一起使用。

它帮助技术人员构建定制的应用程序和解决方案，以增强这些应用程序的功能。这个工具的优点是不需要在电脑上安装visual basic，直接从安装Office软件中就能隐含地使用来达到目的。

您可以在所有Office版本中使用VBA，从MS-Office 97到MS-Office 2016以及任何最新版本。 在VBA中，Excel VBA是最流行的。使用VBA的好处是可以使用线性编程在MS Excel中建立非常强大的工具。

## VBA之HelloWorld

我们来学习如何逐步编写一个简单的宏。

**第1步** - 首先，在*Excel 2016中*启用“开发者”菜单。要完成这个设置，请点击左上角菜单：*文件* -> *选项*。如下图所示 -
![img](http://www.yiibai.com/uploads/images/201711/2111/885141140_43872.png)

**第2步** - 点击*“自定义功能区”*选项卡并选中*“开发工具”*。然后点击*“确定”*。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/857141144_84580.png)

**第3步** - *“开发工具”*功能区出现在菜单栏中。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/423141147_74226.png)

**第4步** - 点击 *“Visual Basic”* 按钮打开VBA编辑器。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/621141149_18613.png)

**第5步** - 通过添加一个按钮启动脚本。点击*插入* -> 选择*按钮*。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/400141156_38470.png)

**第6步** - 右键单击按钮并选择*“属性”*。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/755151101_15726.png)

**第7步** - 编辑名称和标题，如下面的截图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/255151104_56017.png)

**第8步** - 现在双击该按钮，将显示子程序编写区域，如下图所示 -

![img](http://www.yiibai.com/uploads/images/201711/2111/796151106_42247.png)

**第9步** - 通过简单编码，添加一条消息，运行并测试。如下图所示 -

```vb
Private Sub say_hello_Click()
    MsgBox "Hi,欢迎您学习VBA~!"
End Sub
Vb
```

**第10步** - 点击按钮执行子程序，子程序的输出如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/150151111_21939.png)

这样一个简单的VBA程序就编写完成了。

## VBA术语

在本章中，将介绍常用的Excel VBA术语。这些术语将在很多的模块中使用，因此理解其中的每一个术语都很重要。

### 模块

模块是编写代码的区域。如下图中，这是一个新的工作簿，因此没有任何模块。

![img](http://www.yiibai.com/uploads/images/201711/2111/896151122_99543.png)

要插入模块，请导航到*插入* -> *模块*。当插入模块之后，就会有一个名称为*“模块1”*的模块被创建了。如下图所示 - 

![插入模块](http://www.yiibai.com/uploads/images/201711/2111/306151124_96510.png)

插入模块完成之后，就可以在模块中编写VBA代码，代码写在一个过程(*Sub*)中。 一个过程/子过程是一系列的VBA语句，指示要做什么工作。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/725151127_71361.png)

### 程序/过程

程序(也叫作过程)是作为一个整体执行的一组语句，它指示Excel如何执行特定的任务。 执行的任务可能是一个非常简单或非常复杂的任务。不过，把复杂的程序分解成小的程序是一个很好的做法。

程序的两种主要类型，它们分别是：子程序(`Sub`)和函数(`Function`)。下面是一段简单的代码 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/188151132_42143.png)

### 函数

函数是一组可重用的代码，可以在程序中的任何地方调用。 这消除了一遍又一遍地编写相同的代码的需要。 这有助于程序员将大型程序划分为许多小型且可管理的功能。

除了内置函数外，VBA还允许编写用户定义的函数，并在 `Function` 和 `End Function` 关键字之间写入语句。

### 子过程

子程序的功能与功能类似。虽然子程序没有返回值，函数可能会或不会返回一个值。子程序可以不使用`call`关键字调用。子程序总是在`Sub`和`End Sub`之间包含执行的语句。

## VBA宏注释

注释用于记录程序逻辑和用户信息，其他程序员将来可以阅读并理解相同的代码无缝工作。

它包括由开发者，修改者以及还可以包括合并逻辑的信息。 解释器在执行时忽略注释。

VBA中的注释用两种方法表示，它们分别如下 - 

- 任何以单引号(`'`)开头的语句都被视为注释。以下是注释的一个例子。

  可以位于别的语句之尾，也可单独一行

  ```vb
  ' This Script is invoked after successful login 
  ' Written by : Yiibai Yiibai
  ' Return Value : True / False
  ```

- 任何以关键字`"REM"`开头的语句。以下是注释的一个例子。

  只能单独一行

  ```vb
  REM This Script is written to Validate the Entered Input 
  REM Modified by  : Yiibai Yiibai /user2
  ```

# VBA基础

## VBA变量

### 变量

变量是一个指定的内存位置，用于保存脚本执行过程中可以更改的值。以下是命名变量的基本规则。

- 变量名称必须使用一个字母作为第一个字符。
- 变量名称不能使用空格，句点(`.`)，感叹号(`!`)或字符`@`，`&`，`$`，`#`。
- 变量名称的长度不能超过`255`个字符。
- 不能使用Visual Basic保留关键字作为变量名称。

### **语法**

在VBA中，变量需要在使用它们之前声明。

```vb
Dim <<variable_name>> As <<variable_type>>
```

### 数据类型

有许多VBA数据类型，可以分为两大类，即数字和非数字数据类型。

#### 1. 数字数据类型

下表显示数字数据类型和允许的值范围。

| 编号 | 数字类型   | 范围值                                                       |
| ---- | ---------- | ------------------------------------------------------------ |
| 1    | `Byte`     | 0 ~ 255                                                      |
| 2    | `Integer`  | -32,768 ~ 32,767                                             |
| 3    | `Long`     | -2,147,483,648 ~ 2,147,483,648                               |
| 4    | `Single`   | 负值：`-3.402823E+38 ~ -1.401298E-45`，正值： `1.401298E-45 ~ 3.402823E+38` |
| 5    | `Double`   | 负值：`-1.79769313486232e+308 ~ -4.94065645841247E-324`，正值： `4.94065645841247E-324 ~ 1.79769313486232e+308` |
| 6    | `Currency` | -922,337,203,685,477.5808 ~ 922,337,203,685,477.5807         |
| 7    | `Decimal`  | 如果不使用小数，则为`+/- 79,228,162,514,264,337,593,543,950,335`；如果使用小数，则为：`+/- 7.9228162514264337593543950335` |

#### 2. 非数字数据类型

下表显示了非数字数据类型和允许的值范围。

| 编号 | 数字类型            | 范围值                      |
| ---- | ------------------- | --------------------------- |
| 1    | 固定长度：`String`  | 1 ~ 65,400个字符            |
| 2    | 可变长度：`String`  | 0到20亿字符                 |
| 3    | `Date`              | 100年1月1日至9999年12月31日 |
| 4    | `Boolean`           | `True` / `False`            |
| 5    | `Object`            | 任何嵌入的对象              |
| 6    | `Variant (numeric)` | 任何大到double的数字值      |
| 7    | `Variant (text)`    | 与可变长度的`string`一样。  |

### 示例

在这个示例中，创建一个按钮并命名为*“VariablesDemo”* 来演示变量的使用。

![img](http://www.yiibai.com/uploads/images/201711/2111/713111123_24289.png)

参考实现的代码如下 - 

```vb
Private Sub VariablesDemo()
   Dim password As String

   password = "123456"

   Dim num As Integer
   num = 1234

   Dim BirthDay As Date

   BirthDay = DateValue("1998-10-11")

   MsgBox ("设置的密码是：" & password & Chr(10) & "num的值是：" & num & Chr(10) & "Birthday的值是：" & BirthDay)

End Sub
```

执行上面示例代码，得到以下结果 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/800111123_48443.png)

## VBA常量

### 常量

常量是一个命名的内存位置，用于保存脚本执行期间固定(无法更改)的值。如果用户试图更改常量值，则脚本执行结束时会出现错误。常量声明与声明变量相同。

以下是命名常量的规则 - 

- 常量名称必须使用一个字母作为第一个字符。
- 常量名称不能在名称中使用空格，句点(`.`)，感叹号(`!`)或字符`@`，`＆`，`$`，`#`。
- 常量名称的长度不能超过`255`个字符。
- 不能使用Visual Basic保留关键字作为常量名称。

### 语法

在VBA中，需要为声明的常量赋值。如果试图改变常量的值，就会抛出一个错误。VBA中常量的语法如下所示 - 

```vb
Const <<constant_name>> As <<constant_type>> = <<constant_value>>
```

### 示例

在这个示例中，创建一个`“ConstantDemo”`程序来演示如何使用常量。

![img](http://www.yiibai.com/uploads/images/201711/2111/618111134_97472.png)

参考以下代码实现 - 

```vb
Private Sub ConstantDemo()

   Const MyInteger As Integer = 720
   Const myDate As Date = #10/21/2000#
   Const myDay As String = "Sunday"

   MsgBox ("整数值是：" & MyInteger & Chr(10) & "myDate的值是：" & myDate & Chr(10) & "myDay 的值是：" & myDay)

End Sub
```

执行上面示例代码，得到以下结果 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/773111137_89219.png)

## VBA变量和常量注意点

（1）VBA允许使用未定义的变量，默认是变体变量

（2）在模块通用说明部分，加入Option Explicit语句可以强迫用户进行变量定义

（3）变量定义语句及变量作用域

![img](https://atts.w3cschool.cn/attachments/day_161018/201610181756022085.png)

一般变量作用域的原则是，那部分定义就在那部分起作用，模块中定义则在该模块那作用。

（4）常量为变量的一种特例，用Const定义，且定义时赋值，程序中不能改变值，作用域也如同变量作用域。如下定义：Const Pi=3.1415926 as single

## VBA运算符

### 运算符

运算符可以用一个简单的表达式定义，例如：`4 + 5`等于`9`。这里，`4`和`5`称为操作数，`+`被称为运算符。VBA支持以下类型的运算符 -

- 算术运算符
- 比较运算符
- 逻辑(或关系)运算符
- 连接运算符

### 算术操作符

以下是VBA支持算术运算符。

假设变量`A=5`，变量`B=10`，那么 -

| 运算符 | 描述                       | 示例             |
| ------ | -------------------------- | ---------------- |
| `+`    | 两个操作数相加             | `A + B = 15`     |
| `-`    | 两个操作数相减             | `A - B = -5`     |
| `*`    | 两个操作数相乘             | `A * B = 50`     |
| `/`    | 两个操作数相除             | `B / A = 2`      |
| `%`    | 模运算符，整数除法后的余数 | `B % A = 0`      |
| `^`    | 指数运算符                 | `B ^ A = 100000` |

有关如何使用，请参考[算术运算符示例](http://www.yiibai.com/vba/vba_arithmetic_operators.html)。

### 比较运算符

VBA支持的比较运算符如下所示。

假设变量`A=10`，变量`B=20`，则 -

| 运算符 | 描述                                                         | 示例                      |
| ------ | ------------------------------------------------------------ | ------------------------- |
| `=`    | 检查两个操作数的值是否相等。如果是，那么条件是真。           | `(A = B)`结果为：`False`  |
| `<>`   | 检查两个操作数的值是否不相等。如果值不相等，则条件为真。     | `(A <> B)`结果为：`True`  |
| `>`    | 检查左操作数的值是否大于右操作数的值。如果是，那么条件是真。 | `(A > B)`结果为：`False`  |
| `<`    | 检查左操作数的值是否小于右操作数的值。如果是，那么条件是真。 | `(A < B)`结果为：`True`   |
| `>=`   | 检查左操作数的值是否大于或等于右操作数的值。 如果是，那么条件是真。 | `(A >= B)`结果为：`False` |
| `<=`   | 检查左操作数的值是否小于或等于右操作数的值。如果是，那么条件是真。 | `(A <= B)`结果为：`True`  |

有关如何使用，请参考[比较运算符示例](http://www.yiibai.com/vba/vba_comparison_operators.html)。

### 逻辑运算符

以下由VBA支持的逻辑运算符。

假设变量`A=10`，变量`B=0`，则 -

| 运算符 | 描述                                                         | 示例                               |
| ------ | ------------------------------------------------------------ | ---------------------------------- |
| `AND`  | 逻辑`AND`运算符。如果两个条件都为真，则表达式为真。          | `A<>0 AND B<>0`结果为：`False`     |
| `OR`   | 逻辑`OR`运算符。如果两个条件中的任何一个为真，则条件为真。   | `A<>0 OR B<>0`结果为：`True`       |
| `NOT`  | 逻辑`NOT`运算符。用于反转其操作数的逻辑状态。 如果条件成立，那么逻辑非运算符结果是条件不成立。 | `NOT(a<>0 OR b<>0)`结果为：`False` |
| `XOR`  | 逻辑排除。它是`NOT`和`OR`运算符的组合。如果表达式中只有一个表达式的值为`True`，则结果为`True`。 | `(a<>0 XOR b<>0)`结果为：`True`    |

有关如何使用，请参考[逻辑运算符示例](http://www.yiibai.com/vba/vba_logical_operators.html)。

### 连接操作符

VBA支持以下连接运算符。

假设变量`A=5`，变量`B=10`，则 -

| 运算符 | 描述                           | 示例          |
| ------ | ------------------------------ | ------------- |
| `+`    | 将两个值添加为变量，其值是数字 | `A + B = 15`  |
| `&`    | 连接两个值                     | `A & B = 510` |

假设变量`A = "Microsoft"`，变量`B = "VBScript"`，则 -

| 运算符 | 描述       | 示例                               |
| ------ | ---------- | ---------------------------------- |
| `+`    | 连接两个值 | `A + B` 的结果为`MicrosoftVBScrip` |
| `&`    | 连接两个值 | `A & B` 的结果为`MicrosoftVBScrip` |

> 注 - 连接操作，可用于数字和字符串。输出取决于上下文，如果变量保存数字值或字符串值。

## VBA标识符

### 标识符

标识符是一种标识变量、常量、过程、函数、类等语言构成单位的符号，利用它可以完成对变量、常量、过程、函数、类等引用。VBA标识符规则如下 -

- 字母打头，由字母、数字和下划线组成，如A987b_23Abc
- 字符长度小于40，（Excel2002以上中文版本等，可以用汉字且长度可达254个字符）
- 不能与VB保留字重名，如public，private，dim，goto，next，with，integer，single等

### 书写规范

- VBA不区分标识符的字母大小写，一律认为是小写字母；
- 一行可以书写多条语句，各语句之间以冒号 :  分开；
- 一条语句可以多行书写，以空格加下划线 _  来标识下行为续行；
- 标识符最好能简洁明了，不造成歧义。

## VBA数据类型

VBA共有12种数据类型，具体见下表，此外用户还可以根据以下类型用Type自定义数据类型。

![VBA数据类型](https://atts.w3cschool.cn/attachments/image/20161018/1476784116445222.jpg)

# VBA语法

## VBA判断语句

### 判断语句

判断允许程序员控制脚本或其中一个部分的执行流程。执行由一个或多个条件语句控制。
以下是在大多数编程语言中找到的典型决策结构的一般形式。

![img](http://www.yiibai.com/uploads/images/201711/2211/190141147_38124.jpg)

VBA提供了以下类型的决策声明。 点击以下链接来查看它们的详细信息。

| 编号 | 语句                                                         | 描述                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | if语句                                                       | 一个`if`语句由一个布尔表达式和一个或多个语句组成。           |
| 2    | [if…else语句](http://www.yiibai.com/vba/vba_if_else_statement.html) | `if else`语句由一个布尔表达式和一个或多个语句组成。如果条件为`True`，则执行`If`语句下的语句。如果条件为`false`，则执行脚本的`Else`部分。 |
| 3    | [if…elseif…else语句](http://www.yiibai.com/vba/vba_if_elseif_else_statement.html) | 一个if语句，后跟一个或多个`else...if`语句，它由布尔表达式组成，接着是一个可选的`else`语句，当所有条件变为`false`时执行`else`语句块。 |
| 4    | [嵌套if语句](http://www.yiibai.com/vba/vba_nested_if_statements.html) | 一个`if`或`elseif`语句中可以嵌套另一个`if`或`elseif`语句。   |
| 5    | switch语句                                                   | 一个`switch`语句允许一个变量与一个值列表进行测试。           |

### VBA if语句

一个`if`语句由一个布尔表达式和一个或多个语句组成。如果条件被评估为`True`，则执行`If`条件块下的语句。如果条件被评估为`False`，则执行`If`循环块后面的语句。

#### 语法

以下是VBScript中的`If`语句的语法。

```vb
If(boolean_expression) Then
   Statement 1
   .....
   .....
   Statement n
End If
Vb
```

#### **流程**

![img](http://www.yiibai.com/uploads/images/201711/2211/810151106_74384.jpg)

#### 示例

为了演示目的，实现一个函数找出两个Excel中最大的数字。

![img](http://www.yiibai.com/uploads/images/201711/2211/111151114_29213.png)

实现代码 - 

```vb
Private Sub if_demo_Click()
   Dim x As Integer
   Dim y As Integer

   x = 234
   y = 32

   If x > y Then
      MsgBox ("X 的值大于 Y 的值")
   End If
End Sub
Vb
```

当上面的代码被执行时，它会产生以下结果。

![img](http://www.yiibai.com/uploads/images/201711/2211/749151112_65406.png)

### VBA if...else语句

一个if语句由一个布尔表达式和一个或多个语句组成。如果条件评估为`True`，则执行`if`条件下的语句。如果条件评估为`False`，则执行`else`部分块下的语句。

#### 语法

以下是VBScript中的`if else`语句的语法。

```vb
If(boolean_expression) Then
   Statement 1
   .....
   .....
   Statement n
Else
   Statement 1
   .....
   ....
   Statement n
End If
Vb
```

#### **流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/189151119_31212.jpg)

#### 示例

为了演示目的，这里借助一个函数找出两个Excel中最大的数字。如下图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/572151122_76430.png)

参考实现代码 - 

```vb
Private Sub if_demo_Click()
   Dim x As Integer
   Dim y As Integer

   x = 10
   y = 20

   If x > y Then
      MsgBox ("X 的值大于 Y 的值")
   Else
      MsgBox ("Y 的值大于 X 的值")
   End If
End Sub
Vb
```

执行上面示例代码，得到以下结果 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/254151123_35074.png)

### VBA if...elseif...else语句

一个If语句，后面可以跟一个或多个由布尔表达式组成的`elseif`语句，然后是一个默认的`else`语句，当所有条件变为`false`时执行`else`语句块。

#### 语法

以下是VBScript中`If...Elseif...Else`语句的语法。

```vb
If(boolean_expression) Then
   Statement 1
   .....
   .....
   Statement n
ElseIf (boolean_expression) Then
   Statement 1
   .....
   ....
   Statement n
ElseIf (boolean_expression) Then
   Statement 1
   .....
   ....
   Statement n
Else
   Statement 1
   .....
   ....
   Statement n
End If
Vb
```

**流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/343151133_40526.jpg)

#### 示例

为了演示目的，这里借助一个函数找出两个Excel中最大的数字。如下图示 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/797151137_85108.png)

参考实现代码 - 

```vb
Private Sub if_demo_Click()
   Dim x As Integer
   Dim y As Integer

   x = 10
   y = 10

   If x > y Then
      MsgBox ("X 大于 Y 的值")
   ElseIf y > x Then
      MsgBox ("Y 大于 X 的值")
   Else
      MsgBox ("X 和 Y 的值相等")
   End If
End Sub
Vb
```

执行上面示例代码，得到以下结果 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/864151137_85899.png)

### VBA嵌套if语句

一个`If`或`ElseIf`语句可以嵌套在另一个`If`或`ElseIf`语句中。内部的`If`语句是根据最外层的`If`语句执行的。这使得VBScript能够轻松处理复杂的条件。

#### 语法

以下是VBScript中嵌套的`If`语句的语法。

```vb
If(boolean_expression) Then
   Statement 1
   .....
   .....
   Statement n

   If(boolean_expression) Then
      Statement 1
      .....
      .....
      Statement n
   ElseIf (boolean_expression) Then
      Statement 1
      .....
      ....
      Statement n
   Else
      Statement 1
      .....
      ....
      Statement n
   End If
Else
   Statement 1
    .....
    ....
   Statement n
End If
Vb
```

#### 示例

为了演示目的，这里借助一个函数来判断一个正数的类型。如下图中所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/438151159_66969.png)

参考实现代码 - 

```vb
Private Sub nested_if_demo_Click()
   Dim a As Integer
   a = 12

   If a > 0 Then
      MsgBox ("The Number is a POSITIVE Number")

      If a = 1 Then
         MsgBox ("The Number is Neither Prime NOR Composite")
      ElseIf a = 2 Then
         MsgBox ("The Number is the Only Even Prime Number")
      ElseIf a = 3 Then
         MsgBox ("The Number is the Least Odd Prime Number")
      Else
         MsgBox ("The Number is NOT 0,1,2 or 3")
      End If
   ElseIf a < 0 Then
      MsgBox ("The Number is a NEGATIVE Number")
   Else
      MsgBox ("The Number is ZERO")
   End If
End Sub
Vb
```

执行上面示例代码，得到以下结果 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/825161100_65751.png)

点击*确定*按钮后，如下所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/245161101_38411.png)

### VBA switch语句

当用户想要根据Expression的值执行一组语句时，使用`Switch Case`语句。 每个值被称为一个”情况”，并根据每种情况变量接通测试。如果测试表达式与用户指定的任何`Case`不匹配，则执行`Case Else`语句。

`Case Else`是`Select Case`中的一个可选语句，但是，总是使用一个`Case Else`语句是一个很好的编程习惯。

#### 语法

以下是VBScript中的`Switch`语句的语法。

```vb
Select Case expression
   Case expressionlist1
      statement1
      statement2
      ....
      ....
      statement1n
   Case expressionlist2
      statement1
      statement2
      ....
      ....
   Case expressionlistn
      statement1
      statement2
      ....
      ....   
   Case Else
      elsestatement1
      elsestatement2
      ....
      ....
End Select
Vb
```

#### 示例

为了演示目的，这里通过一个函数的来计算整型的类型。参考以下图 - 

![img](http://www.yiibai.com/uploads/images/201711/2211/868161133_75363.png)

参考示例代码 - 

```vb
Private Sub switch_demo_Click()
   Dim MyVar As Integer
   MyVar = 1

   Select Case MyVar
      Case 1
         MsgBox "The Number is the Least Composite Number"
      Case 2
         MsgBox "The Number is the only Even Prime Number"
      Case 3
         MsgBox "The Number is the Least Odd Prime Number"
      Case Else
         MsgBox "Unknown Number"
   End Select
End Sub
```

执行上面示例代码，得到以下结果  -

![img](http://www.yiibai.com/uploads/images/201711/2211/302161126_59880.png)

## VBA循环语句

当需要多次执行一段代码时，就可以使用循环语句。 一般来说，语句是按顺序执行的：函数中的第一个语句首先执行，然后是第二个，依此类推。

编程语言提供了各种控制结构，允许更复杂的执行路径。

循环语句允许多次执行语句或语句组。 以下是VBA中循环语句的一般形式。

![img](http://www.yiibai.com/uploads/images/201711/2211/554201149_24281.jpg)

VBA提供以下类型的循环来处理循环需求。点击以下链接查看详细信息。

| 编号 | 循环类型                                                     | 描述                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | [for循环](http://www.yiibai.com/vba/vba_for_loop.html)       | 多次执行一系列语句，缩写管理循环变量的代码。                 |
| 2    | [for…each循环](http://www.yiibai.com/vba/vba_foreach_loop.html) | 如果组中至少有一个元素并为组中的每个元素重复执行，则执行此操作。 |
| 3    | [while…wend循环](http://www.yiibai.com/vba/vba_while_wend_loop.html) | 这在执行循环体之前测试条件。                                 |
| 4    | [do…while循环](http://www.yiibai.com/vba/vba_do_while_loop.html) | `do..while`语句只要条件为`True`就会被执行(即，)循环应该被重复直到条件为`False`。 |
| 5    | do…until循环                                                 | 只要条件是False，do..Until语句就会被执行(即，)循环应该被重复直到条件为真。 |

### VBA for循环

`for`循环是一种重复控制结构，它允许开发人员有效地编写需要执行特定次数的循环。

#### 语法

以下是VBA中`for`循环的语法。

```vb
For counter = start To end [Step stepcount]
   [statement 1]
   [statement 2]
   ....
   [statement n]
   [Exit For]
   [statement 11]
   [statement 22]
   ....
   [statement n]
Next
Vb
```

**流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/756091105_76454.jpg)

以下是`For`循环中的控制流程 -

- `For`步骤先执行。这一步允许您初始化任何循环控制变量，并递增步进计数器变量。
- 其次，评估条件。 如果评估结果为：`True`，则循环体被执行。 如果为`False`，则循环体不会执行，并且控制流将跳转到紧跟在`For`循环之后的下一个语句。
- 在执行`For`循环体之后，控制流将跳转到下一个语句。 这个语句更新任何循环控制变量。 它根据步计数器值进行更新。
- 现在条件再次评估。 如果条件为：`True`，则循环执行并且该过程重复自身(循环体，然后递增步，然后再次条件)。 条件变为`False`后，`For`循环终止。

#### 示例

添加一个模块，并添加以下函数代码 - 

```vb
Private Sub Constant_demo_Click()
   Dim a As Integer
   a = 10

   For i = 0 To a Step 2
      MsgBox ("The value is i is : " & i)
   Next
End Sub
Vb
```

当上面的代码被编译并执行时，会产生类似以下结果。

```shell
The value is i is : 0

The value is i is : 2

The value is i is : 4

The value is i is : 6

The value is i is : 8

The value is i is : 10
Shell
```

### VBA For Each循环

`For Each`循环用于为数组或集合中的每个元素执行语句或一组语句。
`For Each`循环与`For`循环类似; 然而，`For Each`循环是为数组或组中的每个元素执行的。 因此，这种类型的循环中将不存在步计数器。 它主要用于数组或在文件系统对象的上下文中使用，以便递归操作。

#### 语法

以下是VBA中`For Each`循环的语法。

```vb
For Each element In Group
   [statement 1]
   [statement 2]
   ....
   [statement n]
   [Exit For]
   [statement 11]
   [statement 22]
Next
Vb
```

#### 示例

```vb
Private Sub Constant_demo_Click()  
   'fruits is an array
   fruits = Array("苹果", "橙子", "樱桃")
   Dim fruitnames As Variant

   'iterating using For each loop.
   For Each Item In fruits
      fruitnames = fruitnames & Item & Chr(10)
   Next

   MsgBox fruitnames
End Sub
Vb
```

当执行上面的代码时，它会在每行中打印一个项目的所有水果名称。

![img](http://www.yiibai.com/uploads/images/201711/2211/426091128_36050.png)

### VBA While Wend循环

在`While...Wend`循环中，如果条件为`True`，则会执行所有语句，直到遇到`Wend`关键字。

如果条件为`false`，则退出循环，然后控件跳转到`Wend`关键字后面的下一个语句。

#### 语法

以下是VBA中`While..Wend`循环的语法。

```vb
While condition(s)
   [statements 1]
   [statements 2]
   ...
   [statements n]
Wend
Vb
```

**流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/133091131_84278.jpg)

#### 示例

参考以下示例代码的实现 - 

```vb
Private Sub Constant_demo_Click()
   Dim Counter :  Counter = 10   

   While Counter < 15     ' Test value of Counter.
      Counter = Counter + 1   ' Increment Counter.
      msgbox "The Current Value of the Counter is : " & Counter
   Wend   ' While loop exits if Counter Value becomes 15.
End Sub
Vb
```

当上面的代码被执行时，它会在消息框中打印以下内容。

```shell
The Current Value of the Counter is : 11 

The Current Value of the Counter is : 12 

The Current Value of the Counter is : 13 

The Current Value of the Counter is : 14 

The Current Value of the Counter is : 15
Shell
```

### VBA Do...While循环

一个`Do...while`循环用于只要条件为真就重复一组语句。该条件可以在循环开始时或循环结束时检查。

#### 语法

以下是VBA中的一个`Do...While`循环的语法。

```vb
Do While condition
   [statement 1]
   [statement 2]
   ...
   [statement n]
   [Exit Do]
   [statement 1]
   [statement 2]
   ...
   [statement n]
Loop
Vb
```

**流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/192091139_58300.jpg)

#### 示例

以下示例使用`Do...while`循环来检查循环开始处的条件。循环内部的语句只有在条件成立时才被执行。

```vb
Private Sub Constant_demo_Click()
   Do While i < 5
      i = i + 1
      msgbox "The value of i is : " & i
   Loop
End Sub
Vb
```

当上面的代码被执行时，它会在消息框中输出下面的输出。

```vb
The value of i is : 1

The value of i is : 2

The value of i is : 3

The value of i is : 4

The value of i is : 5
Vb
```

#### 备用/替代语法

另外还有一个替代语句`for...while`循环，用于在循环结束时检查条件。下面的例子解释了这两种语法的主要区别。语法 - 

```vb
Do 
   [statement 1]
   [statement 2]
   ...
   [statement n]
   [Exit Do]
   [statement 1]
   [statement 2]
   ...
   [statement n]
Loop While condition
Vb
```

#### 示例

以下示例使用`Do...while`循环来检查循环结束时的条件。循环内的语句至少执行一次，即使条件为`False`。

```vb
Private Sub Constant_demo_Click() 
   i = 10
   Do
      i = i + 1
      MsgBox "The value of i is : " & i
   Loop While i < 3 'Condition is false.Hence loop is executed once.
End Sub
Vb
```

当上面的代码被执行时，它会在消息框中输出下面的输出。

![img](http://www.yiibai.com/uploads/images/201711/2211/184091143_23669.png)

​		

## VBA循环控制语句

循环控制语句从正常顺序改变执行。 当执行离开一个作用域时，循环中的所有其余语句都不会被执行。

VBA支持以下控制语句。点击以下链接查看详细信息。

| 编号 | 控制语句                                                     | 描述                                         |
| ---- | ------------------------------------------------------------ | -------------------------------------------- |
| 1    | [Exit For语句](http://www.yiibai.com/vba/vba_exit_for_statement.html) | 终止For循环语句并将执行转移到循环之后的语句  |
| 2    | [Exit Do语句](http://www.yiibai.com/vba/vba_exit_do_statement.html) | 终止Do While语句并将执行转移到循环之后的语句 |

### VBA Exit For语句

当想要根据特定标准退出`For`循环时，就可以使用`Exit For`语句。当执行`Exit For`时，控件会立即跳转到`For`循环之后的下一个语句。

#### 语法

以下是在VBA中`Exit For`语句的语法。

```vb
Exit For
Vb
```

**流程图**

![img](http://www.yiibai.com/uploads/images/201711/2211/348101100_46336.jpg)

#### 示例

以下使用`Exit For`语句的示例。 如果计数器(`i`)的值达到`4`，则退出`For`循环，并在`For`循环之后立即跳转到下一个语句。

```vb
Private Sub Constant_demo_Click()
   Dim a As Integer
   a = 10

   For i = 0 To a Step 2 'i is the counter variable and it is incremented by 2
      MsgBox ("The value is i is : " & i)
      If i = 4 Then
         i = i * 10 'This is executed only if i=4
         MsgBox ("The value is i is : " & i)
         Exit For 'Exited when i=4
      End If
   Next
End Sub
```

当执行上面的代码时，它将在消息框中输出以下输出。

```shell
The value is i is : 0

The value is i is : 2

The value is i is : 4

The value is i is : 40
Shell
```

### VBA Exit Do语句	

当想要根据特定标准退出`Do`循环时，可使用`Exit Do`语句。 它可以同时用于`Do...While`和`Do...Until`直到循环。

当`Exit Do`被执行时，控制器在`Do`循环之后立即跳转到下一个语句。

#### 语法

以下是在VBA中`Exit Do`语句的语法。

```vb
 Exit Do
Vb
```

#### 示例

以下示例演示如何使用`Exit Do`语句，如果计数器的值达到`10`，则退出`Do`循环，并在`For`循环之后立即跳转到下一个语句。

```vb
Private Sub Constant_demo_Click()
   i = 0
   Do While i <= 100
      If i > 10 Then
         Exit Do   ' Loop Exits if i>10
      End If
      MsgBox ("The Value of i is : " & i)
      i = i + 2
   Loop
End Sub
Vb
```

当上面的代码被执行时，它会在消息框中输出下面的输出。

```shell
The Value of i is : 0

The Value of i is : 2

The Value of i is : 4

The Value of i is : 6

The Value of i is : 8

The Value of i is : 10
```

## VBA字符串

### 字符串

字符串是一个字符序列，可以由字母，数字，特殊字符或全部字符组成。 如果一个变量被包含在双引号`""`中，则被认为是一个字符串。

### **语法**

```vb
variable_name = "this is a string"
```

### **简单示例**

```vb
str1 = "string"   ' Only Alphabets
str2 = "132.45"   ' Only Numbers
str3 = "!@#$;*"  ' Only Special Characters
Str4 = "Asc23@#"  ' Has all the above
```

### 字符串函数

预定义的VBA字符串函数可以帮助开发人员非常有效地处理字符串。以下是VBA中支持的字符串的方法。请点击每个方法来详细了解。

| 编号 | 函数                                                         | 描述                                           |
| ---- | ------------------------------------------------------------ | ---------------------------------------------- |
| 1    | [InStr](http://www.yiibai.com/vba/vba_instr_function.html)   | 返回指定子字符串的第一个匹配项。从左到右搜索。 |
| 2    | [InstrRev](http://www.yiibai.com/vba/vba_instrrev_function.html) | 返回指定子字符串的第一个匹配项。从右到左搜索。 |
| 3    | [Lcase](http://www.yiibai.com/vba/vba_lcase_function.html)   | 返回指定字符串的小写字母。                     |
| 4    | [Ucase](http://www.yiibai.com/vba/vba_ucase_function.html)   | 返回指定字符串转为大写字母的形式。             |
| 5    | [Left](http://www.yiibai.com/vba/vba_left_function.html)     | 返回在左侧指定数量字符的字符串。               |
| 6    | [Right](http://www.yiibai.com/vba/vba_right_function.html)   | 返回在右侧指定数量字符的字符串                 |
| 7    | [Mid](http://www.yiibai.com/vba/vba_mid_function.html)       | 根据指定的参数从字符串中返回特定数量的字符。   |
| 8    | [Ltrim](http://www.yiibai.com/vba/vba_ltrim_function.html)   | 删除指定字符串左侧的空格后返回一个字符串。     |
| 9    | [Rtrim](http://www.yiibai.com/vba/vba_rtrim_function.html)   | 删除指定字符串右侧的空格后返回一个字符串。     |
| 10   | [Trim](http://www.yiibai.com/vba/vba_trim_function.html)     | 删除开头和结尾空格后返回一个字符串值。         |
| 11   | [Len](http://www.yiibai.com/vba/vba_len_function.html)       | 返回给定字符串的长度。                         |
| 12   | [Replace](http://www.yiibai.com/vba/vba_replace_function.html) | 用另一个字符串替换字符串后返回字符串。         |
| 13   | [Space](http://www.yiibai.com/vba/vba_space_function.html)   | 用指定数量的空格填充字符串。                   |
| 14   | [StrComp](http://www.yiibai.com/vba/vba_strcomp_function.html) | 比较两个指定的字符串后返回一个整数值。         |
| 15   | [String](http://www.yiibai.com/vba/vba_string_function.html) | 返回指定次数的字符的字符串。                   |
| 16   | [StrReverse](http://www.yiibai.com/vba/vba_strreverse_function.html) | 反转给定字符串的字符序列后，返回一个字符串。   |

## VBA日期时间函数

VBScript日期和时间函数帮助开发人员将日期和时间从一种格式转换为另一种格式，或以适合特定条件的格式表示日期或时间值。

### 日期函数

| 编号 | 函数                                                         | 描述                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | [Date](http://www.yiibai.com/vba/vba_date_function.html)     | 一个函数，它返回当前的系统日期。                             |
| 2    | [CDate](http://www.yiibai.com/vba/vba_cdate_function.html)   | 一个函数，将给定的输入转换为日期。                           |
| 3    | [DateAdd](http://www.yiibai.com/vba/vba_dateadd_function.html) | 一个函数，它返回一个指定的时间间隔被添加的日期。             |
| 4    | [DateDiff](http://www.yiibai.com/vba/vba_datediff_function.html) | 一个函数，它返回两个时间段之间的差异。                       |
| 5    | [DatePart](http://www.yiibai.com/vba/vba_datepart_function.html) | 一个函数，它返回给定输入日期值的指定部分。                   |
| 6    | [DateSerial](http://www.yiibai.com/vba/vba_dateserial_function.html) | 函数，返回给定年份，月份和日期的有效日期。                   |
| 7    | [FormatDateTime](http://www.yiibai.com/vba/vba_formatdatetime_function.html) | 一个函数，根据提供的参数格式化日期。                         |
| 8    | [IsDate](http://www.yiibai.com/vba/vba_isdate_function.html) | 无论提供的参数是否为日期，都返回一个布尔值的函数。           |
| 9    | [Day](http://www.yiibai.com/vba/vba_day_function.html)       | 一个函数，它返回一个`1`到`31`之间的整数，表示指定日期的某一天。 |
| 10   | [Month](http://www.yiibai.com/vba/vba_month_function.html)   | 一个函数，它返回一个介于`1`和`12`之间的整数，表示指定日期的月份。 |
| 11   | [Year](http://www.yiibai.com/vba/vba_year_function.html)     | 一个函数，它返回一个表示指定日期的年份的整数。               |
| 12   | [MonthName](http://www.yiibai.com/vba/vba_monthname_function.html) | 一个函数，返回指定日期的特定月份的名称。                     |
| 13   | [WeekDay](http://www.yiibai.com/vba/vba_weekday_function.html) | 一个函数，返回一个整数(`1`到`7`)，表示指定日期的星期几。     |
| 14   | [WeekDayName](http://www.yiibai.com/vba/vba_weekdayname_function.html) | 一个函数，返回指定日期的星期几名称。                         |

### 时间函数

| 编号 | 函数                                                         | 描述                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | [Now](http://www.yiibai.com/vba/vba_now_function.html)       | 一个函数，它返回当前系统的日期和时间。                       |
| 2    | [Hour](http://www.yiibai.com/vba/vba_hour_function.html)     | 一个函数，它返回一个介于`0`到`23`之间的整数，表示给定时间的小时部分。 |
| 3    | [Minute](http://www.yiibai.com/vba/vba_minute_function.html) | 一个函数，它返回`0`到`59`之间的整数，表示给定时间的分钟部分。 |
| 4    | [Second](http://www.yiibai.com/vba/vba_second_function.html) | 一个函数，返回`0`到`59`之间的一个整数，表示给定时间的秒数部分。 |
| 5    | [Time](http://www.yiibai.com/vba/vba_time_function.html)     | 一个函数，它返回当前的系统时间。                             |
| 6    | [Timer](http://www.yiibai.com/vba/vba_timer_function.html)   | 一个函数，返回自上午`12:00`以来的秒数和毫秒数。              |
| 7    | [TimeSerial](http://www.yiibai.com/vba/vba_timeserial_function.html) | 一个函数，它返回小时，分钟和秒的特定输入的时间。             |
| 8    | [TimeValue](http://www.yiibai.com/vba/vba_timevalue_function.html) | 将输入字符串转换为时间格式的函数。                           |

## VBA数组

我们都知道，一个变量是一个存储值的容器。 有时，开发人员希望一次可以在一个变量中保存多个值。 当一系列值存储在单个变量中时，则称为数组变量。

### 数组声明

数组声明的方式与声明变量相同，只是数组变量的声明使用括号。 在下面的例子中，括号里提到了数组的大小。参考以下示例 - 

```vb
'Method 1 : Using Dim
Dim arr1()    'Without Size

'Method 2 : Mentioning the Size
Dim arr2(5)  'Declared with size of 5

'Method 3 : using 'Array' Parameter
Dim arr3
arr3 = Array("apple","Orange","Grapes")
```

在上面代码中，

- 虽然数组大小被指定为`5`，但是当数组索引从零开始时，它可以保持`6`个值。
- 数组索引不能是负数。
- VBScript数组可以在数组中存储任何类型的变量。因此，一个数组可以在一个数组变量中存储一个整数，字符串或字符。

### 赋值给数组

通过为每个要分配的值指定一个数组索引值，将这些值分配给数组。它可以是一个字符串。

#### **例子**

添加一个模块并添加以下代码 - 

```vb
Private Sub Constant_demo_Click()
   Dim arr(5)
   arr(0) = "1"           'Number as String
   arr(1) = "VBScript"    'String
   arr(2) = 100            'Number
   arr(3) = 2.45            'Decimal Number
   arr(4) = #10/07/2013#  'Date
   arr(5) = #12.45 PM#    'Time

   msgbox("Value stored in Array index 0 : " & arr(0))
   msgbox("Value stored in Array index 1 : " & arr(1))
   msgbox("Value stored in Array index 2 : " & arr(2))
   msgbox("Value stored in Array index 3 : " & arr(3))
   msgbox("Value stored in Array index 4 : " & arr(4))
   msgbox("Value stored in Array index 5 : " & arr(5))
End Sub
Vb
```

当执行上面的函数时，它会产生下面的输出。

```shell
Value stored in Array index 0 : 1
Value stored in Array index 1 : VBScript
Value stored in Array index 2 : 100
Value stored in Array index 3 : 2.45
Value stored in Array index 4 : 7/10/2013
Value stored in Array index 5 : 12:45:00 PM
```

### 多维数组

数组不仅限于一个维度，但它们最多可以有`60`个维度。 二维数组是最常用的数组。

#### 例子

在下面的例子中，一个多维数组被声明为`3`行`4`列。

```vb
Private Sub Constant_demo_Click()
   Dim arr(2,3) as Variant    ' Which has 3 rows and 4 columns
   arr(0,0) = "Apple" 
   arr(0,1) = "Orange"
   arr(0,2) = "Grapes"           
   arr(0,3) = "pineapple" 
   arr(1,0) = "cucumber"           
   arr(1,1) = "beans"           
   arr(1,2) = "carrot"           
   arr(1,3) = "tomato"           
   arr(2,0) = "potato"             
   arr(2,1) = "sandwitch"            
   arr(2,2) = "coffee"             
   arr(2,3) = "nuts"            

   msgbox("Value in Array index 0,1 : " &  arr(0,1))
   msgbox("Value in Array index 2,2 : " &  arr(2,2))
End Sub
```

当执行上面的函数时，它会产生下面的输出。

```shell
Value stored in Array index : 0 , 1 : Orange
Value stored in Array index : 2 , 2 : coffee
```

### ReDim语句

`ReDim`语句用于声明动态数组变量并分配或重新分配存储空间。

```vb
ReDim [Preserve] varname(subscripts) [, varname(subscripts)]
```

#### **参数说明**

- *Preserve* - 一个可选参数，用于在更改最后一个维度的大小时保留现有数组中的数据。
- *Varname* - 必需的参数，表示变量的名称，应遵循标准变量命名约定。
- *Subscripts* - 必需的参数，表示数组的大小。

#### 例子

在下面的例子中，数组已经被重新定义，当数组的现有大小发生改变时，这些值被保存下来。

> 注意 - 调整数组的大小时，删除的元素中的数据将丢失。

```vb
Private Sub Constant_demo_Click()
   Dim a() as variant
   i = 0
   redim a(5)
   a(0) = "XYZ"
   a(1) = 41.25
   a(2) = 22

   REDIM PRESERVE a(7)
   For i = 3 to 7
   a(i) = i
   Next

   'to Fetch the output
   For i = 0 to ubound(a)
      Msgbox a(i)
   Next
End Sub
```

当执行上面的函数时，它会产生下面的输出。

```vb
XYZ
41.25
22
3
4
5
6
7
```

### 数组方法

VBScript中有各种内置函数，可以帮助开发人员有效地处理数组。 下面列出了与数组一起使用的所有方法。请点击方法名称来详细了解它们如何应用。

| 编号 | 方法                                                         | 描述                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | [LBound](http://www.yiibai.com/vba/vba_lbound_function.html) | 它返回一个整数，对应于给定数组的最小下标。                   |
| 2    | [UBound](http://www.yiibai.com/vba/vba_ubound_function.html) | 它返回一个整数，对应于给定数组的最大下标。                   |
| 3    | [Split](http://www.yiibai.com/vba/vba_split_function.html)   | 它返回一个包含指定数量值的数组。根据分隔符分割。             |
| 4    | [Join](http://www.yiibai.com/vba/vba_join_function.html)     | 它返回一个包含数组中指定数量的子串的字符串。这是`Split`方法的一个完全相反的功能。 |
| 5    | [Filter](http://www.yiibai.com/vba/vba_filter_function.html) | 它返回一个基于零的数组，该数组包含基于特定过滤条件的字符串数组的子集。 |
| 6    | [IsArray](http://www.yiibai.com/vba/vba_isarray_function.html) | 它返回一个布尔值，表示输入变量是否是一个数组。               |
| 7    | [Erase](http://www.yiibai.com/vba/vba_erase_function.html)   | 为数组变量恢复分配的内存。                                   |

## VBA用户自定义函数

函数是一组可重复使用的代码，可以在程序中的任何地方调用。这消除了一遍又一遍地编写相同的代码的需要。这使程序员能够将一个大程序划分成许多小的可管理的功能模块。

除了内置函数外，VBA还允许编写用户定义的函数。 在本章中，我们将学习如何在VBA中编写自己的函数。

### 函数定义

一个VBA函数可以有一个可选的`return`语句。如果要从函数返回值，则可使用`return`语句。
例如，可以在一个函数中传递两个数字，然后从函数中返回它们的乘积。

> 注 - 函数可以返回由逗号分隔的多个值，作为分配给函数名称本身的数组。

在使用函数之前，我们需要定义这个特定的函数。 在VBA中定义函数的最常见的方法是使用`Function`关键字，后跟一个唯一的函数名称，它可能会也可能不会带有一个带有`End Function`关键字的参数列表和一个语句，这表示函数的结束。以下是定义函数的基本语法。

### **基本语法**

```vb
Function Functionname(parameter-list)
   statement 1
   statement 2
   statement 3
   .......
   statement n
End Function
Vb
```

### 例子

添加以下函数计算返回面积。请注意，可以使用函数名称本身返回一个值/值。

```vb
Function findArea(Length As Double, Optional Width As Variant)
   If IsMissing(Width) Then
      findArea = Length * Length
   Else
      findArea = Length * Width
   End If
End Function
Vb
```

### 调用函数

要调用函数，请使用函数名称调用函数，如以下屏幕截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2411/985111105_96991.png)

计算面积的结果输出如下所示将显示给用户。

![img](http://www.yiibai.com/uploads/images/201711/2411/744111105_39039.png)

## VBA子程序

子程序(*Sub Procedures*，也叫子过程)与函数类似，但有一些差异。

- 子过程不需要有返回一个值，而函数可能会或可能不会有返回一个值。
- 子程序可以不用`call`关键字来调用。
- 子程序总是包含在`Sub`和`End Sub`语句中。

### **示例**

```vb
Sub Area(x As Double, y As Double)
   MsgBox x * y
End Sub
Vb
```

### 调用程序

要在脚本的某处调用过程，可以使用函数进行调用。无法使用与函数相同的方式来调用子过程，因为子过程不会返回值。

```vb
Function findArea(Length As Double, Width As Variant)
   area Length, Width    ' To Calculate Area 'area' sub proc is called
End Function
Vb
```

现在只能调用该函数，而不能调用子程序，如下图所示。
![img](http://www.yiibai.com/uploads/images/201711/2411/491111142_55828.png)

该区域的面积仅在消息框中计算和显示。

![img](http://www.yiibai.com/uploads/images/201711/2411/814111143_24497.png)

结果单元显示为零，因为计算的面积值不是从函数返回的。简而言之，不能直接在Excel工作表中调用子程序。

## VBA消息框（MsgBox）

`MsgBox`函数显示一个消息框，并等待用户点击一个按钮，然后根据用户点击的按钮执行相关的操作。

### 语法

```vb
MsgBox(prompt[,buttons][,title][,helpfile,context])
Vb
```

### **参数说明**

- *prompt* - 必需的参数。在对话框中显示为消息的字符串。提示的最大长度大约为`1024`个字符。 如果消息扩展为多行，则可以使用每行之间的回车符(`Chr(13)`)或换行符(`Chr(10)`)来分隔行。
- *buttons* - 可选参数。一个数字表达式，指定要显示的按钮的类型，要使用的图标样式，默认按钮的标识以及消息框的形式。如果留空，则按钮的默认值为`0`。
- *title* - 可选参数。 显示在对话框的标题栏中的字符串表达式。 如果标题留空，应用程序名称将被放置在标题栏中。
- *helpfile* - 可选参数。一个字符串表达式，标识用于为对话框提供上下文相关帮助的帮助文件。
- *Context* - 可选参数。一个数字表达式，用于标识由帮助作者分配给相应帮助主题的帮助上下文编号。 如果提供上下文，则还必须提供`helpfile`。

*Buttons* 参数可以使用以下任何值 -

- *0 vbOKOnly* - 仅显示*“确定”* 按钮。
- *1 vbOKCancel* - 显示*“确定”* 和*“取消”* 按钮。
- *2 vbAbortRetryIgnore* - 显示*“中止”*，*“重试”*和*“忽略”* 按钮。
- *3 vbYesNoCancel* - 显示*“是”*，*“否”*和*“取消”* 按钮。
- *4 vbYesNo* - 显示*“是”*和*“否”*按钮。
- *5 vbRetryCancel* - 显示*“重试”*和*“取消”*按钮。
- *16 vbCritical* - 显示严重消息图标。
- *32 vbQuestion* - 显示警告查询图标。
- *48 vbExclamation* - 显示警告消息图标。
- *64 vbInformation* - 显示信息消息图标。
- *0 vbDefaultButton1* - 第一个按钮是默认的。
- *256 vbDefaultButton2* - 第二个按钮是默认的。
- *512 vbDefaultButton3* - 第三个按钮是默认的。
- *768 vbDefaultButton4* - 第四个按钮是默认的。
- *0 vbApplicationModal* 应用程序模式 - 当前的应用程序将不会工作，直到用户响应消息框。
- *4096 vbSystemModal* 系统模式 - 所有的应用程序将不会工作，直到用户响应消息框。

上述值在逻辑上分为四组：第一组(`0`至`5`)指示要在消息框中显示的按钮。第二组(`16`,`32`,`48`,`64`)描述要显示的图标的样式，第三组(`0`,`256`,`512`,`768`)指示哪个按钮必须是默认的，第四组(`0`,`4096` )确定消息框的形式。

### 返回值

`MsgBox`函数可以返回以下值之一，可用于标识用户在消息框中单击的按钮。

- *vbOK* - *确定* 按钮被点击。
- *vbCancel* - *取消* 按钮被点击。
- *vbAbort* - *中止* 按钮被点击。
- *vbIgnore* - *忽略* 按钮被点击。
- *vbYes* - *是* 按钮被点击。
- *vbNo* - *否* 按钮被点击。

### 示例

```vb
Function MessageBoxDemo() 
   'Message Box with just prompt message '
   MsgBox("欢迎您~")     

   'Message Box with title, yes no and cancel Butttons  '
   result = MsgBox("你喜欢蓝色吗?", 3, "选择一个选项") 

   ' Assume that you press No Button  '
   MsgBox ("返回 result 的值是：" &result) 
End Function
Vb
```

**输出结果**

**第1步** - 上述功能函数可以通过单击VBA窗口上的“运行”按钮或通过从Excel工作表调用函数来执行，如以下屏幕截图所示 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/764091128_65645.png)

运行子程序 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/371091131_41328.png)

**第2步** - 显示一个简单的消息框，并显示消息“欢迎”和“确定”按钮

![img](http://www.yiibai.com/uploads/images/201711/2111/145091132_69468.png)

**第3步** - 点击*确定*后，另一个对话框会显示一个消息，同时显示*“是，否和取消”*按钮。

![img](http://www.yiibai.com/uploads/images/201711/2111/943091133_10755.png)

**第4步**  - 点击*“否”*按钮后，该按钮(`7`)的值将被存储为一个整数，并显示为一个消息框给用户，如以下屏幕截图所示。使用这个值，可以理解用户点击了哪个按钮。

![img](http://www.yiibai.com/uploads/images/201711/2111/476091134_96541.png)

## VBA输入框（InputBox）

`InputBox`函数提示用户输入值。当输入值后，如果用户单击*确定* 按钮或按下键盘上的*ENTER* 键，`InputBox`函数将返回文本框中的文本。如果用户单击*“取消”* 按钮，该函数将返回一个空字符串(`""`)。

### 语法

```vb
InputBox(prompt[,title][,default][,xpos][,ypos][,helpfile,context])
Vb
```

### 参数说明

- *Prompt* - 必需的参数。 在对话框中显示为消息的字符串。提示的最大长度大约为`1024`个字符。 如果消息扩展为多行，则可以使用每行之间的回车符(`Chr(13)`)或换行符(`Chr(10)`)来分隔行。
- *title* - 一个可选参数。显示在对话框的标题栏中的字符串表达式。如果标题留空，应用程序名称将被放置在标题栏中。
- *default* - 一个可选参数。用户希望显示的文本框中的默认文本。
- *xpos* - 一个可选参数。`X`轴的位置表示水平从屏幕左侧的提示距离。 如果留空，则输入框水平居中。
- *ypos* - 一个可选参数。`Y`轴的位置表示竖直方向从屏幕左侧的提示距离。如果留空，则输入框垂直居中。
- *helpfile* - 一个可选参数。一个字符串表达式，标识用于为对话框提供上下文相关帮助的帮助文件。 
- *context* - 一个可选参数。一个数字表达式，用于标识由帮助作者分配给相应帮助主题的帮助上下文编号。如果提供上下文，则还必须提供`helpfile`。

### 示例

在这个示例中，通过在两个输入框(一个用于长度，一个用于宽度)的帮助下在运行时从用户获取值来计算矩形的面积。实现代码如下 - 

```vb
Function CountArea()
   Dim Length As Double
   Dim Width As Double

   Length = InputBox("输入一个长度值： ", "输入长度")
   Width = InputBox("输入一个宽度值：", "输入宽度")
   findArea = Length * Width
   CountArea = findArea
End Function
Vb
```

实现过程 - 

**第1步** - 执行相同的操作，使用函数名称进行调用，然后按`Enter`键，如下图所示。

![img](http://www.yiibai.com/uploads/images/201711/2111/148101137_96112.png)

**第2步** - 执行时(点击单元格，然后移出时即触发执行)，显示第一个输入框(长度)，在输入框中输入一个值。

![img](http://www.yiibai.com/uploads/images/201711/2111/479101132_45354.png)

弹出一个输入框，并输入长度值 - 

![img](http://www.yiibai.com/uploads/images/201711/2111/672101139_66176.png)

**第3步** - 输入第一个值后，显示第二个输入框(宽度)。

![img](http://www.yiibai.com/uploads/images/201711/2111/916101140_66830.png)

**第4步** - 输入第二个数字后，单击*确定* 按钮。该区域显示计算得到结果如下面的截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2111/724101143_23231.png)				

## VBA事件

在VBA中，要手动更改单元格或单元格值范围时，可以触发事件驱动的编程。 更改事件可能会使事情变得更容易，但您可以非常快速地结束一个完整的格式化页面。VBA中有两种事件 - 

- 工作表事件
- 工作簿事件

### 工作表事件

工作表事件在工作表中发生更改时被触发。 它是通过右键单击工作表选项卡并选择*“查看代码”*，然后粘贴代码来创建的。

![img](http://www.yiibai.com/uploads/images/201711/2411/685121107_12999.png)

用户可以选择这些工作表中的每一个，并从下拉列表中选择*“工作表”*以获取所有支持的工作表事件的列表。

![img](http://www.yiibai.com/uploads/images/201711/2411/184121107_56220.png)

以下是可以由用户添加的支持的工作表事件。

```vb
Private Sub Worksheet_Activate() 
Private Sub Worksheet_BeforeDoubleClick(ByVal Target As Range, Cancel As Boolean)    
Private Sub Worksheet_BeforeRightClick(ByVal Target As Range, Cancel As Boolean) 
Private Sub Worksheet_Calculate() 
Private Sub Worksheet_Change(ByVal Target As Range) 
Private Sub Worksheet_Deactivate() 
Private Sub Worksheet_FollowHyperlink(ByVal Target As Hyperlink) 
Private Sub Worksheet_SelectionChange(ByVal Target As Range)
Vb
```

#### 例子

在这个示例中，只需要双击之前显示一条消息。

```vb
Private Sub Worksheet_BeforeDoubleClick(ByVal Target As Range, Cancel As Boolean)
   MsgBox ("这是一个双击事件触发提示")
End Sub
Vb
```

双击任何单元格后，消息框将显示给用户，如以下屏幕截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2411/624121117_78253.png)

### 工作簿事件

工作簿事件总是在工作簿发生更改时触发的。可以通过选择“ThisWorkbook”并从下拉列表中选择“workbook”来添加工作簿事件的代码，如下图所示。 

![img](http://www.yiibai.com/uploads/images/201711/2411/956121120_58061.png)

立即将`Workbook_open`子过程显示给用户，如以下屏幕截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2411/929121122_30705.png)

以下是可以由用户添加的受支持的工作簿事件。

```vb
Private Sub Workbook_AddinUninstall() 
Private Sub Workbook_BeforeClose(Cancel As Boolean) 
Private Sub Workbook_BeforePrint(Cancel As Boolean) 
Private Sub Workbook_BeforeSave(ByVal SaveAsUI As Boolean, Cancel As Boolean) 
Private Sub Workbook_Deactivate() 
Private Sub Workbook_NewSheet(ByVal Sh As Object) 
Private Sub Workbook_Open() 
Private Sub Workbook_SheetActivate(ByVal Sh As Object) 
Private Sub Workbook_SheetBeforeDoubleClick(ByVal Sh As Object, ByVal Target As Range, Cancel As Boolean) 
Private Sub Workbook_SheetBeforeRightClick(ByVal Sh As Object, ByVal Target As Range, Cancel As Boolean) 
Private Sub Workbook_SheetCalculate(ByVal Sh As Object) 
Private Sub Workbook_SheetChange(ByVal Sh As Object, ByVal Target As Range) 
Private Sub Workbook_SheetDeactivate(ByVal Sh As Object) 
Private Sub Workbook_SheetFollowHyperlink(ByVal Sh As Object, ByVal Target As Hyperlink) 
Private Sub Workbook_SheetSelectionChange(ByVal Sh As Object, ByVal Target As Range) 
Private Sub Workbook_WindowActivate(ByVal Wn As Window) 
Private Sub Workbook_WindowDeactivate(ByVal Wn As Window) 
Private Sub Workbook_WindowResize(ByVal Wn As Window)
Vb
```

#### 例子

只需要向用户显示一条消息，无论何时创建新的工作表，都会成功创建新的工作表。

```vb
Private Sub Workbook_NewSheet(ByVal Sh As Object)
   MsgBox "New Sheet Created Successfully"
End Sub
Vb
```

在创建一个新的excel工作表后，会向用户显示一条消息，如以下屏幕截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2411/278121127_36924.png)

## VBA错误处理

在(VBScript/VBA)编程中有三种类型的错误：

- 语法错误
- 运行时错误
- 逻辑错误

## 语法错误

语法错误(也称为解析错误)发生在VBScript的解释时间。 例如，下面一行导致语法错误，因为它缺少一个右括号。

```vb
Function ErrorHanlding_Demo()
   dim x,y
   x = "Yiibai Yiibai"
   y = Ucase(x
End Function
Vb
```

## 运行时错误

运行时错误(也称为异常)在执行期间发生，在解释之后。

例如，下面的行会导致运行时错误，因为这里的语法是正确的，但是在运行时它正在尝试调用`fnmultiply`，但这是一个不存在的函数。

```vb
Function ErrorHanlding_Demo1()
   Dim x,y
   x = 10
   y = 20
   z = fnadd(x,y)
   a = fnmultiply(x,y)
End Function

Function fnadd(x,y)
   fnadd = x + y
End Function
Vb
```

## 逻辑错误

逻辑错误可能是最难追查的错误类型。这些错误不是语法或运行时错误的结果。 相反，当您在驱动脚本的逻辑中犯了一个错误，并且没有得到预期的结果时，就会发生这种情况。

你可能无法捕捉到这些错误，因为这取决于业务需求，在程序中加入什么类型的逻辑。

例如，将一个数字除以零，或写入一个进入无限循环的脚本。

### Error对象

假设我们有一个运行时错误，那么通过显示错误信息来停止执行。作为开发人员，如果想捕获错误，那么使用`Error`对象。

**例子**

在下面的例子中，`Err.Number`给出错误号，`Err.Description`给出错误描述。

```vb
Err.Raise 6   ' Raise an overflow error.
MsgBox "Error # " & CStr(Err.Number) & " " & Err.Description
Err.Clear   ' Clear the error.
Vb
```

### 错误处理

VBA启用错误处理例程，也可以用来禁用错误处理例程。没有`On Error`语句，发生的任何运行时错误都是致命的：显示错误消息，并且执行突然停止。

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
Vb
```

| 编号 | 关键字        | 描述                                                         |
| ---- | ------------- | ------------------------------------------------------------ |
| 1    | *GoTo line*   | 启用在所需的行参数中指定的行开始的错误处理例程。指定的行必须与`On Error`语句在相同的过程中，否则将发生编译时错误。 |
| 2    | *GoTo 0*      | 禁用当前过程中启用的错误处理程序并将其重置为`Nothing`。      |
| 3    | *GoTo -1*     | 禁用当前过程中启用的异常并将其重置为`Nothing`。              |
| 4    | *Resume Next* | 指定发生运行时错误时，控制权转到发生错误的语句之后的语句，并从该点继续执行。 |

**例子**

```vb
Public Sub OnErrorDemo()
   On Error GoTo ErrorHandler   ' Enable error-handling routine.
   Dim x, y, z As Integer
   x = 50
   y = 0
   z = x / y   ' Divide by ZERO Error Raises

   ErrorHandler:    ' Error-handling routine.
   Select Case Err.Number   ' Evaluate error number.
      Case 10   ' Divide by zero error
         MsgBox ("You attempted to divide by zero!")
      Case Else
         MsgBox "UNKNOWN ERROR  - Error# " & Err.Number & " : " & Err.Description
   End Select
   Resume Next
End Sub
```

## VBA Excel对象

使用VBA进行编程时，用户将要处理的重要对象很少。下面是一些常见的对象 -

- 应用程序对象
- 工作簿对象
- 工作表对象
- 范围对象

### 应用程序对象

应用程序对象由以下部分组成 -

- 应用程序范围的设置和选项。
- 返回顶级对象的方法，比如`ActiveCell`，`ActiveSheet`等等。

**示例**

```vb
'Example 1 :
Set xlapp = CreateObject("Excel.Sheet") 
xlapp.Application.Workbooks.Open "C:\test.xls"

'Example 2 :
Application.Windows("test.xls").Activate

'Example 3:
Application.ActiveCell.Font.Bold = True
Vb
```

### 工作簿对象

`Workbook`对象是`Workbooks`集合的成员，并包含当前在*Microsoft Excel*中打开的所有`Workbook`对象。

**示例**

```vb
'Ex 1 : To close Workbooks
Workbooks.Close

'Ex 2 : To Add an Empty Work Book
Workbooks.Add

'Ex 3: To Open a Workbook
Workbooks.Open FileName:="Test.xls", ReadOnly:=True

'Ex : 4 - To Activate WorkBooks
Workbooks("Test.xls").Worksheets("Sheet1").Activate
Vb
```

### 工作表对象

工作表对象是工作表集合的成员，并包含工作簿中的所有工作表对象。

**示例**

```vb
'Ex 1 : To make it Invisible
Worksheets(1).Visible = False

'Ex 2 : To protect an WorkSheet
Worksheets("Sheet1").Protect password:=strPassword, scenarios:=True
Vb
```

### 范围对象

`Range`对象表示单元格，行，列或包含一个或多个连续单元格块的单元格的选择。

```vb
'Ex 1 : To Put a value in the cell A5
Worksheets("Sheet1").Range("A5").Value = "5235"

'Ex 2 : To put a value in range of Cells
Worksheets("Sheet1").Range("A1:A4").Value = 5
```

## VBA文本文件

还可以读取Excel文件，并使用VBA将单元格的内容写入文本文件。VBA允许用户使用两种方法处理文本文件 -

- 文件系统对象(`FSO`)
- 使用`Write`命令

### 文件系统对象(FSO)

顾名思义，`FSO`对象帮助开发人员使用驱动器，文件夹和文件。 在本节中，我们将讨论如何使用`FSO`。

| 编号 | 对象类型     | 描述                                                         |
| ---- | ------------ | ------------------------------------------------------------ |
| 1    | `Drive`      | `Drive`是一个对象。 包含收集有关连接到系统的驱动器的信息的方法和属性。 |
| 2    | `Drives`     | `Drives`是一个集合。 它提供了连接到系统的驱动器的物理或逻辑列表。 |
| 3    | `File`       | `File`是一个对象。 它包含允许开发人员创建，删除或移动文件的方法和属性。 |
| 4    | `Files`      | `Files`是一个集合。 它提供了一个文件夹中包含的所有文件的列表。 |
| 5    | `Folder`     | `Folder`是一个对象。 它提供了允许开发人员创建，删除或移动文件夹的方法和属性。 |
| 6    | `Folders`    | `Folders`是一个集合。 它提供了一个文件夹内所有文件夹的列表。 |
| 7    | `TextStream` | `TextStream`是一个对象。 它使开发人员能够读写文本文件。      |

#### Drive

`Drive` 是一个对象，它提供对特定磁盘驱动器或网络共享的属性的访问。 `Drive`对象支持以下属性 -

- `AvailableSpace`
- `DriveLetter`
- `DriveType`
- `FileSystem`
- `FreeSpace`
- `IsReady`
- `Path`
- `RootFolder`
- `SerialNumber`
- `ShareName`
- `TotalSize`
- `VolumeName`

#### 示例

**第1步** - 在使用`FSO`进行脚本编写之前，应该启用Microsoft脚本运行时。请导航到*工具*->*引用*，如以下屏幕截图所示。
![img](http://www.yiibai.com/uploads/images/201711/2611/148091102_64349.png)

**第2步** - 添加“Microsoft脚本运行时间”，然后单击确定。

![img](http://www.yiibai.com/uploads/images/201711/2611/666091102_67139.png)

**第3步** - 添加想要写入文本文件中的数据，这里添加一个命令按钮。

![img](http://www.yiibai.com/uploads/images/201711/2611/359091131_73629.png)

**第4步** - 现在运行脚本。

```vb
Sub CommandButton1_Click()
   Const ForReading = 1, ForWriting = 2, ForAppending = 3
   Dim FilePath As String
   Dim CellData As String
   Dim LastCol As Long
   Dim LastRow As Long
   LastCol = ActiveSheet.UsedRange.Columns.Count
   LastRow = ActiveSheet.UsedRange.Rows.Count

    ' Create a TextStream.
   Set fso = CreateObject("Scripting.FileSystemObject")
   Set stream = fso.OpenTextFile("F:\worksp\vba\Support.log", ForWriting, True)

   CellData = ""
   ' LastRow = 3
   LastCol = 3
   For i = 1 To LastRow
      For j = 1 To LastCol
         CellData = Trim(ActiveCell(i, j).Value)
         stream.WriteLine "The Value at location (" & i & "," & j & ")" & CellData
      Next j
   Next i

   stream.Close
   MsgBox ("Job Done")

End Sub
Vb
```

执行脚本时，请确保将光标放在工作表的第一个单元格中。 `Support.log`文件的创建方式如下面*“F:\worksp\vba”*的目录，如下的截图所示。

![img](http://www.yiibai.com/uploads/images/201711/2611/864091132_94644.png)

该文件的内容，如以下屏幕截图中所示 - 

```txt
The Value at location (1,1)姓名
The Value at location (1,2)性别
The Value at location (1,3)城市
The Value at location (2,1)张三
The Value at location (2,2)男
The Value at location (2,3)北京
The Value at location (3,1)李四
The Value at location (3,2)男
The Value at location (3,3)北京
The Value at location (4,1)王五
The Value at location (4,2)男
The Value at location (4,3)上海
The Value at location (5,1)李小丽
The Value at location (5,2)女
The Value at location (5,3)深圳
The Value at location (6,1)Linsa
The Value at location (6,2)女
The Value at location (6,3)深圳
Txt
```

### Write命令

与FSO不同，不需要添加任何引用，但是，我们将无法使用驱动器，文件和文件夹。也能够将流添加到文本文件。

**示例**

```vb
Sub CommandButton1_Click()
   Const ForReading = 1, ForWriting = 2, ForAppending = 3
   Dim FilePath As String
   Dim CellData As String
   Dim LastCol As Long
   Dim LastRow As Long

   LastCol = ActiveSheet.UsedRange.Columns.Count
   LastRow = ActiveSheet.UsedRange.Rows.Count

   FilePath = "F:\worksp\vba\write.txt"
   Open FilePath For Output As #2

   CellData = ""
   LastCol = 3
   For i = 1 To LastRow
      For j = 1 To LastCol
         CellData = "The Value at location (" & i & "," & j & ")" & Trim(ActiveCell(i, j).Value)
         Write #2, CellData
      Next j
   Next i

   Close #2
   MsgBox ("Job Done")

End Sub
Vb
```

执行该脚本时，将在*“F:\worksp\vba”*位置创建*“write.txt”*文件，如以下屏幕截图所示。
![img](http://www.yiibai.com/uploads/images/201711/2611/346091135_64935.png)

该文件的内容显示如以下屏幕截图 - 

![img](http://www.yiibai.com/uploads/images/201711/2611/293091136_47677.png)

## VBA编程图表

使用VBA，可以根据特定标准生成图表。下面通过一个例子来看看它如何实现。

**第1步** - 输入要生成图形的数据。
![img](http://www.yiibai.com/uploads/images/201711/2611/615101109_59001.jpg)

**第2步** - 创建3个按钮 - 一个生成条形图，另一个生成饼图，另一个生成柱形图。
![img](http://www.yiibai.com/uploads/images/201711/2611/321101109_36417.jpg)

**第3步** - 开发一个宏来生成这些类型的图表。

```vb
' Procedure to Generate Pie Chart
Private Sub fn_generate_pie_graph_Click()
   Dim cht As ChartObject
   For Each cht In Worksheets(1).ChartObjects
      cht.Chart.Type = xlPie
   Next cht
End Sub

' Procedure to Generate Bar Graph
Private Sub fn_Generate_Bar_Graph_Click()
   Dim cht As ChartObject
   For Each cht In Worksheets(1).ChartObjects
      cht.Chart.Type = xlBar
   Next cht
End Sub

' Procedure to Generate Column Graph
Private Sub fn_generate_column_graph_Click()
   Dim cht As ChartObject
   For Each cht In Worksheets(1).ChartObjects
      cht.Chart.Type = xlColumn
   Next cht
End Sub
```

**第4步** - 点击相应的按钮，图表被创建。 在下面的输出中，点击生成饼图按钮。

![img](http://www.yiibai.com/uploads/images/201711/2611/579101110_74776.jpg)

