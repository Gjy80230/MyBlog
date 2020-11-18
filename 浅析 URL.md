# 浅析 URL

## URL 包含哪几部分，每部分分别有什么作用
李爵士发明了万维网（WWW=URL+HTTP+HTML），我们来说说其中的URL由哪几部分组成。
### IP
IP全称是Internet Protocol，直译就是网际互连协议。
#### IP的作用
它主要约定了两件事：

1. 如何定位一台设备
1. 如何封装报文，跟其他设备交流

只要你在互联网中，你就会至少有一个独特的IP。


#### 内网IP和外网IP
IP分为内网和外网IP，以路由器为界限。
#### 
#### 如何获取内外网IP

- 外网IP ：路由器连接上了电信的服务器，路由器就会有一个外网IP，它也是你在互联网中的地址，如 14.17.32.211 ，如果你重启了路由器，那么可能会重新分配一个IP给你，也就是说这个外网IP不是固定的**
- 内网IP：当你家里的设备连接上了路由器广播的wifi，那么家里的这些设备就是在内网IP了，路由会自动的给每个设备分配一个不同的IP，格式一般都是 192.168.xxx.xxx 



#### 内外网之间如何访问呢？

- 内网中的设备要访问外网，不能直接访问，需要通过路由器才能访问外网
- 同样的，外网中的设备可以互相访问。但是不能直接访问你的内网，也需要通过路由器
- 内网和外网是两个隔绝的空间，无法互通，唯一的联通点就是路由器，这也是路由器为什么被叫做 **网关** 



### 端口号
有了IP，我们还需要端口号。  
#### 定义
它是一台机器所能提供的服务，每一种服务代表一个号码，这个号码叫做端口号（port）。


#### 常用服务

- Http服务使用80端口
- Https服务使用443端口
- Ftp服务使用21端口

一共有65535个端口，我们只需要记住一些常用的就可以了，剩下的可以用到的时候[查表](https://zh.wikipedia.org/wiki/TCP/UDP%E7%AB%AF%E5%8F%A3%E5%88%97%E8%A1%A8#0.E5.88.B01023.E5.8F.B7.E7.AB.AF.E5.8F.A3) 。


#### 端口使用规则

- 0到1023（2的10次方减1）号端口是留给系统使用的
- 你只有拥有了管理员权限后，才能使用这1024个端口
- 其他端口可以给普通用户使用
- 比如http-server默认使用8080端口
- 一个端口如果被占用，你就只能换一个端口



#### 注意
默认端口是不会显示的，一般的网站使用HTTP、HTTPS协议，你需要知道的就是端口号前者为80端口，后者是443端口。

### 域名
#### 什么是域名
域名就是IP的别称。


#### ping命令的使用
我们可以使用ping命令，来ping下百度、QQ，看下结果：  
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605701126216-749d4862-1a55-4511-9340-e84dcc6cafaa.png#align=left&display=inline&height=149&margin=%5Bobject%20Object%5D&name=image.png&originHeight=192&originWidth=457&size=19752&status=done&style=none&width=354)![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605701187802-28b51ee3-d9db-40f0-b90a-7c4530ac1717.png#align=left&display=inline&height=149&margin=%5Bobject%20Object%5D&name=image.png&originHeight=192&originWidth=454&size=20263&status=done&style=none&width=352)  

可以看到，ping了网址之后，返回了对应的IP，但是如果我们分别同时去ping同一个网址那么有可能会返回不同的IP。

- 这是一种叫做负载均衡的网站策略，防止一台机器扛不住。一般是大公司会这么做。
- 一个IP可以对应不同域名，这个叫做共享主机，穷开发者会这么做



#### 路径
当你进入一个网站，想要看到不同的页面，除了可以直接跳转，还可以通过输入不同路径来实现。  
MDN网站下面的HTML和CSS这两个页面，可以看到对应请求页面的路径是不一样的。    
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605702972254-3b925f5d-f72b-461a-bc0a-603968965394.png#align=left&display=inline&height=122&margin=%5Bobject%20Object%5D&name=image.png&originHeight=122&originWidth=666&size=13660&status=done&style=none&width=666)![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605703002257-dc446d25-1931-4b7c-a064-28922342c15b.png#align=left&display=inline&height=117&margin=%5Bobject%20Object%5D&name=image.png&originHeight=121&originWidth=687&size=14344&status=done&style=none&width=662)
#### 查询参数
如果我们想要看到同一个页面的不同内容，只需要改变查询参数就可以实现。
如百度的查询参数，在"?"后面输入wd=20，就会出现20的搜索页面。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605703364247-a52a4739-3a3a-4df4-8d55-b8059639ffd7.png#align=left&display=inline&height=266&margin=%5Bobject%20Object%5D&name=image.png&originHeight=266&originWidth=531&size=50989&status=done&style=none&width=531)
#### 锚点
锚点可以在同一内容中，不同的位置。
如MDN网站下面的CSS页面内容，当你要看参考书这一内容，只需要在网址后面加个 #参考书 即可
### DNS 
域名是怎么和IP对应起来的呢？--通过DNS。


#### DNS 的作用
当你输入一个网址，你的Chrome 浏览器会向电信/联通提供的DNS 服务器询问这个网址对应什么IP。电信/联通会回答一个IP并返回。然后Chrome才会向对应IP的80/443端口发送请求，内容是查看该网页的首页，发送index.html，index.html又会请求CSS、JS文件  
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605702003928-7dc7d456-9a51-4a5b-a976-ad16497d212d.png#align=left&display=inline&height=142&margin=%5Bobject%20Object%5D&name=image.png&originHeight=142&originWidth=560&size=16167&status=done&style=none&width=560)
#### 域名级别

- 同一域名

www.baidu.com 和 baidu.com是同一个域名吗？--不是

- 他们的关系
   - com是顶级域名
   - baidu.com 是二级域名（俗称一级域名）
   - www.baidu.com是三级域名（俗称二级）
   - 他们是父子关系
#### nslookup 命令
在上面输入一个网站的过程中，nslookup用于向运营商询问网址对应的IP。可以看到下面的哔哩哔哩对应了5个IP  

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605705473004-854c5039-db0d-45fe-b760-cc4981003b21.png#align=left&display=inline&height=219&margin=%5Bobject%20Object%5D&name=image.png&originHeight=219&originWidth=249&size=10090&status=done&style=none&width=249)

### 协议
万维网中用得最广的协议就是 HTTP协议 ，它是一种基于TCP和IP的传输协议。


#### CURL命令
我们可以用curl命令来发送HTTP请求
```
curl -v http://baidu.com 
curl -s-v -- https://www.baidu.com	

//返回对应的网页内容
```


#### 过程
url会被curl工具重写，先请求DNS获得IP。进行TCP连接，TCP连接成功后，开始发送HTTP请求。请求内容看一下
响应内容看一下，响应结束后，最后关闭TCP连接，再真正结束。


我们请求了百度的旧地址，它让我们访问带www的地址。  
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605706199129-d9516a90-8ee2-4186-b60f-8eeb83e87c19.png#align=left&display=inline&height=65&margin=%5Bobject%20Object%5D&name=image.png&originHeight=65&originWidth=542&size=6405&status=done&style=none&width=542)  
我们又用curl -s-v -- [https://www.baidu.com](https://www.baidu.com)发送了请求，这次百度返回了请求和响应的完整网页  

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605706460120-2e69d0d4-634d-4850-ade5-07cfbdf00fc9.png#align=left&display=inline&height=84&margin=%5Bobject%20Object%5D&name=image.png&originHeight=84&originWidth=262&size=3614&status=done&style=none&width=262)  
上图是请求的内容  

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2506859/1605706620154-b6ee8e61-abc8-422b-9e6e-2255a81f93fe.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&name=image.png&originHeight=226&originWidth=640&size=24619&status=done&style=none&width=545)  
上图是响应的内容  

#### HTTP的作用
它规定了请求的格式和响应的格式怎么写。
上面百度返回的两张图，分别介绍了请求的格式和响应的格式。

### 总结
URL=协议+域名或IP+端口号+路径+查询字符串+锚点
