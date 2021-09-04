<a name="FT8h0"></a>
### jQuery的核心思想
> 用选择器来获取元素，但是不返回这些元素，而是返回一个可以操作的jQuery对象。

<a name="gDOnq"></a>
### jQuery如何获取元素
我们需要将操作的元素放入`jQuery()`函数，然后得到被选中的元素。<br />当然，如果你觉得`jQuery`太长了，你也可以把`jQuery`简写为`$`。
```javascript
let div = jQuery('.test')
//jQuery可以简写为$.
let div = $('.test')
```
除了上面的获取方式，还有以下获取方式。
```javascript
$("*")  //选择所有元素.
$("#myDiv") //选择ID为myDiv的元素.
$('div:first')  //选择第一个div元素.
$(":button")  //选择所有按钮元素和类型为按钮的元素.
```
<a name="xjvYK"></a>
### jQuery 的链式操作是怎样的
选中元素以后可以对它进行一系列操作，并且这些操作是连贯的，犹如链条，称为链式操作。
```javascript
$('.test').find('li').eq(2).title('jQuery')
```
我们来分解下。
```javascript
$('.test')  //选择class为test的元素.
  .find('li') //找到里面的li元素.
  .eq(2)  //选择第3个li元素.
  .text('jQuery') //把它的文本内容改为jQuery.
```
这是jQuery最令人惊艳的一个特点，它获取到元素之后的每一步操作，返回的都是一个jQuery对象，而且这些操作还能连在一起。<br />
<br />除此之外，jQuery还提供了`end()`方法，可以让返回的jQuery对象后退一步。
```javascript
$('.test')
  .find('li')
  .eq(2)
  .text('jQuery')
  .end()  //退回到选中所有li元素的那一步.
  .eq(1)  //选中第二个li元素.
  .text('hello')  //把它的文本内容改为hello.
```
<a name="gjHQg"></a>
### jQuery 如何创建元素
创建新元素非常方便，只需要把新元素直接放在jQuery构造函数后面就可以了。<br />用`append`方法给`class="test"`的元素添加一个p元素
```javascript
$('.test').append('<p>这是一段插入文本</p>')		
```
用`appendTo`方法给`class="parent"`的元素添加一个span元素
```javascript
$('<span>没什么特别的</span>').appendTo('.parent') 
```
append和appendTo两种方法功能相同，主要的不同是语法——内容和目标的位置不同。对于`append`方法, 选择表达式在函数的前面，参数是将要插入的内容。对于`appendTo`方法则刚好相反，内容在方法前面，无论是一个选择器表达式或创建作为标记上的标记，它都将被插入到目标容器的末尾。<br />

<a name="gZbHJ"></a>
### jQuery 如何移动元素
> jQuery也提供了在Dom树中移动元素的方法。

在元素后面插入另一个元素，我们可以用下面两种方法。
```javascript
$('div').after($('p'))
$('p').insertAfter($('div'))
```
同样，在元素前面插入另一个元素，我们可以用下面两种方法。
```javascript
$('div').before($('p'))
$('p').insertBefore($('div'))
```
以上的每组两种方法，效果都是一样的。除了操作元素的不同，还有一个很重要的差别，那就是返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素。你可以根据情况，来选择使用。<br />​<br />
<a name="qYewY"></a>
### jQuery 如何修改元素的属性
```javascript
$("p").addClass("myClass"); //给p元素添加class值为myClass
$('li').attr('title', '列表项');  //把li元素的title值改为"列表项"
$("div").text('这是一段文字') //把div的text值改为"这是一段文字"
$('input').val('默认文字')  //把文本框的值改为传入的参数值

```
<a name="xiY4b"></a>
### 小结
当然，上面这些只是jQuery的一部分。<br />jQuery用到的设计模式，除了它的核心思想，还有其他超越那个时代的设计模式，到现在还在被使用。

- 它虽然构造出了jQuery函数，但是它不是严格意义上的构造函数，且不用`new`关键字。
- jQuery的参数支持多种类型以及参数的个数，这个叫做**重载**。
- jQuery根据不同的浏览器来决定使用不同的操作，这个叫做**适配器。**


<br />感谢观看到这里，本文参考：  <br />[阮一峰：jQuery设计思想](http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html)<br />[jQuery API 中文文档](https://www.jquery123.com/)​
