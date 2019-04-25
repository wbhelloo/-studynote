---
title: 简明Python教程-输入与输出
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-19 10:02:27
keywords:
---

### 输入与输出

有些时候我们的程序会与用户产生交互。举个例子，我们希望获取用户的输入内容，并向用户打印出返回的结果。我们可以分别通过` input() `函数与` print` 函数来实现这一需求。

<!--more-->

对于输入，我们还可以使用` str `（`String`，字符串）类的各种方法。例如，你可以使用`rjust `方法来获得右对齐到指定宽度的字符串，你可以查看` help(str)` 来了解更多细节。

另一个常见的输入输出类型是处理文件。创建、读取与写入文件对于很多程序来说是必不可少的功能。

### 用户输入内容

#### 例子

（将以下程序保存为 `io_input.py`）

```python
def reverse(text):
    return text[::-1]

def is_palindrome(text):
    return text == reverse(text)

something = input("Enter text: ")
if is_palindrome(something):
    print("Yes, it is a palindrome")
else:
    print("No it is not a palindrome")
```

#### 输出：

```python
$ python3 io_input.py
Enter text: sir
No, it is not a palindrome

$ python3 io_input.py
Enter text: madam
Yes, it is a palindrome

$ python3 io_input.py
Enter text: racecar
Yes, it is a palindrome
```

#### ***它是如何工作的?***

> 我们使用切片功能翻转文本。我们已经知道可以通过使用` seq[a:b]` 来从位置 `a` 开始到位置 `b `结束来对序列进行切片 。我们同样可以提供第三个参数来确定切片的步长（`Step`）。默认的步长为 `1 `，它会返回一份连续的文本。如果给定一个负数步长，如` -1 `，将返回翻转过的文本。
>
> `input() `函数可以接受一个字符串作为参数，并将其展示给用户。之后将等待用户输入内容或敲击返回键。一旦用户输入了某些内容并敲下返回键，` input() `函数将返回用户输入的文本。

### 文件

可以通过创建一个属于 `file `类的对象并使用` read `、` readline` 、` write `方法来打开或使用文件，并对它们进行读取或写入。读取或写入文件的能力取决于你指定以何种方式打开文件。最后，当你完成了文件，你可以调用 `close` 方法来告诉 Python 我们已经完成了对该文件的使用。

#### 例子：

（保存为` io_using_file.py`）

```python
poem = '''\
Programming is fun
When the work is done
if you wanna make your work also fun:
use Python!
'''

# 打开文件以编辑（'w'riting）
f = open('poem.txt', 'w')
# 向文件中编写文本
f.write(poem)
# 关闭文件
f.close()

# 如果没有特别指定，
# 将假定启用默认的阅读（'r'ead）模式
f = open('poem.txt')
while True:
    line = f.readline()
    # 零长度指示 EOF
    if len(line) == 0:
        break
    # 每行（`line`）的末尾
    # 都已经有了换行符
    # 因为它是从一个文件中进行读取的
    print(line, end='')

# 关闭文件
f.close()
```

#### 输出：

```python
Programming is fun
When the work is done
if you wanna make your work also fun:
use Python!
```

#### ***他是如何工作的？***

> 首先，我们使用内置的 `open` 函数并指定文件名以及我们所希望使用的打开模式来打开一个文件。打开模式可以是**阅读模式**（` 'r' `），**写入模式**（` 'w' `）和**追加模式**（` 'a' `）。我们还可以选择是通过文本模式（` 't' `）还是二进制模式（` 'b' `）来读取、写入或追加文本。实际上还有其它更多的模式可用，` help(open)` 会给你有关它们的更多细节。在默认情况下， `open() `会将文件视作文本（`text`）文件，并以阅读（`read`）模式打开它。
>
> 字本例子中，我们首先采用写入模式打开文件并使用文件对象的 `write` 方法来写入文件，并在最后通过 close 关闭文件。
>
> 接下来，我们重新以阅读模式打开同一个文件。我们不需要特别指定打开模式，因为“阅读文本文件”是默认的。我们在循环中使用 `readline` 方法来读取文件的每一行。这一方法将会一串完整的行，其中在行末尾还包含了换行符。当一个空字符串返回时，它表示我们已经到达了文件末尾，并且通过 `break` 退出循环。
> 最后，我们通过` close `关闭了文件。
>
> 现在，你可以检查`poem.txt `文件的内容来确认程序确实对该文件进行了写入与读取操作。

### Pickle

Python 提供了一个叫作 `Pickle `的标准模块，通过它你可以将任何纯 Python 对象存储到一个文件中，并在稍后将其取回，这叫作持久地（`Persistently`）存储对象。

#### 例子：

（保存为` io_pickle.py`）

```python
import pickle

# 我们存储相关对象的文件的名称
shoplistfile = 'shoplist.data'
# 需要购买的物品清单
shoplist = ['apple', 'mango', 'carrot']

# 准备写入文件
f = open(shoplistfile, 'wb')
# 转储对象至文件
pickle.dump(shoplist, f)
f.close()

# 清除 shoplist 变量
del shoplist

# 重新打开存储文件
f = open(shoplistfile, 'rb')
# 从文件中载入对象
storedlist = pickle.load(f)
print(storedlist)
```

#### 输出：

```python
['apple', 'mango', 'carrot']
```

#### ***它是如何工作的?***

> 要想将一个对象存储到一个文件中，我们首先需要通过` open `以写入（`write`）二进制（`binary`）模式打开文件，然后调用 `pickle `模块的 `dump` 函数。这一过程被称作**封装**（`Pickling`）。
> 接着，我们通过 `pickle` 模块的` load` 函数接收返回的对象，这个过程被称作**拆封**（`Unpickling`）。

### Unicode

截止到现在，我们编写或使用字符串、读取或写入某一文件时，我们用到的只是简单的英语字符。

#### 注意：

> 如果你正在使用 Python 2，我们又希望能够读写其它非英语语言，我们需要使用`unicode` 类型，它全都以字母 `u` 开头，例如 `u"hello world" `。

```python
>>> "hello world"
'hello world'
>>> type("hello world")
<class 'str'>
>>> u"hello world"
'hello world'
>>> type(u"hello world")
<class 'str'>
```

当我们阅读或写入某一文件或当我们希望与互联网上的其它计算机通信时，我们需要将我们的` Unicode` 字符串转换至一个能够被发送和接收的格式，这个格式叫作`“UTF-8”`。我们可以在这一格式下进行读取与写入，只需使用一个简单的关键字参数到我们的标准 `open`函数中：

#### 例子：

```python
# encoding = utf-8
import io

f = io.open("abc.txt", "wt", encoding="utf-8")
f.write(u"Hello here is 312 lab")
f.close()

text = io.open("abc.txt", encoding="utf-8").read()
print(text)
```

输出：

```python
Hello here is 312 lab
```

***它是如何工作的?***

现在我们可以先忽略 `import` 语句，我们会在模块章节章节探讨有关它的更多细节。每当我们诸如上面那番使用 `Unicode` 字面量编写一款程序时，我们必须确保 Python 程序已经被告知我们使用的是 `UTF-8`，因此我们必须将` # encoding=utf-8` 这一注释放置在我们程序的顶端。

我们使用` io.open `并提供了“编码（`Encoding`）”与“解码（`Decoding`）”参数来告诉 Python我们正在使用`Unicode`。

### 总结：

我们已经讨论了有关输入和输出的多种类型，这些内容有关文件处理，有关 `pickle` 模块还有关于`Unicode`。
接下来，我们将探索一些异常的概念。
