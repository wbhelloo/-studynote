## 字符串

JavaScript的字符串就是用`''`或`""`括起来的字符表示。

如果`'`本身也是一个字符，那就可以用`""`括起来，比如`"I'm OK"`包含的字符是`I`，`'`，`m`，`空格`，`O`，`K`这6个字符。

如果字符串内部既包含`'`又包含`"`怎么办？可以用转义字符`\`来标识，比如：

```javascript
'I\'m \"OK\"!';

#
"I'm "OK"!"
```
转义字符`\`可以转义很多字符，比如`\n`表示换行，`\t`表示制表符，字符`\`本身也要转义，所以`\\`表示的字符就是`\`。

ASCII字符可以以`\x##`形式的十六进制表示，例如：

```javascript
'\x41'

#
"A"
```

还可以用`\u####`表示一个Unicode字符：

```javascript
'\u4e2d\u6587'; 

#
"中文"
```

### 多行字符串

由于多行字符串用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用反引号 \`\` 表示：

```javascript
`这是一个
多行
字符串`;

#
"这是一个
多行
字符串"
```

### 模板字符串

要把多个字符串连接起来，可以用`+`号连接：

```javascript
var name = '小明';
var age = 20;
var message = '你好, ' + name + ', 你今年' + age + '岁了!';
alert(message);

#
你好, 小明, 你今年20岁了!
```

如果有很多变量需要连接，用+号就比较麻烦。ES6新增了一种模板字符串，表示方法和上面的多行字符串一样，但是它会自动替换字符串中的变量：

```javascript
var name = '小明';
var age = 20;
var message = `你好, ${name}, 你今年${age}岁了!`;
alert(message);

# 
你好, 小明, 你今年20岁了!
```

### 操作字符串

字符串常见的操作如下：

```javascript
var s = 'hello world';
s.length

#
11
```

要获取字符串某个指定位置的字符，使用类似`Array`的下标操作，索引号从`0`开始：

```javascript
var s = 'hello world'
s.length
#
11

s[5]
#
" "
s[6]
#
"w"
```

JavaScript为字符串提供了一些常用方法，注意，调用这些方法本身不会改变原有字符串的内容，而是返回一个新字符串：

### toUpperCase

toUpperCase()把字符串全部变为大写：

```javascript
var s = 'hello world'
s.toUpperCase()
#
"HELLO WORLD"
```

### toLowerCase

toLowerCase()把一个字符串全部变为小写：

### indexOf

indexOf()会搜索指定字符串出现的位置：

```javascript
var s = 'hello world'
s.indexOf('o')
# 
4
```
### substring

substring()返回指定索引区间的子串：

```javascript
var s = "hello world";
s.substring(1,3);
#
"el"
```
