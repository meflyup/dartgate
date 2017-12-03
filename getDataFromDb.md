# 获取数据库数据

上一节课http放回json数据。本次课从数据库获取数据，并以json格式返回客户端。本课结束后，将拥有一个常规意义上完整的web app。你已经走完了一个圆圈。知道web app开发的一些基本的、核心的要素和概念。剩下的就靠你在本课程中所掌握的学习能力不断发展了。  
同上节课一样。老师给各位同学演示零dart数据库基础该怎么做，希望大家掌握这些思路。
数据库是应用的后台基础。各类语言都会发展出相关的数据库处理API。dart语言也不例外。那么从dart文档网站我们如何开始学习。

##思路
1. 在[dart网站](www.dartlang.org)搜索如下关键字。
 - database
 - mysql
 - sqlserver
 - postgresql  

2. 查看是否有搜索结果
3. 如果没有结果，基本可以判断这个网站上没有收录相关的文档
4. 但是，也有可能是网站没有对所有文档做索引，因此检索不到任何信息，故有时候使用手动查找也有必要。文档那么多，从哪里查找？  
 - 数据库操作通常都是后端的，意味着我们可从服务器考虑。那么就到服务器相关的文档中查找
 - 到了具体页面，可以在页面中迅速ctrl-f快速查找，定位关键字。  
 
##实战操作  

5. 以mysql为关键字搜索，结果如图所示。  
 ![screenshot-search-mysqllib](http://img1.ph.126.net/bAUhLIXC6EhyQpGIPg-Bqw==/6631339345072279084.png)  
6. 选择第一条(通常，搜索结果也靠前，相关性越高)，打开进入。
![screenshot-search-mysqllib](http://img2.ph.126.net/ODJLtzHaHYL3Ly4AM6fsNA==/6631278871932749408.png)  
在页面中搜索mysql，效果如图。点击打开MySQL driver。
7. 很好！快速浏览一下，似乎我们已经发现了用于dart连接数据库的一个工具。  
  ![screenshot-search-mysqllib-pub](http://img1.ph.126.net/wwiymwX_z7WpZYBV79h9PQ==/6631267876816476619.png)  
8. 可是，怎么用？不用担心，请记住，跟我们买来电器设备一样。编程工作中出现的
API和各种库，通常都会伴随一个使用手册，让我们分析一下这个页面。上面有几个tab  
 - README.md
 - CHANGLOG.md
 - Installing
 - Version  

我们要的就是解决问题的思路。通常，我们可以在README.md中获得这个API和工具的基本介绍，甚至包括怎么使用；在CHANGLOG 中查看进度状况以及相关的修改；在Installing中获悉如何安装和使用；在Version中获得版本信息。这在编程世界已经几乎似乎约定俗成的通用规则。其他语言都有类似的情形，因此不论以后换到那个语言，你都不必害怕和担忧。  
   ![screenshot-search-mysqllib-pub-usage](http://img0.ph.126.net/yr2-i4Vs9a2ai4Pce9Tb6w==/6631416310886224920.png)  
   ![screenshot-search-mysqllib-pub-install](http://img1.ph.126.net/wwiymwX_z7WpZYBV79h9PQ==/6631267876816476619.png)  
到此，我们从文档了获知关于sqljoy 库的基本情况。可是有同学问installing中的安装是说了，可是那是什么意思？让我们问问自己，这个问题你一定需要老师给你解答吗？你觉得老师一定知道吗？如果老师也是第一次使用，老师在课堂上第一次这么做，他能回答你吗？事实上，你一定可以自己解决？在这个信息时代，你需要能力是：  
  - 检索信息
  - 获得知识
  - 动手测试  


现在，我们不知道如下代码到底是什么含义：  
  {%ace edit=true, lang='dart'%}
    dependencies:
    sqljocky: "^0.14.1"
  {%endace%}
 
这里就该回到dart web编程初体验哪一个，请回忆我们曾经打开dart web项目中的.yaml文件，在webstorm中点击get dependencies，跟这里相互呼应：就是要获取项目依赖的API、库、utility。而这里指的就是取sqljocky。紧随其后的  

{%ace edit=true,lang='dart'%}
pug get 
{%endace%}

其实就是我们在webstorm中点击get dependences 背后所执行的命令。我们已经指导了IDE是辅助我们开发的工具，它会将各种命令用UI的方式提供给开发者，省去了敲打命令的繁琐。

<!--sec data-title="练习" data-id="section0" data-show=true ces-->

尝试在[dart网站](www.dartlang.org)学习关于pub 命令的知识。

<!--endsec-->

<!--sec data-title="tips" data-id="section1" data-show=true ces-->
yaml 以及pub get这些东西与其说是知识，不如说是规则。这是dart语言及技术体系设计开发者认为设计出来的一组规范，把它们当做产品说明书就可以，忘了不要紧，只要你知道如何去查找这组规范即可，用得多了自然就记住了。关于如何查抄，那就跟本节上面的思路一样了。请各自自己搜索、阅读、理解、实践。
<!--endsec-->


##学习数据库连接代码

一般来说，无论是何种语言提供的API和utility，开发者通常都会附上一份入门example。从[pub.dartlang.org](http://pub.dartlang.org)网站中获得的各种package也是如此。并且，所下载的pub package一般都有源代码，可以用各种工具查看，比如用web storm可以打开，跟我们之前打开应用的方式一模一样。 如图所示。  
![screenshot-open-pub-package](http://img0.ph.126.net/8aUG0_tY7YoL-cCgW1Sc6w==/6631272274863080304.png)  
![screenshot-open-pub-package-layout](http://img2.ph.126.net/HgUjh-7U6PH5CU1MKk27Eg==/6631328349956094413.png)  
```dart
var pool = new ConnectionPool(host: 'localhost', port: 3306, user: 'bob', password: 'wibble', db: 'stuff', max: 5);
var results = await pool.query('select name, email from users');
results.forEach((row) {
	print('Name: ${row[0]}, email: ${row[1]}');
});
```
{%ace edit=true,lang='dart'%}
var pool = new ConnectionPool(host: 'localhost', port: 3306, user: 'bob', password: 'wibble', db: 'stuff', max: 5);
var results = await pool.query('select name, email from users');
results.forEach((row) {
	print('Name: ${row[0]}, email: ${row[1]}');
});
{%endace%}  

这段代码来自[sqljocky usage](https://pub.dartlang.org/packages/sqljocky)。 
你知道第1行是做什么的吗？要知道做什么，关键就看ConnectionPool这个类是做什么的。这个容易，我们查看它的“说明书”即可： 

![screenshot-sqljocky-document](http://img2.ph.126.net/kvetzNvOKU3G2kkqVp-0QQ==/6631212901235179577.png)  
这张图中的位置告诉我们那里找到sqljocky的支持文档
![screenshot-sqljocky-document-connectionpool](http://img0.ph.126.net/Z7yRtwmI6rlghZ4ZHq8Ebg==/6631411912839807156.png)  
这张图中告诉我们ConnectionPool这个类是做什么的，构造函数中各种参数是做什么。有了这些说明，我们就明白连接sql数据库需要哪些条件，怎么设置这些条件。 

<!--sec data-title="练习" data-id="section2" data-show=true ces-->

搜索学习连接数据库方面的概念。包括：
 - 数据库host
 - 数据库端口
 - 数据库连接用户名
 - 数据库连接密码
 - 以及其他各种参数

<!--endsec-->





### to be continued...
