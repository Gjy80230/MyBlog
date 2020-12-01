# JavaScript诞生

<a name="H7EfG"></a>
### 创造之初
1994年[Netscape公司](https://baike.baidu.com/item/%E7%BD%91%E6%99%AF/70176?fromtitle=netscape&fromid=2778944)（网景）发明了Navigator浏览器，由于这是历史上第一个比较成熟的网络浏览器，轰动一时。但是，这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。当时的交互是让服务器来做，这样会非常的浪费资源和时间。<br />次年也就是1995年，刚进公司的Brendan Eich（JS之父）临危受命，被公司要求给浏览器加入一个脚本功能，并且当时因为网景与Sun公司合作，网景的管理层希望它看起来像Java，但是比Java简单以此来蹭Java的流量，因此取名为JavaScript。<br />Brendan花了十天设计了JS的最初版本（不是实现），但由于设计时间太短，一些细节考虑得不够严谨，导致后来很长一段时间，JavaScript写出来的程序混乱不堪。
<a name="eY4PQ"></a>
### 浏览器大战
1996年IE3发布，支持JScript（微软的JS）。至此浏览器大战开始，当时每家的脚本不太一样。之后网景向ECMA提交语言标准，由于版权问题JS语言的标准被命名为[ECMAScript](https://baike.baidu.com/item/ECMAScript%20/1889420) 。<br />但是，由于微软的Windows系统自带了IE浏览器，在市场上很快就超越了Navigator浏览器。网景陷入内忧外患，临死之前网景把浏览器开源了，也就是后来的Firefox（由Mozilla维护，[过程详情](https://www.bilibili.com/video/av15989846/) ），当时还没有一家商业公司会把自己的产品开源，所以造成了一定的轰动。但这也没能挽救网景，1998年11月美国在线收购了网景，在这之后Brendan成立了Mozilla。<br />时间到了2001年，IE 6随着WindowsXP系统一起发布。之后3年市场占有率达到了80%，由于IE 6的巨大成功，微软开始松懈。觉得再花费精力不值得，而且没有竞争对手，所以直接解散了IE 6的开发团队。同时IE 6不兼容W3C标准，并且不断爆出安全漏洞。让Firefox看到了机会，从微软的市场中分得了一杯羹。<br />Firefox的举动逐渐映入微软的眼帘，微软虽然重新组建了IE团队，但不是同一伙人，所以造成后来发布的IE 7/8一直问题不断。当时主流浏览器还是IE 6和Firefox，2010年以前因为盗版Windows XP在中国的风行，IE 6还是占据这很大的市场，同时也让前端开发者很头疼。
<a name="cvkbP"></a>
### Chrome的崛起
2004年谷歌雇用了一些Firefox和IE的开发者，经过多年的努力，2008年Chrome终于发布，迅速拿下1%的市场份额。<br />2011年Chrome份额才超过了Firefox。之后的2016年，Chrome全球份额达到62%。[Chrome到底有多快](https://www.bilibili.com/video/av3745910/)
<a name="GxhX8"></a>
### 移动市场的兴起
2010年一代神机[iPhone 4发布](https://www.bilibili.com/video/BV1Kb411t7ZP?from=search&seid=9059039301173211077)，智能手机的时代来临。同时因为新增加的手机网页，让当时不是专职写网页的后端程序员感到头疼，他们大部分并不知道手机上的网页要怎么写，于是[前端工程师](https://baike.baidu.com/item/%E5%89%8D%E7%AB%AF%E5%B7%A5%E7%A8%8B%E5%B8%88)这个职位也爆发了现象级的增长。<br />2011年Nokia看到这个局面，打算和微软联合起来，不过后来的事情大家都知道，Nokia手机业务完了。也就是说，手机上基本没有IE了。再加上2016年，淘宝天猫宣布不再支持IE 6、IE 7、IE 8，这让前端程序员表示欣喜若狂，终于不用兼容IE了。<br />移动市场的兴起，让中国前端摆脱IE十年的恐怖支配，从此前端极速发展。
<a name="1B27Y"></a>
### 标准发布
1997年6月第一版ECMAScript发布<br />1999年12月第三版发布，这个版本使用最广。第四版，没有第四版。<br />2009年12月第五版发布，增加了一些功能。至于为什么等了十年才更新了第五版，因为当时IE 6大火，导致停滞不前。<br />2015年6月第六版发布，新浏览器都支持这一版，这一年也是Chrome市场份额过半的时候。之后每年发布一版，版本号以年份命名（如现在就是ES2020）
<a name="NNwYe"></a>
#### JavaScript与ECMAScript的关系
ES是JS的标准，JS是浏览器的实现。标准往往是落后于浏览器的，先实现再写进标准。
<a name="RJWxT"></a>
#### JavaScript兴起
2004年愚人节，谷歌发布Gmail 在线网页，当时的人们认为网页只能用来看新闻和图片。Gmail的发布让用户和开发者眼前一亮，次年有一个叫Jesse的人将谷歌用到的技术命名为[AJAX](https://baike.baidu.com/item/ajax/8425)，从此前端技术正式出现。<br />在此之前的网页开发都是由后端和设计师完成，2006年jQuery发布，是目前最长寿的JS库。后来的十年，jQuery大发异彩，直到IE不行了，jQuery才稍微没有那么火。
<a name="rIYVd"></a>
#### 另一个战场
Chrome的执行JS的引擎叫做V8（V1-V7分别是不同语言的解析器）。<br />2009年Ryan基于V8创建了Node.js，次年Isaac基于Node.js写出了npm，现在你只要安装了Node.js就会自带npm，这样就可以让前端工程师在浏览器之外执行JS了，Node.js快速风靡。同年，TJ受Sinatra启发，发布了Express.js。从此前端工程师可以愉快地写后端应用了~~<br />以上就是JavaScript的部分历史，当然还有后面的很多技术没有提到（gulp、grunt、yeoman、requirejs、webpack、Angular、React、Vue等），感谢观看。<br />
<br />
<br />
<br />

