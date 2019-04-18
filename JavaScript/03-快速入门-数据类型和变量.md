## 04 数据类型和变量

在`JavaScript`中定义了以下几种数据类型：

 - Number

    `JavaScript`不区分整数和浮点数，统一用Number表示，

    > 由于计算机使用二进制，所以，有时候用十六进制表示整数比较方便。
    十六进制用`0x`前缀和`0-9`，`a-f`表示，例如：`0xff00`，`0xa5b4c3d2`，等等，它们和十进制表示的数值完全一样。    

    Number可以直接做四则运算，规则和数学一致

    ```javascript
    1 + 2;   // 3
    (1 + 2) * 5 / 2;   // 7.5
    2 / 0;   // Infinity
    0 / 0;   // NaN
    10 % 3;   // 1
    10.5 % 3;   // 取余运算。1.5
    ```

 - 字符串

    字符串是以单引号 \' 或双引号 \" 括起来的任意文本，比如`'abc'`，`"xyz"`等等。

 - 布尔值

    布尔值和布尔代数的表示完全一致，一个布尔值只有`true`、`false`两种值。

    ```javascript
    2 > 1;   // 这是一个true值
    2 >= 3;   // 这是一个false值
    ```

    `&&` 运算是与运算。只有所有都为`true`，`&&`运算结果才是`true`：

    ```javascript
    true && true; // 这个&&语句计算结果为true
    true && false; // 这个&&语句计算结果为false
    ```

    `||`运算是或运算。

    ```javascript
    false || false;   // 这个||语句计算结果为false
    true || false;   // 这个||语句计算结果为true
    ```

    `!`运算是非运算，它是一个单目运算符，把`true`变成`false`，`false`变成`true`.

    ```javascript
    ! true; // 结果为false
    ! false; // 结果为true
    ! (2 > 5); // 结果为true
    ```

    布尔值经常用在条件判断中，比如：

    ```javascript
    var age = 15;
    if (age >= 18) {
        alert('adult');
    } else {
        alert('teenager');
    }
    ```

 - 比较运算符    

    当我们对Number做比较时，可以通过比较运算符得到一个布尔值：

    ```javascript
    2 > 5; // false
    5 >= 2; // true
    7 === 7; // true
    ```
    > 特别注意：相等运算符`===`

    `JavaScript`允许对任意数据类型做比较，例如：    

    ```javascript
    false === 0; // false
    ```

    另一个例外是`NaN`这个特殊的Number与所有其他值都不相等，包括它自己：
    
    ```javascript
    NaN === NaN;   // false
    ```

    唯一能判断NaN的方法是通过`isNaN()`函数：

    ```javascript
    isNaN(NaN);   // true
    ```

    浮点数的相等比较

    ```javascript
    1 / 3 === (1 - 2 / 3);   // false
    ```

    > 原因：浮点数在运算过程中会产生误差，因为计算机无法精确表示无限循环小数。要比较两个浮点数是否相等，只能计算它们之差的绝对值，看是否小于某个阈值。

    ```javascript
    Math.abs(1 / 3 - (1 - 2 / 3)) < 0.0000001;    // true
    ```

 - `null`和`undefined`

    `null`表示一个“空”的值，它和`0`以及空字符串`''`不同，`0`是一个数值，`''`表示长度为`0`的字符串，而`null`表示`空`。

    `undefined`，它表示“未定义”。

 - 数组

    数组是一组按顺序排列的集合，集合的每个值称为元素。数组用`[]`表示，元素之间用`,`分隔, `JavaScript`的数组可以包括任意数据类型。例如：

    ```javascript
    [1, 2, 3.14, 'Hello', null, true];
    ```
    另一种创建数组的方法是通过`Array()`函数实现

    ```javascript
    new Array(1, 2, 3); // 创建了数组[1, 2, 3]
    ```

    数组的元素可以通过索引来访问。请注意，索引的起始值为`0`：

    ```javascript
    var arr = [1, 2, 3.14, 'Hello', null, true];
    arr[0]; // 返回索引为0的元素，即1
    arr[5]; // 返回索引为5的元素，即true
    arr[6]; // 索引超出了范围，返回undefined
    ```

 - 对象
    
    `JavaScript`的对象是一组由`键-值`组成的`无序集合`，JavaScript对象的`键`都是`字符串`类型，`值`可以是`任意数据类型`。例如：    

    ```javascript
        var person = {
        name: 'Bob',
        age: 20,
        tags: ['js', 'web', 'mobile'],
        city: 'Beijing',
        hasCar: true,
        zipcode: null
    };
    ```

    要获取一个对象的属性，我们用`对象变量.属性名`的方式：

    ```javascript
    person.name; // 'Bob'
    person.zipcode; // null
    ```

## 变量

 - 变量

    变量在 `JavaScript`中就是用一个变量名表示，变量名是`大小写英文`、`数字`、`$`和`_`的组合，且<font color = red>不能用数字开头</font>。变量名也不能是`JavaScript`的关键字，如`if`、`while`等。
    
    申明一个变量用`var`语句，比如：

    ```javascript
    var a; // 申明了变量a，此时a的值为undefined
    var $b = 1; // 申明了变量$b，同时给$b赋值，此时$b的值为1
    var s_007 = '007'; // s_007是一个字符串
    var Answer = true; // Answer是一个布尔值true
    var t = null; // t的值是null
    ```

    在JavaScript中，使用等号`=`对变量进行赋值。可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量，但是要注意只能用var申明一次，例如：

    ```javascript
    var a = 123; // a的值是整数123
    a = 'ABC'; // a变为字符串
    ```    

    要显示变量的内容，可以用`console.log(x)`，打开`Chrome`的控制台就可以看到结果。

    使用`console.log()`代替`alert()`的好处是可以避免弹出烦人的对话框。

 - `strict`模式    

    `JavaScript`在设计之初，为了方便初学者学习，并不强制要求用`var`申明变量。这个设计错误带来了严重的后果：如果一个变量没有通过`var`申明就被使用，那么该变量就自动被申明为全局变量：

    为了修补`JavaScript`这一严重设计缺陷，`ECMA`在后续规范中推出了`strict`模式，在`strict`模式下运行的`JavaScript`代码，强制通过`var`申明变量，未使用`var`申明变量就使用的，将导致运行错误。

    启用`strict`模式的方法是在`JavaScript`代码的第一行写上：

    ```javascript
    'use strict';
    ```

    不用`var`申明的变量会被视为全局变量，为了避免这一缺陷，所有的`JavaScript`代码都应该使用`strict`模式。
