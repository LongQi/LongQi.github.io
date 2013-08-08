---
layout: post
---
# REST in Practice #

## chapter 1 ##

资源是基于Web系统的基础建造模块，我们应该从资源的角度来思考Web.

URI（Uniform Resource Identifier）统一资源标识符，一个URI唯一标识一个Web资源，但是一个资源可以有多于一个URI。URI的形式为<scheme\>:<特定于scheme的结构\>

- URI(Uniform Resource Identifier)统一资源标识符
- URN(Uniform Resource Name)统一资源名称
- URL(Uniform Resource Locator)统一资源定位符

URL和URN都是URI的特殊形式。一个URI标识了访问资源的机制，通常称作一个URL。HTTP URI就是URL的例子。

资源必须至少有一个标识符，以便于在Web上寻址，每个标识符与一个或多个表述相关联。一个表述指的是某个资源在某特定时刻的状态的转化形式或者视图。对于一个资源的访问，总是通过其表述方式来间接完成。URI对于消费者来说应该是不透明的，只有URI的发布者才知道如何来解释它和如何将它映射到一个资源。

资源、标识符以及动作就是所有我们需要与在Web之上的资源交互的东西。

REST(Representational stat Transfer)表述性状态转移，由Fielding在2000年提出。

Web作为一个应用平台，是松耦合的。

Richardson成熟度模型：

- **零级服务**，其特征为那些服务有单个的URI，并且使用单个的HTTP方法（通常是POST）
- **一级服务**，使用了很多URI，但是只是用单个HTTP动词（通常是GET）
- **二级服务**，使用了大量的可通过URI寻址的资源，支持多个HTTP动词
- **三级服务**，支持超媒体作为应用状态的引擎的观念。

## chapter 2 ##

以Restbucks为例，把Web看作一个建造分布式系统的平台。

##chapter 3 基础的Web集成##

用于应用集成的两种简单的Web技术：

- URI隧道技术
- 普通老式XML(POX)

URI隧道技术，是将信息编码到URI内部，只要向Web服务器发送一个简单的HTTP GET或者POST请求，就可以触发程序的执行，还可以使用URI的内容为这些代码的执行设定参数。

URI隧道技术在Richardson成熟度模型中被划分为一级服务。在一般情况下，URI隧道技术并非是对Web友好的，因为它是用URI来对操作进行编码，而不是标识可以通过HTTP动词来操作的资源。

HTTP GET的安全性（是不是改变了服务器的状态？）和幂等性（重复时，结果是不是一样？）

POX：基于HTTP之上的普通老式XML，消息传递，用Web风格的普通老式XML方法做应用集成时，是使用HTTP请求和响应在客户和服务器之间转移被编码为普通XML的文档。

POX使用HTTP的POST在系统之间传递XML文档。

POX服务在Richardson的成熟度模型中排在零级。POX方式并不是将Web当作一个平台，而只是用它作为传输远程调用的隧道。Web架构固有的可伸缩性、可靠性和健壮性，对于基于POX的解决方案来说并不存在。虽然POX是一种比较简单的、令人感到熟悉而舒适的方法，但它像URI隧道技术一样，使用范围极为有限，因此我们通常建议：应该像躲避瘟疫一样避开POX！

URI隧道技术和HTTP之上的POX集成强调了简单性和可访问性，却忽视了健壮性。


##Chapter 4 CRUD式Web服务##

从现在开始，我们将网络和HTTP看作是我们的分布式应用中不可分割的组成部分，而并非只是在线路上传输字节的手段。通过CRUD，我们将开始明白为何要把HTTP用作一种应用协议，而不是一种传输协议，还会发现Web其实是一个建造分布式系统的大框架。


POST-create, GET-read, PUT-upgrade, DELETE-delete

CRUD同时使用了HTTP和URI，它们被认为是处于Richardson成熟度模型的第二级。与其他分布式系统方法不同的是，CRUD式服务暴露给消费者的契约是非常简单的，因为它只涉及到一个具体的URI，一个URI模板、四个HTTP动词。

- POST： /order 创建一个新订单，成功之后收到一个Location头信息，说明新订单的URI；
- GET： /order/{orderId} 请求该URI所对应的订单的当前状态；
- PUT： /order/{orderId} 更新该URI所对应的订单，提供完整的表述；
- DELETE： /order/{orderId} 从逻辑上删除该URI所对应的订单。

健壮的服务必须遵守Postel法则，即“严格发送，自由接收”。

PUT请求期望能将整个资源的表述都提供给服务器，而不是只提供资源状态的变化量。如果只提供变化量，可以用动词PATCH。PUT是幂等的。

GET请求既安全又幂等，PUT请求和DELETE请求是幂等的，但都不安全。POST请求则是既不安全也不幂等。

##Chapter 5 超媒体服务##

**超媒体原则**

简单地说，超媒体系统转换了应用的状态。REST的超媒体原则没有指定具体的表述格式，但是要求该格式必须能够传递必要的超媒体信息。

**超媒体格式**

Atom， XHTML是通用的标准的超媒体格式。在超媒体格式中，超媒体控件表现了协议信息。

HTTP头信息中，Content-Type设置为application/vnd.restbucks+xml

**契约**

契约是一切分布式系统中的关键部分，因为它们规定了一个应用的各个部分应该如何交互。

Web上任何契约的核心都是服务所支持的一组媒体类型。


##Chapter 7 Atom联合格式##

Atom是一种基于XML的超媒体格式，用于表现Web内容的时间戳列表以及诸如blog发表和新闻文章这样的元数据。

**格式**

Atom通过列表来表示数据，称之为提要（feed），提要是由一个或多个带有时间戳的条目(entry)组成，条目将文档的元数据与Web内容关联起来。提要和条目一样，包含自身有关的元数据。Atom提要中条目的排列顺序没有任何含义。提要的元数据包括下列元素：

	<atom:id>是提要的永久的、通用唯一标识符；
	<atom:title>为提要提供了人类可读的名称；
	<atom:updated>表明当前提要的最后修改日期；
	<atom:generated>标识出创建提要的软件代理；
	<atom:link>包含用于获取提要的标准URI。

每一个条目还包含了一个<atom:content>元素，它可以用来包含任意的外部元素，包括共享默认命名空间的元素。

**Atom的一般用途**

联合内容，表述文档和文档类似的结构，创建元数据丰富的资源列表，在现有的资源表述上添加元数据，创建非超媒体内容的目录。

##Chatper 8 Atom发布协议##

Atom发布协议（Atom Publishing Protocol,简称AtomPub）,一个建立在Atom之上的协议，用于发布和编辑Web资源。AtomPub是一种用于发布和编辑包含相关的Atom元数据的Web内容的领域应用协议。该协议是由一些特定于协议的资源，加上客户如何使用HTTP动词、头信息和状态代码来操作这些资源的规则所组成。

AtomPub是一个发布和编辑Web资源的应用层协议，基于HTTP对Atom格式表述的转移来实现。
