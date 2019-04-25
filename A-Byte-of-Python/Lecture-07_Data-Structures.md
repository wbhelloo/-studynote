---
title: 简明Python教程-数据结构
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-17 14:16:33
keywords:
---

### 数据结构

数据结构（Data Structures）是用来存储一系列相关数据的**集合**。
Python 中有四种内置的数据结构——**列表（List）**、**元组（Tuple）**、**字典（Dictionary）**和**集合（Set）**。

<!--more-->

### 列表

列表 是一种用于保存一系列有序项目的集合，也就是说，你可以利用列表保存一串项目的序列。
项目的列表用方括号括起来，这样 Python 才能理解到你正在指定一张列表。一旦你创建了一张列表，你可以添加、移除或搜索列表中的项目。列表是一种可变的（Mutable）数据类型，即，这种类型是可以被改变的。

### 有关对象与类的快速介绍

**列表**是使用**对象**与**类**的实例。当我们启用一个变量 `i `并将整数` 5` 赋值给它时，你可以认为这是在创建一个` int `类（即类型）之下的对象（即实例）` i`。

一个类也可以带有方法（Method），该方法仅对这个类定义。只有当你拥有一个属于该类的对象时，你才能使用这些功能。举个例子，Python 为` list` 类提供了一种` append` 方法，能够允许你向列表末尾添加一个项目。例如 `mylist.append('an item')`将会向列表` mylist` 添加一串字符串。在这里要注意到我们通过使用点号的方法来访问对象。

一个类同样也可以具有字段（Field），它是只为该类定义且只为该类所用的变量。只有当你拥有一个属于该类的对象时，你才能够使用这些变量或名称。字段同样可以通过点号来访问，例如` mylist.field` 。

#### 例子：

（保存为 `ds_using_list.py`）

```python
# 这是我的购物清单
shoplist = ['apple', 'mango', 'carrot', 'banana']

print('I have', len(shoplist), 'items to purchase.')

print('These items are:', end=' ')
for item in shoplist:
    print(item, end=' ')

print('\nI also have to buy rice.')
shoplist.append('rice')
print('My shopping list is now', shoplist)

print('I will sort my list now')
shoplist.sort()
print('Sorted shopping list is', shoplist)

print('The first item I will buy is', shoplist[0])
olditem = shoplist[0]
del shoplist[0]
print('I bought the', olditem)
print('My shopping list is now', shoplist)
```

#### 输出：

```python
I have 4 items to purchase.
These items are: apple mango carrot banana 
I also have to buy rice.
My shopping list is now ['apple', 'mango', 'carrot', 'banana', 'rice']
I will sort my list now
Sorted shopping list is ['apple', 'banana', 'carrot', 'mango', 'rice']
The first item I will buy is apple
I bought the apple
My shopping list is now ['banana', 'carrot', 'mango', 'rice']
```

***它是如何工作的***

> 变量` shoplist `是一张购物清单。在` shoplist` 中，我们只存储了一些字符串，它们是我们需要购买的物品的名称，但是你可以向列表中添加任何类型的对象，包括数字，甚至是其它列表。
> 我们还使用` for...in `循环来遍历列表中的每一个项目。学习到现在，你必须有一种**列表**也是一个**序列**的意识。有关**序列**的特性将会在稍后的章节予以讨论。
> 在这里要注意在调用` print `函数时我们使用` end `参数，这样就能通过一个空格来结束输出工作，而不是通常的换行。
>
> 接下来，我们通过列表对象中的 `append` 方法向列表中添加一个对象。然后，我们将列表简单地传递给 `print `函数，打印出列表内容，以检查项目是否被添加进列表之中。
> 接着，我们用列表的 `sort `方法对列表进行排序。这里要注意这一方法影响到的是列表本身，而不会返回一个修改过的列表——这与修改字符串的方式并不相同。这也说明了列表是可变的（Mutable）而字符串是不可变的（Immutable）。
> 接下来，`del `语句则会从列表中移除对应的项目。例如我们希望移除列表中的第一个商品，我们使用`del shoplist[0]` （要记住 Python 从 0 开始计数）。

### 元组

**元组（Tuple）**用于将多个对象保存到一起，你可以将它们近似地看作列表。元组的一大特征类似于字符串，它是不可变的，也就是说，你不能编辑或更改元组。

**元组**是通过特别指定项目来定义的，在指定项目时，你可以给它们加上括号，并在括号内部用逗号进行分隔。

**元组**通常用于保证某一语句或某一用户定义的函数可以安全地采用一组数值，意即元组内的数值不会改变。

#### 例子

（保存为` ds_using_tuple.py`）

```python
# 我会推荐你总是使用括号
# 来指明元组的开始与结束
# 尽管括号是一个可选选项。
# 明了胜过晦涩，显式优于隐式。
zoo = ('python', 'elephant', 'penguin')
print('Number of animals in the zoo is', len(zoo))

new_zoo = 'monkey', 'camel', zoo
print('Number of cages in the new zoo is', len(new_zoo))
print('All animals in new zoo are', new_zoo)
print('Animals brought from old zoo are', new_zoo[2])
print('Last animal brought from old zoo is', new_zoo[2][2])
print('Number of animals in the new zoo',
      len(new_zoo)-1+len(new_zoo[2]))
```

#### 输出：

```python
Number of animals in the zoo is 3
Number of cages in the new zoo is 3
All animals in new zoo are ('monkey', 'camel', ('python', 'elephant', 'penguin'))
Animals brought from old zoo are ('python', 'elephant', 'penguin')
Last animal brought from old zoo is penguin
Number of animals in the new zoo is 5
```

#### *他是如何工作的？*

> 变量` zoo` 指的是一个包含项目的元组。我们能够看到 `len `函数在此处用来获取元组的长度。这也表明元组同时也是一个序列。
> 如同列表的操作，我们可以通过在方括号中指定项目所处的位置来访问元组中的各个项目。这种使用方括号的形式被称作索引`（Indexing）`运算符。我们通过指定`new_zoo[2] `来指定 `new_zoo `中的第三个项目，我们也可以通过指定` new_zoo[2][2] `来指定`new_zoo `元组中的第三个项目中的第三个项目。

#### 注意：

> **包含 0 或 1 个项目的元组**
>
> 一个空的元组由一对圆括号构成，就像` myempty = () `这样。然而，一个只有一个项目的元组并不像这样简单。你必须在第一个（也是唯一一个）项目的后面加上一个逗号来指定它，如此一来 Python 才可以识别出在这个表达式想表达的是一个元组还是只是一个被括号所环绕的对象，即，如果你想指定一个包含项目 `2 `的元组，你必须指定 `singleton = (2, )` 。

### 字典

**字典**就像一本地址簿，如果你知道了他的姓名，你就可以在这里找到其地址或是更多的信息，换言之，我们将**键值**`（Keys）`（即姓名）与**值**`（Values）`（即地址等详细信息）联立到一起，在这里要注意到键值必须是唯一的。

另外要注意的是你只能使用不可变的对象（如字符串）作为字典的**键值**，但是你可以使用可变或不可变的对象作为字典中的**值**。

在字典中，你可以通过使用符号构成 `d = {key : value1 , key2 : value2} `这样的形式，来成对地指定**键值**与**值**。在这里要注意到成对的键值与值之间使用**冒号**分隔，而每一对键值与值则使用**逗号**进行区分，它们全都由一对**花括号**括起。

字典中的成对的**键值**--**值**配对不会以任何方式进行排序。如果你希望为它们安排一个特别的次序，只能在使用它们之前自行进行排序。

你将要使用的字典是属于 dict 类下的实例或对象。

#### 例子：

（保存为 `ds_using_dict.py`）

```python
# “ab”是地址（Address）簿（Book）的缩写
ab = {
'Swaroop': 'swaroop@swaroopch.com',
'Larry': 'larry@wall.org',
'Matsumoto': 'matz@ruby-lang.org',
'Spammer': 'spammer@hotmail.com'
}

print("Swaroop's address is", ab['Swaroop'])

# 删除一对键值—值配对
del ab['Spammer']

print('\nThere are {} contacts in the address-book\n'.format(len(ab)))

for name, address in ab.items():
	print('Contact {} at {}'.format(name, address))

# 添加一对键值—值配对
ab['Guido'] = 'guido@python.org'

if 'Guido' in ab:
	print("\nGuido's address is", ab['Guido'])
```

#### 输出：

```python
Swaroop's address is swaroop@swaroopch.com

There are 3 contacts in the address-book

Contact Swaroop at swaroop@swaroopch.com
Contact Larry at larry@wall.org
Contact Matsumoto at matz@ruby-lang.org

Guido's address is guido@python.org
```

***它是如何工作的?***

> 我们通过`del `语句——来删除某一键值--值配对。只需指定字典、包含需要删除的键值名称的索引算符，并将其传递给` del `语句即可，这一操作不需要你知道与该键值相对应的值。
>
> 接着，我们通过使用字典的` items` 方法来访问字典中的每一对键值—值配对信息，这一操作将返回一份包含元组的列表，每一元组中则包含了每一对相应的信息——键值以及其相应的值。我们检索这一配对，并通过` for...in` 循环将每一对配对的信息相应地分配给` name `与`address` 变量，并将结果打印在 `for `代码块中。
>
> 可以通过使用索引运算符访问一个键值并为其分配与之相应的值，就像我们在上面的例子中对` Guido `键值所做的那样。我们可以使用 `in `运算符来检查某对键值--值配对是否存在。
> 要想了解有关 `dict` 类的更多方法，请参阅` help(dict) `。

> **关键字参数与字典**
> 如果你曾在你的函数中使用过关键词参数，那么你就已经使用过字典了！你在定义函数的参数列表时，就指定了相关的键值—值配对。当你在你的函数中访问某一变量时，它其实就是在访问字典中的某个键值。（在编译器设计的术语中，这叫作**符号表**`（Symbol Table）`）

### 序列

**列表**、**元组**和**字符串**可以看作**序列（Sequence）**的某种表现形式，可是究竟什么是序列，它又有什么特别之处？

**序列**的主要功能是**资格测试（Membership Test）**（也就是` in` 与 `not in` 表达式）和**索引操作**（**Indexing Operations**），它们能够允许我们直接获取序列中的特定项目。

上面所提到的序列的三种形态——列表、元组与字符串，同样拥有一种**切片（Slicing）运算符**，它能够允许我们序列中的某段切片——也就是序列之中的一部分。

#### 例子：

（保存为 `ds_seq.py`）

```python
shoplist = ['apple', 'mango', 'carrot', 'banana']
name = 'swaroop'
# Indexing or 'Subscription' operation #
# 索引或“下标（Subscription）”操作符 #
print('Item 0 is', shoplist[0])
print('Item 1 is', shoplist[1])
print('Item 2 is', shoplist[2])
print('Item 3 is', shoplist[3])
print('Item -1 is', shoplist[-1])
print('Item -2 is', shoplist[-2])
print('Character 0 is', name[0])
# Slicing on a list #
print('Item 1 to 3 is', shoplist[1:3])
print('Item 2 to end is', shoplist[2:])
print('Item 1 to -1 is', shoplist[1:-1])
print('Item start to end is', shoplist[:])
# 从某一字符串中切片 #
print('characters 1 to 3 is', name[1:3])
print('characters 2 to end is', name[2:])
print('characters 1 to -1 is', name[1:-1])
print('characters start to end is', name[:])
```

#### 输出：

```python
Item 0 is apple
Item 1 is mango
Item 2 is carrot
Item 3 is banana
Item -1 is banana
Item -2 is carrot
Character 0 is s
Item 1 to 3 is ['mango', 'carrot']
Item 2 to end is ['carrot', 'banana']
Item 1 to -1 is ['mango', 'carrot']
Item start to end is ['apple', 'mango', 'carrot', 'banana']
characters 1 to 3 is wa
characters 2 to end is aroop
characters 1 to -1 is waroo
characters start to end is swaroop
```

***它是如何工作的？***

> 首先，我们已经了解了如何通过使用索引来获取序列中的各个项目。这也被称作**下标操作（Subscription Operation）**。如上所示，当你在方括号中为序列指定一个数字，Python 将获取序列中与该位置编号相对应的项目。要记得 Python 从 0 开始计数。因此 `shoplist[0]`将获得` shoplist `序列中的第一个项目，而 `shoplist[3] `将获得第四个项目。
>
> **索引操作**也可以使用**负数**，在这种情况下，位置计数将从队列的末尾开始。因此，` shoplist[-1] `指的是序列的最后一个项目， `shoplist[-2]` 将获取序列中倒数第二个项目。
>
> 你需要通过指定序列名称来进行序列操作，在指定时序列名称后面可以跟一对数字--这是可选的操作，这一对数字使用方括号括起，并使用冒号分隔。在这里需要注意，它与你至今为止使用的索引操作显得十分相像。但是你要记住数字是可选的，冒号却不是。在切片操作中，第一个数字（冒号前面的那位）指的是切片**开始**的位置，第二个数字（冒号后面的那位）指的是切片**结束**的位置。如果第一位数字没有指定，Python 将会从序列的**起始处**开始操作。如果第二个数字留空，Python 将会在序列的**末尾**结束操作。要注意的是切片操作会在开始处返回 start，并在 end 前面的位置结束工作。也就是说，序列切片将包括起始位置，但不包括结束位置。
>
> 因此， `shoplist[1:3] `返回的序列的一组切片将从位置 `1 `开始，包含位置` 2` 并在位置` 3` 时结束，因此，这块切片返回的是两个项目。类似地， `shoplist[:] `返回的是整个序列。你同样可以在切片操作中使用负数位置。使用负数时位置将从序列末端开始计算。例如，` shoplist[:-1]` 强返回一组序列切片，其中不包括序列的最后一项项目，其它所有项目都包含其中。
>
> 你同样可以在切片操作中提供第三个参数，这一参数将被视为切片的**步长（Step）**（在默认情况下，步长大小为 1）

```python
>>> shoplist = ['apple', 'mango', 'carrot', 'banana']
>>> shoplist[::1]
['apple', 'mango', 'carrot', 'banana']
>>> shoplist[::2]
['apple', 'carrot']
>>> shoplist[::3]
['apple', 'banana']
>>> shoplist[::-1]
['banana', 'carrot', 'mango', 'apple']
```

> 你会注意到当步长为 2 时，我们得到的是第 0、2、4…… 位项目。当步长为 3 时，我们得到的是第 0、3……位项目。
> 序列的一大优点在于你可以使用同样的方式访问元组、列表与字符串。

### 引用

当你创建了一个对象并将其分配给某个变量时，变量只会查阅（Refer）某个对象，并且它也不会代表对象本身。也就是说，变量名只是指向你计算机内存中存储了相应对象的那一部分。这称作将名称绑定（Binding）给那一个对象。

#### 例子：

（保存为 `ds_reference.py`）

```python
print('Simple Assignment')
shoplist = ['apple', 'mango', 'carrot', 'banana']
# mylist 只是指向同一对象的另一种名称
mylist = shoplist

# 我购买了第一项项目，所以我将其从列表中删除
del shoplist[0]

print('shoplist is', shoplist)
print('mylist is', mylist)
# 注意到 shoplist 和 mylist 二者都
# 打印出了其中都没有 apple 的同样的列表，以此我们确认
# 它们指向的是同一个对象

print('Copy by making a full slice')
# 通过生成一份完整的切片制作一份列表的副本
mylist = shoplist[:]
# 删除第一个项目
del mylist[0]

print('shoplist is', shoplist)
print('mylist is', mylist)
# 注意到现在两份列表已出现不同
```

#### 输出：

```python
Simple Assignment
shoplist is ['mango', 'carrot', 'banana']
mylist is ['mango', 'carrot', 'banana']
Copy by making a full slice
shoplist is ['mango', 'carrot', 'banana']
mylist is ['carrot', 'banana']
```

#### ***它是如何工作的?***

> 你要记住如果你希望创建一份诸如序列等复杂对象的副本（而非整数这种简单的对象（Object）），你必须使用切片操作来制作副本。如果你仅仅是将一个变量名赋予给另一个名称，那么它们都将“查阅”同一个对象，如果你对此不够小心，那么它将造成麻烦。

### 有关字符串的更多内容

在程序中使用的所有字符串都是` str` 类下的对象。下面的案例将演示这种类包含的一些有用的方法。要想获得这些方法的完成清单，你可以查阅 help(str) 。

#### 例子

```python
# 这是一个字符串对象
name = 'Swaroop'

if name.startswith('Swa'):
    print('Yes, the string starts with "Swa"')

if 'a' in name:
    print('Yes, it contains the string "a"')

if name.find('war') != -1:
    print('Yes, it contains the string "war"')

delimiter = '_*_'
mylist = ['Brazil', 'Russia', 'India', 'China']
print(delimiter.join(mylist))
```

#### 输出：

```python
Yes, the string starts with "Swa"
Yes, it contains the string "a"
Yes, it contains the string "war"
Brazil_*_Russia_*_India_*_China
```

***它是如何工作的?***

> `startswith` 方法用于查找字符串是否以给定的字符串内容开头。` in `运算符用以检查给定的字符串是否包含查询的字符串中的一部分。`find `方法用于定位字符串中给定的子字符串的位置。如果找不到相应的子字符串， `find`会返回` -1`。` str `类同样还拥有一个简洁的方法用以 **联结（Join）** 序列中的项目，其中字符串将会作为每一项目之间的分隔符，并以此生成并返回一串更大的字符串。

### 总结

我们已经详细探讨了 Python 中内置的多种不同的数据结构。这些数据结构对于编写大小适中的 Python 程序而言至关重要。
现在我们已经具备了诸多有关 Python 的基本知识，接下来我们将会了解如何设计并编写一款真实的 Python 程序。