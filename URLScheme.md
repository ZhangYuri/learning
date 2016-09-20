##浏览器自定义协议
####一、是什么
正如http://baidu.com，整个网址称之为url，http部分我们称之为scheme，通过这样的链接，我们可以打开相应的网页；与此相似的，也有类似的协议可以打开对应的app，比如weixin://可以打开微信，weixin://dl/moments则是微信中的朋友圈。不过这样的协议是app的开发者在开发的时候自己定义，比如我们可以自定义myapp://*，相应的，如果他没有定义，我们就没有办法在网页或者其它app中调起它了。
####二、常见的例子
#####1.系统级：
	
- tel://——打电话
- sms://——发短信
- mailto://——发邮件

#####2.应用级：

- mqq://——QQ
- weixin://——微信
- taobao://——淘宝
- sinaweibo://——微博

#####3.一些已知URLScheme汇总:
<a href="http://www.zhihu.com/question/19907735">点我</a>，
<a href="https://gist.github.com/genadyo/295a5e8f0d743f57137f">点我</a>，<a href="http://wiki.akosma.com/IPhone_URL_Schemes">点我</a>。
	
####三、在浏览器中如何使用
#####1.常用：
最常用的做法就是直接使用`<a>`标签：

	<a href="myapp://">Open my app</a>
	<a href="weixin://">打开微信</a>
#####2.不常用
自定义协议，不像网页的URL，网页和网址都是一一对应的关系，而在app中，由于URLScheme并没有一个统一的标准，这些协议就可能出现多对多点情况，即一个app可以定义多个scheme，而一个scheme可能对应多个应用，这就给我们的使用造成了一些麻烦。

其实对于自定义协议的使用远不止打开应用这么简单的操作，比如，当我们想调起字典的时候，可以在地址中加入参数，去读取剪切板clipboard，也可以在点击链接的时候让你进行一些输入操作，甚至可以设置回调地址。

但是由于前面提到的原因，它并没有一个统一标准，能不能实现，全凭app自己有没有设置这些功能，所以这里没办法给出一个放之四海皆准的用法，能不能用，只能具体问题具体分析了，放一个<a href="http://sspai.com/31500#04">参考网站</a>，里面有些用法，可作参考，然而里面用来举例的app我基本没用过，而我们常用的那些app支不支持，以后有机会一一试过才知道。

####四、在HybridApp中如何自定义Scheme
开门见山，有一个Cordova插件——<a href="https://github.com/EddyVerbruggen/Custom-URL-scheme">cordova-plugin-customurlscheme</a>。

详细用法见<a href="https://github.com/EddyVerbruggen/Custom-URL-scheme">官网</a>。
贴一个<a href="https://developer.android.com/training/basics/intents/filters.html">android原生</a>开发作为辅助资料。


