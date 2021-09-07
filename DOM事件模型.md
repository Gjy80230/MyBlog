<a name="EdaNH"></a>
### 标准的发布
2002年，W3C发布了[新的事件触发机制](https://www.w3.org/TR/DOM-Level-2-Events/)。<br />不过在这之前Netscape (网景)和 IE在这件事情互不相让。<br />网景认为，事件发生后是由外向内传播的。而IE跟网景是相反的，主张事件发生后是由内向外传播。<br />两家主张的事件标准如下（这里以为点击事件为例）
```javascript
Node.attachEvent('onclick', fn)		//IE的标准，也就是后来的冒泡
Node.addEventListener('click', fn)	//网景的标准，也就是后来的捕获
```
那个时候的开发者也是非常头疼的，在ie下面要用ie的标准，在网景的浏览器则要用网景的标准。<br />于是W3C让两家和谈，最后在2002年发布了新标准。
<a name="NQrU5"></a>
### 事件传播
W3C把网景和IE两家的标准整合成一起，规定浏览器应该同时支持两种调用顺序，它分为三个阶段。

- 第一阶段：从`window`对象传导到目标节点（上层传到底层），称为“捕获阶段”。
- 第二阶段：在目标节点上触发，称为“目标阶段”。
- 第三阶段：从目标节点传导回window对象（从底层传回上层），称为“冒泡阶段”。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/2506859/1631026094931-53215ca4-28c5-4b2f-ac08-a4346894c72a.png#clientId=u0c6cf31a-1042-4&from=paste&height=526&id=u56341aef&margin=%5Bobject%20Object%5D&name=image.png&originHeight=706&originWidth=673&originalType=url&ratio=1&size=144583&status=done&style=shadow&taskId=u03100115-ceae-4615-a15d-ce69b733bf4&width=501)<br />如上图，最底层的`td`标签被点击了，就会先问`Window`有没有函数要执行，如没有就会一直问下去直到`td`标签。<br />这个过程走完之后，就来到了目标阶段，可以选择是否冒泡。如选择冒泡则从`td`标签一直冒到`Window`上。<br />​<br />
<a name="gbaPx"></a>
### 事件监听
W3C发布的新标准，规定了统一使用`EventTarget.addEventListener()`给当前节点绑定一个特定事件的监听函数，一旦这个事件发生，就会执行监听函数。<br />​

**语法**
```javascript
target.addEventListener(type, listener[, useCapture]);
```
**参数**​

- `type`：事件名称，大小写敏感。
- `listener`：监听函数。事件发生时，会调用该监听函数。
- `useCapture`：布尔值，如果设为`true`，表示监听函数将在捕获阶段（capture）触发。该参数可选，如不写则默认值为`false`，监听函数会在冒泡阶段被触发。
```javascript
function fn(){
  console.log('hello')
}
        
div.addEventListener('click', fn)
```
上面的代码给`div`的`addEventListener`方法绑定了一个`click`事件的监听函数`fn()`。该函数在冒泡阶段触发。<br />**​**

**优点**<br />`EventTarget.addEventListener`是推荐的指定监听函数的方法。<br />它有如下优点：

- 同一个事件可以添加多个监听函数。
- 能够指定在哪个阶段（捕获阶段还是冒泡阶段）触发监听函数。
<a name="z0y6V"></a>
### 取消冒泡
捕获阶段是不可以取消的，只有冒泡阶段才能取消，`stopPropagation方法`阻止事件在 DOM 中继续传播，防止再触发定义在别的节点上的监听函数，但是**不包括在当前节点上的事件监听函数**。
```javascript
function fn(e){
	e.stopProgation()
}

div.addEventListener('click', fn)
```
上面代码，`click`事件将不会冒泡到`div`节点的父节点。
<a name="PaUx4"></a>
### 事件委托
我们知道了监听函数的定义，但是如果遇到了一次性要给几十个，甚至几百个元素定义监听事件呢？<br />别慌，我们可以把监听事件定义到它们的父元素，由父元素的监听函数统一处理多个子元素的事件。<br />这种方法叫做**事件委托**。
```javascript
let ul = document.querySelector('ul')

ul.addEventListener('click', (e)=>{
	let t = e.target
  if(t.tagName.toLowerCase() === 'li'){
  		console.log(t.textContent + '被点击了')
  }
})
```
上面代码中，`click`事件的监听函数定义在`<ul>`节点，但是实际上，它处理的是子节点`<li>`的`click`事件。<br />​

**优点**<br />像上面事件委托的例子，只要定义一个监听函数，就能处理多个子节点的事件，而不用在每个<li>节点上定义监听函数。这样做的好处是能节省监听函数的数量，内存也不会太多。<br />它还有一个好处，就是能监听目前不存在而以后会被添加的子节点，这个叫**监听动态元素。**
```javascript
setTimeout(()=>{
  let button = document.createElement('button')
  button.textContent = 'click 1'
  div.appendChild(button)
},1000)

div.addEventListener('click',(e)=>{
  let t = e.target
  if(t.tagName.toLowerCase() === 'button'){
    console.log(t.textContent + '被点击了')
  }
})
```
上面代码中，我们直接监听父元素`div`的点击事件，这样它一添加子元素监听函数依然有效。<br />
<br />以上就是本次**DOM事件模型**的全部内容了，感谢观看。<br />本文参考：[阮一峰. 网道：事件](https://wangdoc.com/javascript/events/index.html)<br />​<br />
