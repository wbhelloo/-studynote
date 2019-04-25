
## Python基础_字符串和编码

### ASCII编码和Unicode编码的区别：

ASCII编码是1个字节，而Unicode编码通常是2个字节。

字母`A`用ASCII编码是十进制的`65`，二进制的`01000001`；

字符`0`用ASCII编码是十进制的`48`，二进制的`00110000`，注意字符`'0'`和整数`0`是不同的；

如果把ASCII编码的`A`用Unicode编码，只需要在前面补`0`就可以，因此，A的Unicode编码是`00000000 01000001`。

### UTF-8编码

UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，

常用的英文字母被编码成1个字节，

汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。

如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间。

| 字符 | ASCII | Unicode | UTF-8 |
| :------: | :------: | :------: | :------: |
| A | 01000001 | 00000000 01000001 | 01000001 |
| 中 | x | 01001110 00101101 | 11100100 10111000 10101101 |

从上面的表格还可以发现，UTF-8编码有一个额外的好处，就是ASCII编码实际上可以被看成是UTF-8编码的一部分，所以，大量只支持ASCII编码的历史遗留软件可以在UTF-8编码下继续工作。

### 现在计算机系统通用的字符编码工作方式:

* 在计算机内存中，统一使用Unicode编码，当需要保存到硬盘或者需要传输的时候，就转换为UTF-8编码.

* 用记事本编辑的时候，从文件读取的UTF-8字符被转换为Unicode字符到内存里，编辑完成后，保存的时候再把Unicode转换为UTF-8保存到文件.

*  浏览网页的时候，服务器会把动态生成的Unicode内容转换为UTF-8再传输到浏览器.

    - 所以你看到很多网页的源码上会有类似`<meta charset="UTF-8" />`的信息，表示该网页正是用的UTF-8编码。

### Python的字符串

 在最新的 Python 3 版本中，字符串是以`Unicode`编码的，也就是说，Python的字符串支持多语言，例如：


```python
print('包含中文的str')
```

    包含中文的str


对于单个字符的编码，Python提供了 `ord()` 函数获取字符的整数表示


```python
ord('A')
```




    65




```python
ord('a')
```




    97




```python
ord("中")
```




    20013



`chr()` 函数把编码转换为对应的字符：


```python
chr(65)
```




    'A'




```python
chr(20013)
```




    '中'



如果知道字符的整数编码，还可以用十六进制这么写`str`


```python
'\u4e2d\u6587'
```




    '中文'



两种写法完全是等价的.

由于Python的字符串类型是 `str`，在内存中以`Unicode`表示，一个字符对应若干个字节。如果要在网络上传输，或者保存到磁盘上，就需要把 `str` 变为以字节为单位的`bytes`。

Python对`bytes`类型的数据用带 `b` 前缀的**单引号**或**双引号**表示：


```python
x = b'ABC'
```

要注意区分`'ABC'`和`b'ABC'`，前者是`str`，后者虽然内容显示得和前者一样，但`bytes`的每个字符都只占用一个字节。

以`Unicode`表示的`str`通过`encode()`方法可以编码为指定的`bytes`，例如：


```python
'ABC'.encode('ascii')
```




    b'ABC'




```python
'中文'.encode('utf-8')
```




    b'\xe4\xb8\xad\xe6\x96\x87'




```python
'中文'.encode('ascii')
```


    ---------------------------------------------------------------------------

    UnicodeEncodeError                        Traceback (most recent call last)

    <ipython-input-18-76f41cd8dafa> in <module>
    ----> 1 '中文'.encode('ascii')
    

    UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)


纯英文的`str`可以用`SCII`编码为`bytes`，内容是一样的，含有中文的`str`可以用`UTF-8`编码为`bytes`。含有中文的`str`无法用`ASCII`编码，因为中文编码的范围超过了`ASCII`编码的范围，Python会报错。

在bytes中，无法显示为ASCII字符的字节，用`\x##`显示。

反过来，如果我们从网络或磁盘上读取了字节流，那么读到的数据就是`bytes`。要把`bytes`变为`str`，就需要用`decode()`方法：


```python
b'ABC'.decode('ascii')
```




    'ABC'




```python
 b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
```




    '中文'



如果bytes中包含无法解码的字节，decode()方法会报错：


```python
b'\xe4\xb8\xad\xff'.decode('utf-8')
```


    ---------------------------------------------------------------------------

    UnicodeDecodeError                        Traceback (most recent call last)

    <ipython-input-21-cd8de1b11dcd> in <module>
    ----> 1 b'\xe4\xb8\xad\xff'.decode('utf-8')
    

    UnicodeDecodeError: 'utf-8' codec can't decode byte 0xff in position 3: invalid start byte


如果bytes中只有一小部分无效的字节，可以传入`errors='ignore'`忽略错误的字节：


```python
b'\xe4\xb8\xad\xff'.decode('utf-8', errors='ignore')
```




    '中'



要计算`str`包含多少个字符，可以用`len()`函数：


```python
len("ABC")
```




    3




```python
len("中文")
```




    2



`len()`函数计算的是`str`的字符数，如果换成`bytes`，`len()`函数就计算字节数：


```python
len(b'ABC')
```




    3




```python
len(b'\xe4\xb8\xad\xe6\x96\x87')
```




    6




```python
len('中文'.encode('utf-8'))
```




    6



由此可见，1个中文字符经过UTF-8编码后通常会占用3个字节，而1个英文字符只占用1个字节。

在操作字符串时，我们经常遇到str和bytes的互相转换。为了避免乱码问题，应当始终坚持使用UTF-8编码对str和bytes进行转换。

由于Python源代码也是一个文本文件，所以，当你的源代码中包含中文的时候，在保存源代码时，就需要务必指定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：

`#!/usr/bin/env python3`

`# -*- coding: utf-8 -*-`


第一行注释是为了告诉Linux/OS X系统，这是一个Python可执行程序，Windows系统会忽略这个注释；

第二行注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。

申明了UTF-8编码并不意味着你的.py文件就是UTF-8编码的，必须并且要确保文本编辑器正在使用UTF-8 without BOM编码：

### 格式化

最后一个常见的问题是如何输出格式化的字符串。我们经常会输出类似'亲爱的xxx你好！你xx月的话费是xx，余额是xx'之类的字符串，而xxx的内容都是根据变量变化的，所以，需要一种简便的格式化字符串的方式。

在Python中，采用的格式化方式和C语言是一致的，用%实现，举例如下：


```python
'hello, %s' % 'world'
```




    'hello, world'




```python
'Hi, %s, you have $%d dollar.' % ('Frank', 10000)
```




    'Hi, Frank, you have $10000 dollar.'



`%`运算符就是用来格式化字符串的。在字符串内部，`%s`表示用字符串替换，`%d`表示用整数替换，有几个`%?`占位符，后面就跟几个变量或者值，顺序要对应好。如果只有一个`%?`，括号可以省略。

常见的占位符有：

| 占位符 | 替换内容 |
| ---- | ---- |
| %d | 整数 |
| %s | 字符串 |
| %f | 浮点数 |
| %x | 十六进制整数 |

其中，格式化整数和浮点数还可以指定是否补0和整数与小数的位数：


```python
print('%02d-%03d' % (3, 1))
```

    03-001



```python
print('%.2f' % 3.1415926)
```

    3.14


如果你不太确定应该用什么，`%s`永远起作用，它会把任何数据类型转换为`字符串`：


```python
'Age: %s. Gender: %s' % (25, True)
```




    'Age: 25. Gender: True'



有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用`%%`来表示一个`%`


```python
'growth rate: %d %%' % 7
```




    'growth rate: 7 %'



### format()

另一种格式化字符串的方法是使用字符串的format()方法，它会用传入的参数依次替换字符串内的占位符{0}、{1}……，不过这种方式写起来比%要麻烦得多.


```python
'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)
```




    'Hello, 小明, 成绩提升了 17.1%'



## 小结

- Python 3的字符串使用Unicode，直接支持多语言。

- 当str和bytes互相转换时，需要指定编码。最常用的编码是UTF-8，如果没有特殊业务要求，请牢记仅使用UTF-8编码。

完
