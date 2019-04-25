
## 05 Python基础_循环

### For循环

为了让计算机能计算成千上万次的重复运算，我们就需要循环语句

Python的循环有两种，一种是`for...in`循环，依次把`list`或`tuple`中的每个元素迭代出来，例子：


```python
names = ['Michael','Bob','Tracy']
for name in names:
    print(name)
```

    Michael
    Bob
    Tracy


`for x in ...`循环就是把每个元素代入变量`x`，然后执行缩进块的语句.

再比如我们想计算1-10的整数之和，可以用一个`sum`变量做累加.


```python
sum = 0
for x in [1,2,3,4,5,6,7,8,9,10]:
    sum = sum + x
print(sum)
```

    55


如果要计算1-100的整数之和，从1写到100有点困难，Python提供一个`range()`函数，可以生成一个整数序列，再通过`list()`函数可以转换为list。比如`range(5)`生成的序列是从0开始小于5的整数.


```python
a = range(5)
```


```python
list(a)
```




    [0, 1, 2, 3, 4]



`range(101)`就可以生成0-100的整数序列，计算如下


```python
list(range(101))
```




    [0,
     1,
     2,
     3,
     4,
     5,
     6,
     7,
     8,
     9,
     10,
     11,
     12,
     13,
     14,
     15,
     16,
     17,
     18,
     19,
     20,
     21,
     22,
     23,
     24,
     25,
     26,
     27,
     28,
     29,
     30,
     31,
     32,
     33,
     34,
     35,
     36,
     37,
     38,
     39,
     40,
     41,
     42,
     43,
     44,
     45,
     46,
     47,
     48,
     49,
     50,
     51,
     52,
     53,
     54,
     55,
     56,
     57,
     58,
     59,
     60,
     61,
     62,
     63,
     64,
     65,
     66,
     67,
     68,
     69,
     70,
     71,
     72,
     73,
     74,
     75,
     76,
     77,
     78,
     79,
     80,
     81,
     82,
     83,
     84,
     85,
     86,
     87,
     88,
     89,
     90,
     91,
     92,
     93,
     94,
     95,
     96,
     97,
     98,
     99,
     100]




```python
sum = 0
for x in list(range(101)):
    sum = sum + x
    
print(sum)
```

    5050


### While循环

第二种循环是while循环，只要条件满足，就不断循环，条件不满足时退出循环。比如我们要计算100以内所有奇数之和，可以用while循环实现：


```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)
```

    2500


在循环内部变量n不断自减，直到变为-1时，不再满足while条件，循环退出。

#### 练习

请利用循环依次对list中的每个名字打印出Hello, xxx!


```python
L = ['Bart', 'List','Adam']
n = len(L)
for i in list(range(n)):
    print("Hello, %s" % L[i])
```

    Hello, Bart
    Hello, List
    Hello, Adam


### Break

在循环中，break语句可以提前退出循环。


```python
n = 1
while n <= 10:
    print(n)
    n = n + 1
print('END')
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    END


如果要提前结束循环，可以用break语句：


```python
n = 1
while n <= 10:
    if n > 3: # 当n = 11时，条件满足，执行break语句
        break # break语句会结束当前循环
    print(n)
    n = n + 1
print('END')
```

    1
    2
    3
    END


break的作用是提前结束循环.

### continue

在循环过程中，也可以通过continue语句，跳过当前的这次循环，直接开始下一次循环。


```python
n = 0
while n < 10:
    n = n + 1
    print(n)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10


上面的程序可以打印出1～10。

但是，如果我们想只打印奇数，可以用`continue`语句跳过某些循环：


```python
n = 0
while n < 10:
    n = n + 1
    if n % 2 == 0: # 如果n是偶数，执行continue语句
        continue # continue语句会直接继续下一轮循环，后续的print()语句不会执行
    print(n)
```

    1
    3
    5
    7
    9


`continue`的作用是提前结束本轮循环，并直接开始下一轮循环。

### 小结

- 循环是让计算机做重复任务的有效的方法。

- break语句可以在循环过程中直接退出循环，而continue语句可以提前结束本轮循环，并直接开始下一轮循环。这两个语句通常都必须配合if语句使用。

    > 要特别注意，不要滥用break和continue语句。break和continue会造成代码执行逻辑分叉过多，容易出错。大多数循环并不需要用到break和continue语句，上面的两个例子，都可以通过改写循环条件或者修改循环逻辑，去掉break和continue语句。

- 有些时候，如果代码写得有问题，会让程序陷入“死循环”，也就是永远循环下去。这时可以用`Ctrl+C`退出程序，或者强制结束Python进程。

完
