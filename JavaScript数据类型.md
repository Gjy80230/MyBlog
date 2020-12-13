# JavaScript数据类型

JS目前有7种类型，但是我目前只学了5种。即： `Number` (数值) 、 `String` (字符串)、 `Boolean` (布尔值)、 `Undefined` (未定义)、 `Null` (空)。
### 为什么需要区分类型？

1. 因为 **不同类型之间的功能不同** ，比如：数字能进行加减乘除，但是字符串不行；字符串能表示电话号码，如果你用数字存020，那么数字前面的 `0` 会被认为是可以省略的。
1. 除了这个还有 **存储的形式也不同** ，JS中数字是用64位浮点数的形式存储的；而字符串是用类似UTF8形式存储的（UCS-2）。



### Number(数值)
JavaScript 内部，所有数字都是以64位浮点数形式储存，即使整数也是如此。
```javascript
1 === 1.0 // true 
```
`1` 与 `1.0` 是相同的，是同一个数。也就是说，JavaScript 语言的底层根本没有整数，所有数字都是小数（64位浮点数）。<br />

### 数值的写法
#### 整数写法
> 1

#### 小数写法
> 0.1

#### 科学计数法
> 1.23e4

#### 八进制写法（用得少）
> 0123 或 00123 或 0o123

#### 十六进制写法
> 0x3F 或 0X3F

#### 二进制写法
> 0b11 或 0B11



### 特殊值
#### 正零和负零
JavaScript 内部实际上存在2个 `0` ：一个是 `+0` ，一个是 `-0` ，区别就是64位浮点数表示法的符号位不同。
```javascript
-0 === +0 // true
0 === -0 // true
0 === +0 // true
```
它们虽然是等价的，但是在作为分母的时候，就不一样了。
```javascript
1 / 0	//Infinity
1 / +0	//Infinity
1 / -0	//-Infinity
```
得到的结果有正和负，这两个是不相等的。
#### Infinity
`Infinity` 表示“无穷”，刚才上面也演示了，一种是一个正的数值太大，或一个负的数值太小，无法表示；另一种是非0数值除以0，得到 `Infinity` 。<br />`Infinity` 有正负之分， `Infinity` 表示正的无穷， `-Infinity` 表示负的无穷。<br />
<br />`Infinity` 大于一切数值（除了 `NaN` ）， `-Infinity` 小于一切数值（除了 `NaN` ）。
```javascript
Infinity > 1000 // true
-Infinity < -1000 // true
```
`Infinity` 与 `NaN` 比较，总是返回 `false` 。
```javascript
Infinity > NaN // false
-Infinity > NaN // false

Infinity < NaN // false
-Infinity < NaN // false
```
#### NaN（Not a Number）
NaN是 JavaScript 的特殊值，表示“非数字”，例如 `0` 除以 `0` 会得到 `NaN` 。
```javascript
0 / 0 // NaN  
```
需要注意， `NaN` 是一个特殊数值，同时它的数据类型是 `Number` 
```javascript
typeof NaN	//number
```
`NaN` 不等于任何值，包括它本身。
```javascript
NaN === NaN // false
```
`NaN` 在布尔运算时被当作 `false` 。
```javascript
Boolean(NaN) // false
```
`NaN` 与任何数（包括它自己）的运算，得到的都是 `NaN` 。
```javascript
NaN + 32 // NaN
NaN - 32 // NaN
NaN * 32 // NaN
NaN / 32 // NaN   
```


### String(字符串)
#### 定义
字符串就是零个或多个排在一起的字符，每个字符两个字节，放在单引号或双引号之中。
```javascript
'abc'
"abc" 
"123"
```
单引号字符串的内部，可以使用双引号。双引号字符串的内部，可以使用单引号。
```javascript
"She said 'Hello'"
"It's OK" 
```
注意：引号不属于字符串的一部分，就像书名号不属于书名的一部分一样。<br />

#### 转义
JS引擎会认为 `'it'` 就结束了，后面的看不懂，于是报错。
```javascript
'it's ok'		//Unexpected identifier
```
如果要在单引号字符串的内部，使用单引号，就必须在内部的单引号前面加上反斜杠，用来转义。双引号字符串内部使用双引号，也是如此。
```javascript
'it\'s ok' //"it's ok"  
```
用反斜杠转义还可以表示特殊字符，主要有下面这些。

- `\0`  ：null
- `\b`  ：后退键
- `\f`  ：换页符
- `\n`  ：换行符
- `\r`  ：回车键
- `\t`  ：制表符
- `\v`  ：垂直制表符
- `\'`  ：单引号
- `\"`  ：双引号
- `\\`  ：反斜杠
```javascript
console.log('1\n2')
// 1
// 2  
```
上面代码中， `\n` 表示换行，输出的时候就分成了两行。  <br />如果在非特殊字符前面使用反斜杠，则反斜杠会被省略。
```javascript
'\a'	// "a"
```
上面代码中， `a` 是一个正常字符，前面加反斜杠没有特殊含义，反斜杠会被自动省略。
#### 多行字符串
如果你想要在字符串里回车
```javascript
let s=\` 这样是
可以的
用反引号很容易做到\`	
```
就像上面的代码一样，很容易做到，但是这个是新的语法，没有反引号之前是怎么写多行字符串的呢？  <br />以前，字符串默认只能写在一行内，分成多行将会报错。
```javascript
'a
b
c'
// Invalid or unexpected token	
```
如果长字符串必须分成多行，可以在每一行的尾部使用反斜杠。
```javascript
var longString = 'Long \
long \
long \
string';

longString
// "Long long long string"

```
上面代码表示，加了反斜杠以后，原来写在一行的字符串，可以分成多行书写。但是，输出的时候还是单行，效果与写在同一行完全一样。注意，反斜杠的后面必须是换行符，而不能有其他字符（比如空格），否则会报错。<br />
<br />也可以用连接运算符（ `+` ）可以连接多个单行字符串，将长字符串拆成多行书写，输出的时候也是单行。
```javascript
var longString = 'Long '
  + 'long '
  + 'long '
  + 'string';
```
不过这些方法都太麻烦了，还是反引号比较好用。
#### 字符串的属性
没有错，字符串是有属性的，这一点学了 `Object` 对象这个数据类型我们才能说清楚（下一节）。
```javascript
'123'.length        //3
'\n\r\t'.length     //3
''.length           //0
' '.length           //1
```
我们还可以通过下标读取字符
```javascript
let s = 'hello'
s[0]    //"h"
s[4]		//"o"	
```
注意方括号中的数字是从0开始的，如果超过字符串的长度，或者方括号中根本不是数字，则返回 `undefined` 。
```javascript
'abc'[3] // undefined
'abc'[-1] // undefined
'abc'['x'] // undefined
```
<br />
### Undefined(未定义)和Null(空)。
`null` 与 `undefined` 都可以表示“没有”，虽然含义非常相似，但是也有区别。
#### 区别**

1. 如果一个变量声明了，但没有赋值，那么默认值就是 `undefined` ，而不是 `null` **
1. 如果一个函数，没有写 `return` ，那么默认return `undefined` ，而不是 `null` 
1. 习惯上，把非对象的空值写为 `undefined` ，把对象的空值写为 `null` 



### Boolean(布尔值)
布尔值只有两个值。代表“真”和“假”两个状态。“真”用关键字 `true` 表示，“假”用关键字 `false` 表示。  <br />下列运算会得到bool值：

- 前置逻辑运算： `!value` (否定)
- 相等运算： `1==2` , `1！=2` , `3===4` , `3！==4` 
- 比较运算： `1>2` , `1>=2` , `3<4` , `3<=4` 


<br />布尔值往往用于程序流程的控制，如条件语句
```javascript
if (value) {
  ...
}else{
	...
} 
```
**但是问题来了，如何确定value的值是bool值？  ** <br />**如果value不是bool值咋办，怎么判断真假呢？  ** <br />JavaScript 预期某个位置应该是布尔值，会将该位置上现有的值自动转为布尔值。<br />除了`false`和下面五个值会被转为 `false` ，其他值都视为 `true` 。

- `undefined`
- `null`
- `0`
- `NaN` 
-  `''`或者 `""`  (空字符串)  

所以现在就知道哪些值是`false` ，哪些值是`true` 了！<br />
<br />感谢观看到这里，本文参考：<br />[阮一峰. 网道：JavaScript 语言入门教程](https://wangdoc.com/javascript/types/index.html)<br />
<br />

