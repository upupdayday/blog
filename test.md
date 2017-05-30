<meta http-equiv="Content-Type" content="text/html; charset=utf-8">

从URL输入到页面实现

简单来说，这是一个数据请求和展示的过程。而这个过程可以划分为以下几个步骤：

##输入URL

通过输入URL，例如“<http://www.baidu.com>”，用户说明了请求数据使用的协议——http，以及要访问的数据的网络位置——www.baidu.com，百度的域名。
网络地址可以使用域名或者IP，而使用域名则便于记忆和识别

##域名解析

当网址完成输入后，浏览器会逐级来查找域名对应的IP地址，顺序如下：
1. 浏览器缓存中查找——浏览器会缓存DNS记录一段时间；
2. 系统缓存 -——从 Hosts 文件查找是否有该域名和对应 IP；
3. 路由器缓存 —— 一般路由器也会缓存域名信息；
4. 请求上级DNS服务器——比如到运营商的DNS中查找；
5. 如果都没有找到，则向根域名服务器查找域名对应 IP，根域名服务器把请求转发到下一级，直到找到 IP；

##服务器处理

当浏览器完成域名解析获得了IP地址后，想服务器发送数据请求。
服务器接收到用户的请求后，进行交给相应的网站代码进行处理，网站代码运行得到结果后，由服务器反馈给用户。
示意图如下：
![](http://upload-images.jianshu.io/upload_images/6073413-637d7d1c7e02fa30.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
图片引用自[“从URL输入到页面展现by若愚@饥人谷”](http://book.jirengu.com/jrg-team/frontend-knowledge-ppt/www/%E5%89%8D%E7%AB%AF%E5%85%A5%E9%97%A8-%E4%BB%8E%20URL%E8%BE%93%E5%85%A5%E5%88%B0%E9%A1%B5%E9%9D%A2%E5%B1%95%E7%8E%B0.html#/)

##网站处理流程

网站的代码主要分为三部分：MVC 模型(model)-视图(view)-控制器(controller)，如下所示：
![](http://upload-images.jianshu.io/upload_images/6073413-f7bb0f655c8da170.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
图片引用自[“从URL输入到页面展现by若愚@饥人谷”](http://book.jirengu.com/jrg-team/frontend-knowledge-ppt/www/%E5%89%8D%E7%AB%AF%E5%85%A5%E9%97%A8-%E4%BB%8E%20URL%E8%BE%93%E5%85%A5%E5%88%B0%E9%A1%B5%E9%9D%A2%E5%B1%95%E7%8E%B0.html#/)

- 网站代码首先对请求进行路由匹配；
- 控制器从模型和数据库中查找用户数据；
- 控制器将数据应用于模板，组合成HTML，发还给浏览器，给用户看到页面

##浏览器处理

- 浏览器得到数据后，解析HTML字符串；
- 解析到link标签后，重新发送请求获取css;
- 解析到script标签后，发送请求获取js代码，并执行；
- 解析到img标签后，发送请求获取图片资源；

根据HTML和CSS计算，得到渲染树，绘制到屏幕上
