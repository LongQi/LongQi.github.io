---
layout: post
---
#安装XAMPP时无法启动MySQL的解决办法

之前也遇到过这个问题，由于没有好的解决办法，就放在那里了。今天又碰上了，想着一定要解决掉才行。

这是个什么问题呢？首先XAMPP是一个捆绑发行版，让PHP的开发环境搭建起来非常方便。它集成了Apache+MySQL+PHP，安装了这个之后，就可以立刻进入PHP的开发了。如果是正常的话，按照好之后，apache和mysql都可以直接提供服务的。

我遇到的情况是这样的，因为之前这个电脑里装的有mysql，而且里面有些数据库是我不想动的，还有用的。那么，我就不能把之前的那个mysql给卸载掉。而安装XAMPP的时候，又要安装一个mysql，那么，在启动mysql服务的时候就会有冲突，而产生错误，无法正常启动。

一个解决办法是这样的：

1. 假设原先的MySQL的安装路径是："C:\Program Files (x86)\MySQL\MySQL Server 5.5\"；
2. 安装XAMPP之后的MySQL的安装路径是："f:\xampp\mysql\"；
3. 修改注册表，Windows+R键，输入regedit；
4. 找到：[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MySQL]的ImagePath，进行修改；
5. 按照第1条的假设，这个ImagePath的内容应该是："C:\Program Files (x86)\MySQL\MySQL Server 5.5\bin\mysqld" --defaults-file="C:\Program Files (x86)\MySQL\MySQL Server 5.5\my.ini" MySQL；
6. 将其修改为：f:\xampp\mysql\bin\mysqld.exe --defaults-file=f:\xampp\mysql\bin\my.ini mysql；
7. 此刻，就可以通过XAMPP上的mysql，来正常地启动MySQL服务了；
8. 在需要原先的数据库的时候，也同样需要将注册表修改回去即可；
9. 这样，即不会影响到之前的数据库，又能够让XAMPP正常提供MySQL服务，只不过在切换的时候需要手动修改注册表。

