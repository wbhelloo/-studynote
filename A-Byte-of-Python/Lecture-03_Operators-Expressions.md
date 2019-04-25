---
title: 简明Python教程-运算符与表达式
categories: 简明Python教程
tags: Python简明教程学习笔记
keywords:
  - Python
  - 运算符
  - 表达式
date: 2018-07-03 14:32:01
description:
---

### 运算符与表达式

你所编写的大多数语句（逻辑行）都包含了**表达式（Expressions）**。一个表达式的简单例子便是 `2+3 `。表达式可以拆分成**运算符（Operators）**与**操作数（Operands）**。

**运算符（Operators）**是进行某些操作，并且可以用诸如 `+ `等符号或特殊关键词加以表达的功能。运算符需要一些数据来进行操作，这些数据就被称作**操作数（Operands）**。

### 运算符

`+`（加）

- 两个对象相加。
- `3+5` 则输出`8` 。 `'a' + 'b' `则输出` 'ab' `。<!-- more -->

`-`（减）

- 从一个数中减去另一个数，如果第一个操作数不存在，则默认为**零**。

- `-5.2` 将输出一个**负数**，` 50 - 24` 输出 `26 `。

`*`（乘）

- 给出两个数的乘积，或返回字符串重复指定次数后的结果。
- 2 * 3 输出 6 。 'la' * 3 输出 'lalala' 。

`**` （乘方）

- 返回 x 的 y 次方。
- `3 ** 4` 输出` 81 `（即 `3 * 3 * 3 * 3` ）。

`/ `（除）

- x 除以 y
- `13 / 3` 输出 `4.333333333333333` 。

`// `（整除）

- `x` 除以 `y `并对结果向下取整至最接近的整数。
- `13 // 3` 输出 `4 `。
- `-13 // 3 `输出` -5` 。

`% `（取模）

- 返回除法运算后的余数。
- `13 % 3` 输出` 1 `。` -25.5 % 2.25 `输出 `1.5` 。

`<< `（左移）

- 将数字的位向左移动指定的位数。（每个数字在内存中以二进制数表示，即` 0 `和`1`）
- `2 << 2 `输出 `8` 。` 2` 用二进制数表示为 `10 `。
- 向左移` 2 `位会得到 `1000 `这一结果，表示十进制中的` 8 `。

`>>` （右移）

- 将数字的位向右移动指定的位数。
- `11 >> 1` 输出` 5` 。
- `11` 在二进制中表示为` 1011` ，右移一位后输出 `101` 这一结果，表示十进制中的`5` 。

`& `（按位与）

- 对数字进行按位与操作。
- `5 & 3` 输出` 1` 。

`| `（按位或）

- 对数字进行按位或操作。
- `5 | 3` 输出` 7 `。

`^ `（按位异或）

- 对数字进行按位异或操作。
- `5 ^ 3` 输出` 6 `。

`~` （按位取反）

- `x` 的按位取反结果为` -(x+1)`。
- `~5 `输出 `-6` 。

`<` （小于）

- 返回 x 是否小于 y。所有的比较运算符返回的结果均为 `True` 或 `False `。请注意这些名称之中的大写字母。
- `5 < 3 `输出` False` ， `3 < 6` 输出 `True `。
- 比较可以任意组成组成链接： `3 < 5 < 7 `返回` True `。

`> `（大于）

- 返回 x 是否大于 y。
- `5 > 3 `返回` True `。如果两个操作数均为数字，它们首先将会被转换至一种共同的类型。否则，它将总是返回` False `。

`<=` （小于等于）

- 返回 x 是否小于或等于 y。
- `x = 3; y = 6; x<=y` 返回` True` 。

`>= `（大于等于）

- 返回 x 是否大于或等于 y。
- `x = 4; y = 3; x>=3 `返回 `True` 。

`== `（等于）

- 比较两个对象是否相等。
- `x = 2; y = 2; x == y `返回 `True `。
- `x = 'str'; y = 'stR'; x == y` 返回 `False `。
- `x = 'str'; y = 'str'; x == y `返回 `True` 。

`!= `（不等于）

- 比较两个对象是否不相等。
- `x = 2; y = 3; x != y `返回 `True` 。

`not `（布尔“非”）

- 如果 x 是 `True `，则返回 `False `。如果 x 是 `False `，则返回 `True `。
- `x = True; not x` 返回` False` 。

`and `（布尔“与”）

- 如果 x 是 `False` ，则` x and y `返回 `False `，否则返回 y 的计算值。
- 当 x 是` False `时，` x = False; y = True; x and y `将返回 False 。在这一情境中，Python 将不会计算 y，因为它已经了解 and 表达式的左侧是 False ，这意味着整个表达式都将是 False 而不会是别的值。这种情况被称作**短路计算（Short-circuit Evaluation）**。

`or `（布尔“或”）

- 如果 x 是 `True `，则返回 `True `，否则它将返回 y 的计算值。
- `x = Ture; y = False; x or y `将返回 Ture 。在这里**短路计算**同样适用。

#### 数值运算与赋值的快捷方式

一种比较常见的操作是对一个变量进行一项数学运算并将运算得出的结果返回给这个变量，因此对于这类运算通常有如下的快捷表达方式：

```python
a = 2
a = a * 3
```

同样也可写作：

```python
a = 2
a *= 3
```

要注意到 `变量 = 变量 运算 表达式` 会演变成 `变量 运算 = 表达式` 。

#### 求值顺序

下面将给出 Python 中从 **最低优先级** 到 **最高优先级** 的优先级表。

- `lambda `：Lambda 表达式
- `if - else` ：条件表达式
- `or` ：布尔“或”
- `and `：布尔“与”
- `not x` ：布尔“非”
- `in, not in, is, is not, <, <=, >, >=, !=, == `：比较，包括成员资格测试（Membership Tests）和身份测试（Identity Tests）。
- `| `：按位或
- `^ `：按位异或
- `& `：按位与
- `<<, >>` ：移动
- `+, -` ：加与减
- `*, /, //, % `：乘、除、整除、取余
- `+x, -x, ~x `：正、负、按位取反
- `** `：求幂

- `x[index], x[index:index], x(arguments...), x.attribute `：下标、切片、调用、属性引用
- `(expressions...), [expressions...], {key: value...}, {expressions...} `：表示绑定或元组、表示列表、表示字典、表示集合。

> 上表中位列同一行的运算符具有相同优先级。例如 + 和 - 就具有相同的优先级。

#### 改变运算顺序

- 为了使表达式更加易读，我们可以使用括号。
- 使用括号还有一个额外的优点——它能帮助我们改变运算的顺序。同样举个例子，如果你希望在表达式中计算乘法之前应先计算加法，那么你可以将表达式写作 `(2 + 3) * 4 `。

#### 结合性

- 运算符通常**由左至右**结合。这意味着具有相同优先级的运算符将从左至右的方式依次进行求值。如 `2 + 3 + 4 `将会以 `(2 + 3) +4 `的形式加以计算。

### 表达式

例子（将其保存为` expression.py`）

```python
#表达式例子
length=5
breadth=2

area=length*breadth
print("Area is",area)
print("Perimeter is",2*(length+breadth))
```

输出：

```python
$ python expression.py
Area is 10
Perimeter is 14
```

*它是如何工作的?*

> 矩形的长度（Length）与宽度（Breadth）存储在以各自名称命名的变量中。我们使用它们并借助表达式来计算矩形的面积（Area）与周长（Perimeter）。我们将表达式 `length *breadth `的结果存储在变量 area 中并将其通过使用` print `函数打印出来。
>
> 在第二种情况中，我们直接在 print 函数中使用了表达式` 2 * (length + breadth) `的值。

> 同时，你需要注意到 Python是如何漂亮地打印出 输出结果的。尽管我们没有特别在 Area is 和变量 area 之间指定空格，Python 会自动帮我们加上，所以我们就能得到一个整洁的输出结果，同时程序也因为这样的处理方式而变得更加易读（因为我们不需要在用以输出的字符串中考虑空格问题）。

### 总结

我们已经了解了如何使用运算符、操作数与表达式——这些是我们构建任何程序的基本块。接下来，我们将看到如何在程序中利用这些语句。