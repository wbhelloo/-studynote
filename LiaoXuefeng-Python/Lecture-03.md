
## Python基础_ list和tuple

### list

Python内置的一种数据类型是列表：list。list是一种有序的集合，可以随时添加和删除其中的元素。

比如，列出班里所有同学的名字，就可以用一个list表示：


```python
classmates = ['Michael', 'Bob', 'Tracy']
classmates
```




    ['Michael', 'Bob', 'Tracy']



变量classmates就是一个list。用len()函数可以获得list元素的个数：


```python
len(classmates)
```




    3



用索引来访问list中每一个位置的元素，记得索引是从0开始的：


```python
classmates[0]
```




    'Michael'



> 当索引超出了范围时，Python会报一个`IndexError`错误，所以，要确保索引不要越界，记得最后一个元素的索引是`len(classmates) - 1`

如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：


```python
classmates[-1]
```




    'Tracy'




```python
classmates[-2]
```




    'Bob'



list是一个可变的有序表，所以，可以往list中追加元素到末尾：


```python
classmates.append("Frank")
classmates
```




    ['Michael', 'Bob', 'Tracy', 'Frank', 'Frank']



也可以把元素插入到指定的位置，比如索引号为1的位置：


```python
classmates.insert(0, 'Adam')
classmates
```




    ['Adam', 'Adam', 'Michael', 'Bob', 'Tracy', 'Frank', 'Frank']



要删除list末尾的元素，用pop()方法：


```python
classmates.pop()
```




    'Frank'



要删除指定位置的元素，用pop(i)方法，其中i是索引位置：


```python
classmates.pop(1)
```




    'Adam'



要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：


```python
classmates[1] = "Serah"
classmates
```




    ['Adam', 'Serah', 'Bob', 'Tracy', 'Frank']



list里面的元素的数据类型也可以不同，比如：


```python
L = ['Apple', 123, True]
L
```




    ['Apple', 123, True]




```python
s = ['Python', 'Java', ['asp', 'php'], 'scheme']
len(s)
```




    4



要注意s只有4个元素，其中s[2]又是一个list，如果拆开写就更容易理解了：


```python
p = ['asp', 'php']
s = ['python', 'java', p, 'scheme']
```

要拿到'php'可以写p[1]或者s[2][1]，因此s可以看成是一个二维数组，类似的还有三维、四维……数组，不过很少用到。


```python
s[2][0]
```




    'asp'



如果一个list中一个元素也没有，就是一个空的list，它的长度为0：


```python
L = []
len(L)
```




    0



### tuple 

另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改，比如同样是列出同学的名字：


```python
classmates = ('Michael', 'Bob', 'Tracy')
classmates
```




    ('Michael', 'Bob', 'Tracy')



现在，`classmates`这个`tuple`不能变了，它也没有`append()`，`insert()`这样的方法。其他获取元素的方法和`list`是一样的，你可以正常地使用`classmates[0]`，`classmates[-1]`，但不能赋值成另外的元素。

当你定义一个tuple时，在定义的时候，tuple的元素就必须被确定下来，比如：


```python
t = (1, 2)
t
```




    (1, 2)



如果要定义一个空的tuple，可以写成()：


```python
t = ()
t
```




    ()



但是，要定义一个只有1个元素的tuple，如果你这么定义：


```python
t = (1)
t
```




    1



定义的不是tuple，是1这个数！这是因为括号`()`既可以表示`tuple`，又可以表示数学公式中的小括号，这就产生了歧义，因此，Python规定，这种情况下，按小括号进行计算，计算结果自然是1。

所以，只有1个元素的`tuple`定义时必须加一个`逗号`,，来消除歧义：


```python
t = (1,)
t
```




    (1,)



Python在显示只有1个元素的tuple时，也会加一个逗号,，以免你误解成数学计算意义上的括号。

#### 一个“可变的”tuple：


```python
t = ('a', 'b', ['A', 'B'])
t[2][0] = 'X'
t[2][1] = 'Y'
t
```




    ('a', 'b', ['X', 'Y'])



这个tuple定义的时候有3个元素，分别是`'a'`，`'b'`和一个`list`。

表面上看，`tuple`的元素确实变了，但其实变的不是`tuple`的元素，而是**list**的元素。tuple一开始指向的`list`并没有改成别的`list`，所以，`tuple`所谓的“不变”是说，`tuple`的每个元素，指向永远不变。即指向`'a'`，就不能改成指向`'b'`，指向一个`list`，就不能改成指向其他对象，但指向的这个`list`本身是可变的！

理解了“指向不变”后，要创建一个内容也不变的`tuple`怎么做？那就必须保证`tuple`每一个元素本身也不能变。

### 小结

- `list`和`tuple`是Python内置的有序集合，一个可变，一个不可变。根据需要来选择使用它们。

完
