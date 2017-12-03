# REST service简介
## Web Service
要明白什么是REST service的概念，首先需要明白什么是Web Service。Web Service(WEB服务)能够快捷和方便地综合结合各种系统、商务和任何应用平台。利用最新的Web Service 标准能够使任何软件系统和系统之间的应用互通互联，方便，而且更加廉价。Web Services 是一种基于组件的软件平台，是面向服务的Internet 应用。Web Services      框架的核心技术包括SOAP, WSDL 和UDDI,它们都是以标准的XML 文档的形式表示。

SOAP (“Simple Object Access Protocol”的缩写)是Web Services 的通信协议。SOAP是一种简单的、轻量级的基于XML 的机制，用于在网络应用程序之间进行结构化数据交换。SOAP包括三部分:一个定义描述消息内容的框架的信封，一组表示应用程序定义的数据类型实例的编码 规则，以及表示远程过程调用和响应的约定。
1. 传递信息的格式为XML.这就使Web Services能够在任何平台上，用任何语言进行实现。
2. 远程对象方法调用的格式。规定了怎样表示被调用对象以及调用的方法名称和参数类型等。
3. 参数类型和XML格式之间的映射。这是因为，被调用的方法有时候需要传递一个复杂的参数，例如，一个Person对象。怎样用XML来表示一个对象参数，也是SOAP所定义的范围。  
WSDL表示WEB服务说明语言。WSDL文件是一个XML 文档，用于说明一组SOAP消息以及如何交换这些消息。当实现了某种服务的时候(如：股票查询服务)，为了让别的程序调用，必须告诉大家服务接口。例如： 服务名称，服务所在的机器名称，监听端口号，传递参数的类型，个数和顺序，返回结果的类型等等。这样别的应用程序才能调用该服务。WSDL协议就是规定了 有关Web Services描述的标准。  
UDDI(“Universal Description， Discovery，and Integration”的缩写)提供一种发布和查找服务描述的方法。UDDI 数据实体提供对定义业务和服务信息的支持。WSDL 中定义的服务描述信息是UDDI注册中心信息的补充。

### Web Services的工作原理
1. Web Services 服务提供方通过WSDL描述所提供的服务，并将这一描述告知Web Services 注册服务器。

2. 注册服务器依据WSDL 的描述，依照UDDI的协定更新服务目录并在Internet 上发布。

3. 用户在使用Web Services 前先向注册服务器发出请求，获得Web Services 提供者的地址和服务接口信息。

4. 使用SOAP 协议与Web Services 提供者建立连接,进行通信。

## REST service

#### 一切都是资源
URL规范(RFC 2396)指出：“资源可以是任何有标示的东西”[18]。
任何事物，只要有被引用的必要，就是一个资源。它可以是一个实物，也可以是一个抽象的概念。通常一个资源是某个可以存放在计算机上并体现为比特流的事物。在Web中，可以这样认为——资源是URL标示的东西。因此：
- 1.数据库是资源 
- 2.网页是资源
- 3.文件是资源
- 4.计算能力也是资源

#### 什么是REST？
-  REST – Is an architectural style.是一种web架构风格,全称Representational State Transfer 

- 什么是Representational State Transfer（表述状态转移）

&emsp;&emsp;REST 从资源的角度来观察整个网络，分布在各处的资源由URI确 定，而客户端应用通过URI来获取资源的表述。获得这些表述致使这些应用程序转变了其状态。随着不断获取资源的表述，客户端应用不断地在转变着其状态，即所谓表述性的状态转移
![表述状态转移](/assets/调试/rest.png)

####REST 架构风格
REST的架构风格如下图所示
![REST](/assets/调试/rest框架.png)

#### REST service的http方法
REST式的Web Service使用HTTP里的方法有：GET， POST， DELETE， PUT。REST式的Web Service调用产生的HTTP请求内容只是用于服务数据不是用来指明调用方法，目标对象或返回值的。



