# JS 对象基础用法

### 1. 对象（Object）
定义：对象就是一组“键值对”（key-value）的集合，是一种无序的复合数据集合。  
#### 1.1 声明对象的两种方法
```javascript
let obj={
  name:'gene',
  age:18
}  			
//上面是简单写法,还有下面这种写法
let obj=new Object({
   name:'gene',
   age:18
})   
//正规写法
```
上面两种写法中定义了一个对象，它被赋值给变量obj，所以变量obj就指向一个对象。该对象内部包含两个键值对（又称为两个“成员”），第一个键值对是 `'name':'gene'` ，其中`name`是“键名”（成员的名称，也叫key），字符串`gene`是“键值”（成员的值，也叫value）。键名与键值之间用冒号分隔。第二个键值对是 `'age':18` ，`age`是键名，`18`是键值。两个键值对之间用逗号分隔。  
#### 1.2 键名
对象的所有键名都是字符串，不是标识符，可以包含任意字符。引号可省略，但是省略之后就只能按照标识符的规则来写。**就算引号省略了，键名也还是字符串** 。上面的代码也可以写成下面这样。  
```javascript
let obj={
  'name':'gene',
  'age':18
}  
```
#### 1.3 属性名
对象的每一个键名又称为“属性名”（property），所有属性名会自动变成字符串。 此外，它的“键值”可以是任何数据类型。  
```javascript
let obj={
    1:'a',
    3.2:'b',
    1e2:true,
    1e-2:true,
    .234:true,
    0XFF:true
}

Object.keys（obj）
//["1"，"100"，"255"，"3.2"，"0.01"，"0.234"]
```
上面代码中，对象 `obj` 的所有属性名虽然看上去像数值，实际上都被自动转成了字符串。  <br />  <br />如果属性名不符合标识名的条件，比如第一个字符为数字，或者含有空格或运算符且也不是纯数字，则必须加上引号，否则会报错。  <br />
#### 1.4 方法
定义：如果一个属性的值为函数，通常把这个属性称为“方法”，它可以像函数那样调用。  
```javascript
var obj = {
  p: function (x) {
    console.log(x)
  }
}

obj.p(1) // 1
```
上面代码中，对象 `obj` 的属性 `p` ，就指向一个函数。  <br />

#### 1.5 引用
如果不同的变量名指向同一个对象，那么它们都是这个对象的引用，也就是说指向同一个内存地址。修改其中一个变量，会影响到其他所有变量。  
```javascript
var o1 = {}
var o2 = o1

o1.a = 1
o2.a // 1

o2.b = 2
o1.b // 2
```
上面代码中， `o1` 和 `o2` 指向同一个对象，因此为其中任何一个变量添加属性，另一个变量都可以读写该属性。  
```javascript
var o1 = {}
var o2 = o1

o1 = 1;
o2 // {}
```
上面代码中， `o1` 和 `o2` 指向同一个对象，然后 `o1` 的值变为 `1` ，这时不会对 `o2` 产生影响， `o2` 还是指向原来的那个对象。    <br />但是，这种引用只局限于对象，如果两个变量指向同一个原始类型的值。那么，变量这时都是值的拷贝。  
```javascript
var x = 1
var y = x

x = 2
y // 1
```
上面的代码中，当 `x` 的值发生变化后， `y` 的值并不变，这就表示 `y` 和 `x` 并不是指向同一个内存地址。  <br />如果属性的值还是一个对象，就形成了链式引用。  

### 2. 属性的操作
#### 2.1 删除对象的属性
`delete`  命令用于删除对象的属性，删除成功后返回 `true` 。   
```javascript
var obj = { p: 1 }
Object.keys(obj) 		// ["p"]

delete obj.p 		// true
obj.p		 // undefined
Object.keys(obj) 	// []
```
删除`p` 属性后，再读取 `p` 属性就会返回 `undefined` ，而且 `Object.keys` 方法的返回值也不再包括该属性。    

但是注意，删除一个不存在的属性， `delete` 不报错，而且返回 `true` 。  
```javascript
var obj = {}
delete obj.p // true

```
上面代码中，对象 `obj` 并没有 `p` 属性，但是 `delete` 命令照样返回 `true` 。因此，不能根据 `delete` 命令的结果，认定某个属性是存在的。  <br />
#### 2.2 查看对象的属性
`in` 运算符用于检查对象是否包含某个属性（注意，检查的是键名，不是键值），如果包含就返回 `true` ，否则返回 `false` 。它的左边是一个字符串，表示属性名，右边是一个对象。  
```javascript
var obj = { name: 'gene' }
'name' in obj // true
'toString' in obj // true
```
`in` 运算符的一个问题是，它不能识别哪些属性是对象自身的，哪些属性是继承的。就像上面代码中，对象obj本身并没有 `toString` 属性，但是 `in` 运算符会返回 `true` ，因为这个属性是继承的。    

这时，可以使用对象的 `hasOwnProperty` 方法判断一下，是否为对象自身的属性，**这也是`in` 运算符和`hasOwnProperty` 方法它们之间的区别**。  
```javascript
var obj = {}
if ('toString' in obj) {
  console.log(obj.hasOwnProperty('toString')) // false
}
```
除了使用上面的方法，还可以用 `Object.keys` 方法，用于查看一个对象本身的所有属性。  
```javascript
var obj = {
  key1: 1,
  key2: 2
}

Object.keys(obj)
// ['key1', 'key2']
```
还可以用 `console.dir` 方法，用于查看所有属性（自身+继承）。  
```javascript
var obj = {
  key1: 1,
  key2: 2
}

console.dir(obj)
//	Object {
//		key1: 1,
//  	key2: 2,
//		obj.__proto__
//	}
//等同于obj 打出整个对象  
```
#### 2.3读取对象的属性
读取有两种方法，一种是使用点运算符，还有一种是使用方括号运算符。  
```javascript
var obj = { 
  name: 'gene' 
}

obj.name	//'gene'
obj['name']	//'gene' 
```
请注意，如果使用方括号运算符，键名必须放在引号里面，否则会被当作变量处理。  
```javascript
var foo = 'bar'

var obj = {
	foo : 1,
  bar : 2
}

obj['foo']	//1
obj[foo]	//2	等同于obj['bar']
```
ES6新语法，可以把 `[]` 中的变量作为属性。不加 `[]` 的属性名会自动变成字符串，加了 `[]` 则会当做变量求值。值如果不是字符串，则会自动变成字符串。对象的属性之间用逗号分隔，最后一个属性后面可以加逗号，也可以不加。  
```javascript
var obj = {
  0.7: 'Hello World'
}

obj['0.7'] // "Hello World"
obj[0.7] // "Hello World"
```
方括号运算符内部还可以使用表达式。  
```javascript
obj['na' + 'me']
obj[3 + 3] 	
```
注意，数值键名不能使用点运算符（因为会被当成小数点），只能使用方括号运算符。  
#### 2.4 属性的赋值
点运算符和方括号运算符，不仅可以用来读取值，还可以用来赋值。
```javascript
var obj = {}

obj.name = 'Hello'
obj['age'] = '18'	
```
JavaScript 允许属性的“后绑定”，也就是说，你可以在任意时刻新增属性，没必要在定义对象的时候，就定义好属性。
```javascript
var obj = {key:1}

//等同于
var obj = {}
obj.key = 1
```
不过上面的方法只能一个一个去赋值，当你要批量赋值的时候，可以使用 `Object.assign` 方法
```javascript
var obj = {name:'gene'}
obj.age = 18
obj.gender='man'

//等同于
Object.assign(obj, {age: 18, gender: 'man'})
```
<br />感谢观看到这里，本文参考：  <br />[阮一峰. 网道：JavaScript 语言入门教程](https://wangdoc.com/javascript/types/object.html)

