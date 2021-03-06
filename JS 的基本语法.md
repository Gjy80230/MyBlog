# JS 的基本语法

## 什么是语句和表达式
#### 语句（statement）
语句是为了完成某种任务而进行的操作，比如下面就是一行赋值语句。
```javascript
var a = 1 + 3;		
```
这条语句先用 `var` 命令，声明了变量 `a` ，然后将 `1 + 3` 的运算结果赋值给变量 `a` 。
#### 表达式（expression）
上面`1 + 3` 叫做表达式（expression），指一个为了得到返回值的计算式。
#### 区别

- 语句主要为了进行某种操作，一般情况下不需要返回值
- 表达式为了得到返回值，一定会返回一个值。
#### 关于分号
分号表示一条语句的结束，JavaScript 允许省略语句末尾的分号。除了一些特殊的语句必须要有分号之外，一般都是可以省略的。
## 标识符（identifier）
标识符指的是用来识别各种值的合法名称。
#### 命名规则

- 第一个字符，可以是任意 Unicode 字母（包括英文字母和其他语言的字母），以及美元符 `$` 和下划线 `_` 。 
- 第二个字符及后面的字符，除了 Unicode 字母、美元符和下划线，还可以用数字 `0-9` 。 
```javascript
var _ws = 1
var $ee111 = 233
var 中文 = 399		//中文也是可以用作变量的
```
## 条件语句
#### if...else 语句 
**语法** 
```javascript
if (表达式){
  语句1;
}else{
	语句2;
}
```
`if` 先判断一个表达式的布尔值真伪，为 `true` 执行语句1，否则执行语句2。<br />当然， `else` 以及后面部分都去掉可以当成 `if` 语句来用。大括号 `{}`也可以省略，但是不建议你这么做。  <br />**例子1** 
```javascript
var a = 2
if (a = 1){
  console.log('a是1')
}else{
  console.log('a不是1')
}
```
上面代码表达式里面用的是赋值运算符 `=`，而不是相等运算符 `==` 或者严格相等运算符 `===` ，表达式的值永远都是 `true` 。<br />建议使用严格相等运算符 `===` ，或者是把常量 `1` 写在运算符的左边，如果写错就会提示你报错的。  <br />**例子2** 
```javascript
var a = 1
if(a === 2)
  console.log('a')
  console.log('a等于2')
```
上面的代码 `if` 会管到后面的第一句，相当于是这样的
```javascript
var a = 1
if(a === 2){
  console.log('a')
}
console.log('a等于2')
```
于是打出 `a等于2` 。<br />

## 循环语句
#### while 循环 
`While` 循环语句包括一个循环条件和一段代码块，只要条件为真，就不断循环执行代码块。<br />其中循环条件是一个表达式，必须放在圆括号中。代码块部分，如果只有一条语句，可以省略大括号，不过不建议你这么做，一般我们还是写上大括号。<br />**语法** 
```javascript
while (条件) {
  语句;
}
```
**例子** 
```javascript
var i = 0;

while (i < 10) {
  console.log('i 当前为：' + i);
  i = i + 1;
}
```
上面的代码将循环10次，直到 `i` 等于10为止
#### for 循环 
`for` 循环语句是循环命令的另一种形式，可以指定循环的起点、终点和终止条件。<br />**语法** 
```javascript
for (初始化表达式; 条件; 递增表达式) {
  语句
}
```
`for` 循环语句后面的括号里面，有三个表达式。

- 初始化表达式（initialize）：确定循环变量的初始值，只在循环开始时执行一次。 
- 条件表达式（test）：每轮循环开始时，都要执行这个条件表达式，只有值为真，才继续进行循环。 
- 递增表达式（increment）：每轮循环的最后一个操作，通常用来递增循环变量。 

**例子** 
```javascript
var x = 3; 
for (var i = 0; i < x; i++) {   
  console.log(i); 
} 
// 0 
// 1 
// 2
```
上面代码中，初始化表达式是 `var i = 0` ，即初始化一个变量 `i` ；测试表达式是 `i < x` ，即只要 `i` 小于 `x` ，就会执行循环；递增表达式是 `i++` ，即每次循环结束后， `i` 增大 `1` 。 
## break语句和continue语句
break语句和continue语句都具有跳转作用，可以让代码不按既有的顺序执行。
#### break
break语句用于跳出当前的所有循环。
```javascript
for(var i=0; i<10; i++){
	if(i === 6){
  	break;
  }
}
```
上面代码会循环10次，但是会在 `i` 为 6 的时候跳出循环。
#### continue
continue语句用于立即终止本次循环（只限单层），返回循环结构的头部，开始下一轮循环。
```javascript
for(var i=0; i<10; i++){
	if(i%2 === 1){
  	continue;
  }else{
    console.log(i)
  }
}
//0
//2
//4
//6
//8
```
上面代码在 `i` 为偶数时，才会输出`i`的值。如果`i`为奇数，则直接进入下一轮循环。
## 标签（label）
JavaScript 语言允许，语句的前面有标签（label），相当于定位符，用于跳转到程序的任意位置，标签的格式如下。
```javascript
label:
  语句
```
标签可以是任意的标识符，但不能是保留字，语句部分可以是任意语句。<br />**例子1** 
```javascript
{
  a:1;
}
//1
```
上面代码中标签是 `a` ，它并不是一个对象，只是会返回 `1` 。<br />**例子2** 
```javascript
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) break top;
      console.log('i=' + i + ', j=' + j);
    }
  }
// i=0, j=0
// i=0, j=1
// i=0, j=2
// i=1, j=0
```
上面代码为一个双重循环区块， `break` 命令后面加上了 `top` 标签（注意，`top`不用加引号），满足条件时，直接跳出双层循环。如果`break`语句后面不使用标签，则只能跳出内层循环，进入下一次的外层循环。<br />
<br />**感谢观看，本文参考：** <br />[阮一峰. 网道：JavaScript 语言入门教程](https://wangdoc.com/javascript/basic/grammar.html#%E5%BE%AA%E7%8E%AF%E8%AF%AD%E5%8F%A5)<br />
<br />
<br />
<br />
<br />
<br />

