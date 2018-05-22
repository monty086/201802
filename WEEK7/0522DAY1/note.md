1.职业规划上的一点建议
 “开放分享”
 A:写一个属于自己的博客
  把自己的学习笔记以及到其他文章中去学习借鉴，然后把文章和学习感想发表出来...
 B:经常参加圈内的技术交流分享
 C:打造自己的自媒体
 ...

2.搭建自己的博客
 A:可以基于第三方平台搭建
 B:基于gitHub发布页面(HEXO)
 C:自己创建博客项目，并且购买域名和服务器进行发布推广

  ->开发项目（项目代码在自己的本地）
  ->项目发布
    1）需要一台服务器 （万网->被阿里云收购了）
       虚拟云服务器 / 独立主机
       购买服务器成功后会有一个外网的IP地址（外网IP：任何用户通过这个IP地址都可以访问到你的服务器）

    2）需要一个域名
       .com/.cn...

    3）把域名进行DNS解析：把域名和服务器关联在一起（解析时候需要填写服务器的外网IP），以后访问域名就相当于访问服务器
       =>DNS（Domain Name System，域名系统），万维网上作为域名和IP地址相互映射的一个分布式数据库 （域名解析成功会在DNS系统中记录一条信息   “www.xxx.com  xxx.xxx.xx.xxx” 保证以后访问域名，可以直接找到外网IP，通过外网IP访问到服务器）

       =>我们还要进行备案


    4）一台服务器可以发布很多项目，服务器买回来还不算结束，我们还需要在服务器上进行项目发布，此时需要一些发布WEB站的工具：IIS(C#.. ->WINDOWS)、APACHE TOMCAT(PHP/JAVA... ->LINUX)、NGINX(用的最多的)...
      ->指定当前域名访问服务器后，到底执行的是哪一个项目的源代码（让域名和服务器上的项目关联到一起）


3.内网IP（局域网）
  在一个区域内，大家连接的是同一个网络（准确来说：连接同一个WIFI不一定是同一个网络，连接不同的WIFI也可能是相同的网络，一切都看路由交换机的配置），这就是局域网

  在同一个局域网下，成员可以互相访问（你的电脑连接了A网络，手机也连接了A网络，那么手机可以访问电脑上的一些信息了 =>这样可以做移动端开发时候的手机联调）

  HBuilder也提供了联调的功能（代码上加断点，手机访问，程序会走断点）

4.怎么把自己本地的代码上传到远程服务器上
  ->服务器上是不允许安装除了开发需要的环境项以外的任何东西(保持服务器的干净)
  ->我们一般都基于FTP上传（有很多FTP上传的工具：FileZilla）

//========================================
面试必问问题：打开一个浏览器，在地址栏输入一个网址，按下ENTER键，到看到整个页面，中间都经历了哪些事情?

【HTTP请求阶段：向服务器发送请求】
    1.浏览器首先向DNS域名解析服务器发送请求
    2.DNS反解析：根据浏览器请求地址中的域名，到DNS服务器中找到对应的服务器外网IP地址
    3.通过找到的外网IP，向对应的服务器发送请求（首先访问的是服务器的WEB站点管理工具:准确来说是我们先基于工具在服务器上创建很多服务，当有客户端访问的时候，服务器会匹配出具体是请求哪个服务）
    4.通过URL地址中携带的端口号，找到服务器上对应的服务，以及服务所管理的项目源文件

【HTTP响应阶段：服务器把客户端需要的内容准备好，并且返回给客户端】
    5.服务器端根据请求地址中的路径名称、问号传参或者哈希值，把客户端需要的内容进行准备和处理
    6.把准备的内容响应给客户端（如果请求的是HTML或者CSS等这样的资源文件，服务器返回的是资源文件中的源代码[不是文件本身]）

【浏览器渲染阶段】
    7.客户端浏览器接受到服务器返回的源代码，基于自己内部的渲染引擎（内核）开始进行页面的绘制和渲染
      ->首先计算DOM结构，生成DOM TREE
      ->自上而下运行代码，加载CSS等资源内容
      ->根据获取的CSS生成带样式的RENDER TREE
      ->开始渲染和绘制

2.我们把一次完整的 请求+响应 称之为 “HTTP事务”
  事务就是完整的一次操作，请求和响应缺一不可

3.一个页面完全加载完成，需要向服务器发起很多次HTTP事务操作
  一般来说：首先把HTML源代码拿回来，加载HTML的时候，遇到link/script/img[src]/iframe/video和audio[没有设置preload='none']...都会重新和服务器端建立HTTP事务交互

  特殊情况：如果我们做了资源缓存处理(304)，而且即将加载的资源在之前已经加载过了，这样的操作和传统的HTTP事务有所不一样，他们是从服务器和浏览器的缓存中读取数据，比传统的读取快很多

4.在客户端向服务器发送请求，以及服务器把内容响应给客户端的时候，中间相互传递了很多内容(客户端把一些内容传递服务器，服务器把一些内容响应给客户端)，我们把传递的内容统称为“HTTP报文”


//===============前端性能优化
一：减少HTTP请求的次数及请求内容的大小









