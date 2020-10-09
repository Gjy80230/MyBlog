## HTML 入门笔记 1

最近了解了 HTML，所以来记录一下，可以日后复习。

### HTML 是谁发明的

HTML 当然是[李爵士(Timothy John Berners-Lee)](https://zh.wikipedia.org/zh/%E8%92%82%E5%A7%86%C2%B7%E4%BC%AF%E7%BA%B3%E6%96%AF-%E6%9D%8E)发明的。同时他还发明了万维网（World Wide Web）、HTTP 和 URL。

### HTML 首先应该写什么

我们写一个 HTML 页面，一般都是会先写以下的内容：

```html
<!DOCTYPE html>
<!--这是文档类型，表示html -->
<html lang="en">
  <!--这是用什么语言，en为英文，改为zh-CN -->
  <!--html标签有两个子元素：head和body -->
  <head>
    <!--head标签除了有meta、title标签，一般还会有script、style标签 -->
    <meta charset="UTF-8" />
    <!--这是文件的编码方式-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!--表示禁用缩放，兼容手机 -->
    <title>My Page</title>
    <!--浏览器打开时，网页的标题-->
  </head>
  <!--下面就是网页的内容了-->
  <body></body>
</html>
```

### 常用表示的章节标签

我们来看下 body 标签里面有什么
**标题 h1~h6**
用于表示标题、副标题。
**章节 section**
用于表示章节，也可以 section 中套 section。
**文章 article**

**段落 p**
当需要输入文本内容的时候，这个标签就体现了它的作用，哪怕是一句话，也可以用 p 标签。

**头部 header**
有时候需要加点广告之类的，可以用这个标签。

**脚部 footer**
一般用于版权声明或者其他声明，像我们浏览的很多网站都是有声明的，就是用的这个标签。
![版权声明](./pictures/HTML入门笔记/banquan1.png)

**主要内容 main**
当我们的结构有头部、有尾部，我们可以把主要的内容标记出来。
**旁支内容 aside**
一般用于写导航，或者次要的内容。
**划分 div**
一般用于划分网页的结构。

### 全局属性有哪些

**class**

- 给一个标签写一个类,一般的使用方法是先在标签中写一个 class，再给 class 一个名字，之后在 style 标签中
- 引用它并给它相应的样式。
  给 class 样式有两种写法，不过第一种写法当有 2 个以上 class 的时候，必须全部都写上去。而第二种只需要写其中一个就可以了
  ![class的写法](./pictures/HTML入门笔记/class1.png)
  ![class的引用](./pictures/HTML入门笔记/class2.png)
  上图，两种写法都是可以的，不过推荐下面的写法，比较方便。

**contenteditable**
可以在网页中编辑任何一个元素。

**hidden**
当你在某个元素写上这个属性，这个元素将会在网页中消失。

**id**

- 不到万不得已，千万不要用。id 是用来表示全局唯一的标签，但是 id 的全局唯一性没有保障，就算有两个重复的 id，HTML 也不会提示我写错了。
- 使用方法：
  1. css：一般给元素写上 id="xx"，在 style 标签中给它添加样式时用#xx{style}引用。
  2. js：用于获取 id。
  3. 不要是已经存在的关键字。如 window 所有的属性

**style**
用于给网页添加样式的标签。

**tabindex**
当元素有这个属性时，可以用 tab 键进行交互。

- tabindex=1；也就是正数，表示可以访问。
- tabindex 可以是 0，表示最后才被 tab 访问。
- tabindex 可以是负数，表示不可被 tab 访问。

**title**
当你省略了之后，title 属性放入完整的内容，就可以通过鼠标悬浮在省略的文字上显示出来。
![text](./pictures/HTML入门笔记/text1.png)

### 常用的内容标签
