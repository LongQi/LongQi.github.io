---
layout: post
---
#The Physical Web

2014年10月3号左右，Google推出了一个项目：[The Physical Web](http://google.github.io/physical-web/)

从名字上来看是一个物联网相关的项目，叫做物理网络。The Physical Web 是把虚拟的 web 延伸到周围的物理世界。其目标是开发出一套共同的 web 标准，让任何设备（不仅仅是 Google 的设备）都可以用来提供交互以及一组服务。利用这套标准，智能设备可以把自己的 URL 地址广播给周围，周围的任何设备（如智能手机、平板电脑）应该就可以接收到这些 URL 然后呈现给用户。用户然后就可以根据需要与这些设备直接交互而不需要下载 app。

![](http://zlong-name.qiniudn.com/6cc26142047c1d85bccc01d4f3925d98.png)

在Github上可以看到更详细的关于这个项目的信息，可以看得出，目前还是雏形期。一开始提出的想法也非常简单，它并不是像很多人想象的那样提供智能物联的通用接口，设计适合物联网的web标准等等。

而只是简单的两样东西：

- 一个硬件：hardware beacon，它的作用就是向周围广播一个URL，目前项目中提到的广播方式是用Bluetooth Low Energy；
- 一个软件：android/ios app，一个手机端的应用，这个应用用来搜索其附近的智能硬件（即装有beacon的硬件，并且正在广播URL），搜索到之后，就将这个URL保存下来。

目前，看到这个项目所要做的就是这两样东西，其中软件部分比较简单，只需要做一个app就行，而且app的功能非常简单，在搜索到一个硬件设备的URL之后，就调用手机的浏览器去打开，交互。这就跟这个app没什么直接关系了。

前面的硬件部分呢，其实功能也非常单一，就是不停地向周围广播一串字符，这串字符就是可以控制或者查看该智能设备相关信息的URL。而这个URL的标准什么的，这个智能设备的控制和查看信息的web页面跟这个项目没什么直接关系。

目前可以提供这种功能的固件有：[Bluegiga BLE113](https://www.bluegiga.com/en-US/), [RFduino](http://www.rfduino.com/)。

可以看出，Google在做这件事的时候，还是从开放性，易用性角度来入手，方式非常简单，也并未为物联网的智能设备指定什么标准什么的，就只是提供一个可以让大家更方便接触到智能设备的一种方式。当然如果这种方式应用量比较大的话，也会逐渐成为一个相当可观的平台。这种方式有什么好处呢，就是可以不需要很多app，比如现在的智能设备肯定都配备一个app，那如果身边全是智能设备的话，app显然是不合适的，而这种轻量级的基于web的方式就非常方便。

不过，很明显还有比这更简单的方式啊，比如：二维码，在一个智能设备上贴一个二维码，里面包含着一个URL，用户只需要扫描一下这个二维码，立刻可以获得所需要的信息。而微信好像就是这种方式，微信已经在做智能设备的接入平台了，其用公众号的方式为每个智能设备开通公众号，也是同样的，不需要一个单独的APP，只需要一个公众号就可以了，同样也是轻量级的。而且微信有很大的用户基数，想做起来还是挺容易的，最近微信应该有团队一直在做这件事。

那反过来再说，这种广播的方式和二维码的方式有什么区别呢？孰优孰劣呢？一个是主动的方式，一个是被动的方式。确实就像刚开始的web，那时候网站本身就很少，人们会记住一些比较常用的网站，就可以上网了。可是随着互联网的快速发展，网站越来越多，类型越来越多，功能越来越多，一个人想要记住那么多的网站URL，怎么可能呢？那就是搜索引擎的天下了，可以很方便地把你想要找的东西搜索出来，这样你就不需要记那么多URL了。那这个时候搜索引擎就成了人们上网的入口。那google的这个Physical Web是不是就想做成这样的一个平台呢？当它接入的智能设备越来越多的时候，确实也会产生一些我们现在意想不到的应用。

不管怎么说，这也是一种尝试的方式，我们离那个智能物联的时代越来越近了，各种各样的方式都值得尝试，只有这样，这个时代才会更加多样，更加多彩地到来。