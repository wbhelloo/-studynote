---
title: 简明Python教程-基础知识
categories: 简明Python教程
tags: Python简明教程学习笔记
abbrlink: 56d9e07f
date: 2018-07-02 17:37:06
keywords:
description:
---

### 注释

注释 是任何存在于 # 号右侧的文字，其主要用作写给程序读者看的笔记。

```python
print('hello world') #注意到 print 是一个函数
```

你应该在你的程序中尽可能多地使用有用的注释：

- 解释假设
- 说明重要的决定
- 解释重要的细节
- 说明你想要解决的问题
- 说明你想要在程序中克服的问题，等等。

**代码会告诉你怎么做，注释会告诉你为何如此。**

<!-- more -->

### 字面常量

一个字面常量（Literal Constants） 的例子是诸如 `5 `、 `1.23` 这样的数字，或者是如 这是一串文本 或 `This is a string` 这样的文本。

### 数字

数字主要分为两种类型——整数（Integers）与 浮点数（Floats）。

整数：`2`

浮点数：`3.23` 或`52.3E-4`

### 字符串

一串字符串（String）是 字符（Characters） 的 序列（Sequence）。基本上，字符串就是一串词汇。

### 单引号

你可以使用单引号来指定字符串，例如`将我这样框进来`或 `Quote me on this` 所有引号内的空间，诸如空格与制表符，都将按原样保留。

### 双引号

被双引号包括的字符串和被单引号括起的字符串其工作机制完全相同。例如` "你的名字是？" `或`"What's your name?" `。

### 三引号

你可以通过使用三个引号—— `"""` 或`'''`来指定多行字符串。你可以在三引号之间自由地使用单引号与双引号。来看看这个例子：

```python
'''这是一段多行字符串。这是它的第一行。
This is the second line.
"What's your name?," I asked.
He said "Bond, James Bond."
'''
```

### 字符串是不可变的

这意味着一旦你创造了一串字符串，你就不能再改变它。

### 格式化方法

有时候我们会想要从其他信息中构建字符串。这正是` format() `方法大有用武之地的地方。

将以下内容保存为文件 `str_format.py` ：

```python
# 格式化输出
age = 20
name = 'Swaroop'
print('{0} was {1} years old when he wrote this book'.format(name,age))
print('Why is {0} playing with that python?'.format(name))
```

输出：

```python
Swaroop was 20 years old when he wrote this book
Why is Swaroop playing with that python?
```

***它是如何工作的？***

> 一个字符串可以使用某些特定的格式（Specification），随后， format 方法将被调用，使用这一方法中与之相应的参数替换这些格式。
>
> 在这里要注意我们第一次应用这一方法的地方，此处 `{0}`对应的是变量 `name `，它是该格式化方法中的第一个参数。与之类似，第二个格式` {1} `对应的是变量` age` ，它是格式化方法中的第二个参数。请注意，Python 从 0 开始计数，这意味着索引中的第一位是` 0`，第二位是基础`1`，以此类推。
>

同时还应注意数字只是一个可选选项，所以你同样可以写成：

例如：

```python
age = 20
name = 'Swaroop'
print('{} was {} years old when he wrote this book'.format(name, age))
print('Why is {} playing with that python?'.format(name))
```

输出：

```python
Swaroop was 20 years old when he wrote this book
Why is Swaroop playing with that python?
```

Python 中` format `方法所做的事情便是将每个参数值替换至格式所在的位置。这之中可以有更详细的格式，

例如：

```python
#对于浮点数‘0.333’保留小数点（.）后三位
print('{0:.3f}'.format(1.0/3))
#使用下划线填充文本，并保持文字处于中间位置
#使用（^ ）定义'___hello___'字符串长度为11
print('{0:_^11}'.format('hello'))
#基于关键词输出'Swaroop wrote A Byte of Python'
print('{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python'))
```

输出：

```python
0.333
___hello___
Swaroop wrote A Byte of Python
```

**注意：**`print` 总是会以一个不可见的“新一行”字符（` \n` ）结尾，因此重复调用 `print `将会在相互独立的一行中分别打印。为防止打印过程中出现这一换行符，你可以通过 `end` 指定其应以空白结尾：

```python
#end 指定其应以空白结尾，避免print的默认换行
print('ab', end='')
print('cd', end='')
print('')
```

输出：

```
abcd
```

或者你通过 `end` 指定以空格结尾：

```python
#通过end指定以空格结尾
print('a',end=' ')
print('b',end=' ')
print('c')
```

输出：

```
a b c
```

### 转义序列（Escape Sequence）

如果你希望生成一串包含单引号（` ' `）的字符串，你应该如何指定这串字符串？

例如，你想要的字符串是` "What's your name?"`

你可以通过 `\ `来指定单引号：要注意它可是反斜杠。现在，你可以将字符串指定为` 'What\'s yourname?' `。

```python
#转义字符
# (What's your name?)输出
print('What\'s your name?')
```

输出：

```python
What's your name?
```

另一种指定这一特别的字符串的方式是这样的： "What's your name?" ，如这个例子般使用**双引号**。类似地， 你必须在使用双引号括起的字符串中对字符串内的双引号使用转义序列。同样，你必须使用转义序列 `\\ `来指定反斜杠本身。

```python
# ("What's your name?")输出
print("\"What\'s your name?\"")
```

输出：

```pytho
"What's your name?"
```

#### 双行字符串:`` \n``

如果你想指定一串**双行字符串**该怎么办？一种方式即使用如前所述的三引号字符串，或者你可以使用一个表示新一行的转义序列——` \n`来表示新一行的开始。下面是一个例子：

```python
#输出双行字符串
print('This is the first line!\nThis is the second line!')
```

输出：

```python
This is the first line!
This is the second line!
```

#### 制表符:`\t`

```python
#\t制表符
print("\t这是开始！")
```

输出：

```python
	这是开始！
```

#### **反斜杠:**`\`

在一个字符串中，一个放置在末尾的 **反斜杠** 表示字符串将在下一行继续，但不会添加新的一行。例子：

```python
#下一行继续
print("This is the first sentence.\
 This is the second sentence.")
```

输出：

```python
This is the first sentence. This is the second sentence.
```

#### 原始字符串

如果你需要指定一些未经过特殊处理的字符串，比如转义序列，那么你需要在字符串前增加 r 或 R 来指定一个 原始（Raw） 字符串。例子：

```python
#原始字符串
print(r"Newlines are indicated by \n")
```

输出：

```python
Newlines are indicated by \n
```

### 变量

变量的值是可以变化的，也就是说，你可以用变量来存储任何东西。变量只是你的计算机内存中用以存储信息的一部分。与文字常量不同，你需要通过一些方式来访问这些变量，因此，你需要为它们命名。

### 标识符命名

变量是标识符的一个例子。

标识符（Identifiers） 是为 某些东西 提供的给定名称。在你命名标识符时，你需要遵守以下规则：

- 第一个字符必须是字母表中的字母（大写 ASCII 字符或小写 ASCII 字符或 Unicode 字符）或下划线（` _ `）。
- 标识符的其它部分可以由字符（大写 ASCII 字符或小写 ASCII 字符或 Unicode 字符）、下划线（ `_ `）、数字（`0~9`）组成。
- 标识符名称区分大小写。例如， `myname` 和 `myName` 并不等同。要注意到前者是小写字母 `n` 而后者是大写字母 `N` 。
- 有效 的标识符名称可以是` i` 或 `name_2_3 `，无效 的标识符名称可能是`2things` ，` this is spaced out `，` my-name` 和` >a1b2_c3 `。

### 数据类型

变量可以将各种形式的值保存为不同的数据类型（Data Type）。基本的类型是我们已经讨论过的 **数字** 与 **字符串** 。在后面的章节中，我们会了解如何通过 **类（Classes）** 类创建我们自己的类型。

### 对象

需要记住的是，Python 将程序中的任何内容统称为 对象（Object）。这是一般意义上的说法。我们以“某某对象（object）”相称，而非“某某东西（something）”。

### 如何编写 Python 程序

从今以后，保存和运行 Python 程序的标准步骤如下：

对于 **PyCharm** 用户

1. 打开 PyCharm。
2. 以给定的文件名创建新文件。
3. 输入案例中给出的代码。
4. 右键并运行当前文件。

注意：

每当你需要提供 命令行参数（Command Line Arguments）时，点击 `Run -> EditConfigurations`并在 `Script parameters: `部分输入相应参数，并点击` OK `按钮：

#### 例子：使用变量与字面常量

```python
#使用变量与字面常量
i=5
print(i)
i=i+1
print(i)
s='''This is a multi-line string.
This is the second line.'''
print(s)
```

输出：

```python
5
6
This is a multi-line string.
This is the second line.
```

*它是如何工作的?*

> 首先，我们使用赋值运算符（` =` ）将字面常量数值 `5 `赋值给变量` i `，这一行被称之为声明语句（Statement）因为其工作正是声明一些在这一情况下应当完成的事情：我们将变量名` i `与值` 5 `相连接。然后，我们通过` print` 语句来打印变量` i `所声明的内容，这并不奇怪，只是将变量的值打印到屏幕上。
>
> 接着，我们将` 1` 加到` i `变量所存储的值中，并将得出的结果重新存储进这一变量。然后我们将这一变量打印出来，并期望得到的值应为` 6 `。
>
> 类似地，我们将字面文本赋值给变量` s `，并将其打印出来。

### 逻辑行与物理行

所谓 **物理行（Physical Line）**是你在编写程序时 你所看到 的内容。所谓 **逻辑行（LogicalLine）**是 Python 所看到 的单个语句。Python 会假定每一 物理行 会对应一个 逻辑行。

```python
i = 5
print(i)
```

实际上等同于

```python
i = 5;
print(i);
```

同样可以看作

```python
i = 5; print(i);
```

也与这一写法相同

```python
i = 5; print(i)
```

Python 鼓励每一行使用一句独立语句从而使得代码更加可读，这个观点就是说你不应该使用分号。

### 显式行连接（Explicit Line Joining）

如果你有一行非常长的代码，你可以通过使用反斜杠将其拆分成多个物理行，这被称作显式行连接（Explicit Line Joining）。

```python
#显示行连接
s = 'This is a string.\
 This continues the string.'
print(s)
```

输出：

```
This is a string. This continues the string.
```

类似地，

```python
i = \
5
```

等同于

```
i = 5
```

### 缩进

空白区在 Python 中十分重要，实际上，空白区在各行的开头非常重要，这被称作 缩进（Indentation）。在逻辑行的开头留下空白区（使用**空格**或**制表符**）用以确定各逻辑行的缩进级别，而后者又可用于确定语句的分组。

```python
# 下面将发生错误，注意行首有一个空格
 print('Value is', i)
print('I repeat, the value is', i)
```

当你运行这一程序时，你将得到如下错误：

```python
  File "E:/var.py", line 3
    print('Value is', i)
    ^
IndentationError: unexpected indent
#缩进错误    
```

*如何缩进？*

> 使用四个空格来缩进。这是来自 Python 语言官方的建议。好的编辑器会自动为你完成这一工作。请确保你在缩进中使用数量一致的空格，否则你的程序将不会运行，或引发不期望的行为。

### 总结

我们已经了解了诸多本质性的细节，接下来我们可以去了解控制流语句等更多更加有趣的东西，记得一定要充分理解在本章所学到的内容。