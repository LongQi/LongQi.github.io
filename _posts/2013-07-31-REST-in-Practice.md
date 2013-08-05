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

