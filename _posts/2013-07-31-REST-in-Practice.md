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

chapter 3 基础的Web集成

用于应用集成的两种简单的Web技术：

- URI隧道技术
- 普通老式XML(POX)