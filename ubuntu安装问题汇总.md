## ubuntu18.04下安装网络打印机

如果是HP等linux友好的打印机，则过程会被简化

1.打开 设置-设备-打印机-额外打印机设置

2.如果网线或者USB连接时能够搜索到打印机IP

![img](https://upload-images.jianshu.io/upload_images/7645113-4fa4408b3739e0dc.png?imageMogr2/auto-orient/)

直接选中并转发。

3.安装驱动 该部分分为以下三种情况

​         (1) 选择搜索要下载的驱动程序 如果可以就直接转发完成 继续下一步即可。（在数据库选择同理）

​         (2) 自动搜索不可以时，选择从PDD文件安装（自己下载驱动）

![img](https://upload-images.jianshu.io/upload_images/7645113-dcee2b0130810268.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

4.为新的打印机设置名称点击 应用

注意：有时提示CUPS无法正常工作之类的报错，需要安装CUPS `sudo apt install cups`



## ubuntu下拨号连接

**使用pppoeconf命令进行配置连接信息**

`sudo pppoeconf`

1.在终端界面下一直选择 是

2.输入用户名和密码（记得要删除usename这几个字）

3.配置DNS（yes，运行运营商自动配置DNS）

4.通过pppoe限制MSS的大小选择 是

5.计算机启动时自动连接（都选是就好）

注：所创建的配置文件位于/etc/ppp/pers,文件名为connection name 

启动DSL连接`sudo pon dsl-provider`

关闭DSL连接`sudo poff`

 ```pon/poff命令详解
pon命令详解：
1.pon命令不带参数，首先检测运行/etc/ppp/ppp_on_boot文件，如果不存在就会去 /etc/ppp/peers/文件夹下寻找启动文件。 
2.pon命令带参数，pon myisp；就会使用/etc/ppp/peers/myisp文件

poff命令详解：
1.poff myisp；命令就是关闭myisp连接，如果只有一个adsl链接，可以不带参数直接运行
2.poff可以带参数：
-r 重复拨号.
-d 切换PPPD的状态调试选项。
-c causes pppd(8) to renegotiate compression.
-a 关闭所有的ppp连接
-h 显示帮助信息
-v 显示版本信息

 ```

查看连接信息`ifconfig ppp0`

查看连接日志`plog`

注：有时打不开网页需要刷新



如果需要进行局域网连接时（接路由器）需要去掉pppoe的影响

1.输入cd /etc/network 转入 /etc/network目录中 打开interfaces

2.```sudo gedit interfaces```将最后一行注释掉加#号（局域网使用的时DHCP网络，不用手动操作）

3.保存文件，关闭gedit 输入```sudo service network-manager restart```

4.回车确定 再去屏幕右上角点击连接（有的需要）





## ubuntu网卡操作

启动网卡

```shell
sudo ifup eth01
```

关闭网卡

```shell
sudo ifdown eth01
```

重启网络的命令

```shell
sudo /etc/init.d/networking restart //会重新读取配置文件
```



## 重新安装ubuntu18.04系统

下载ubuntu64位iso镜像文件，下载Ultarso工具



## ubuntu18.04下配置安装搜狗输入法

首先，安装Fcitx输入框架

`sudo apt insatll fcitx`

到搜狗官网下载LInux版本64位安装包.deb

![img](https://img-blog.csdn.net/20180511114512166)

![img](https://img-blog.csdn.net/20180511114734772)

根据下方箭头更爱输入框架为fcitx，然后点击上面的Apply System-Wide应用到全局。然后将当前用户进行注销后再进行登录（注销没有效果，重启就可以了）。

登陆后在右上角出现一个键盘标志，点击进入，选择Configure Current Input Method

![img](https://img-blog.csdn.net/20180511115128483)

![img](https://img-blog.csdn.net/20180511115356714)

进入到Add input method界面，将下面的Only Show Current Language 点掉后，在搜索栏搜索搜狗拼音，选中之后进行添加。

![img](https://img-blog.csdn.net/2018051111581755)

成功之后，打开浏览器随便输入，可以看到输入结果，同时成功后下方还会出现搜狗输入法的标志，这时候就可以通过shirt键切换中英文。

## ubuntu安装Typora markdown编辑器

#Ubuntu 安装 typora
今日刚刚更换了Ubuntu 17.04系统， 熟悉的markdown编辑器typora无法通过包安装管理直接安装，需要自己添加源，把过程记录在这里留作记录，也供大家参考：

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE这是一个可选的操作，但是建议还是添加上这一步。
    sudo add-apt-repository 'deb http://typora.io linux/'添加typora的远程仓库
    sudo apt-get update更新
    sudo apt-get install typora 安装
    如果出现typora无法打开的情况，执行 sudo apt install gconf2
## ubuntu下安装anaconda3&配置环境变量

官网下载https://www.anaconda.com/download/#linux终端打开目录

`./Anaconda3-5.1.0-Linux-x86_64.sh`

或者终端输入 `wget https://repo.continuum.io/archive/Anaconda3-5.1.0-Linux-x86_64.sh && bash Anaconda3-5.1.0-Linux-x86_64.sh`

然后照着安装，基本也就是路径，同意协议之类的，最后装好了会提示微软vs的安装，如果不是要用到VS的，NO掉.

`sudo gedit /etc/profile`

在文件尾输入

`PATH=/root/annconda3/bin:$PATH`

![img](https://img-blog.csdn.net/20180814123031949?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3phaXNoaWppemhpZGlhbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

保存后输入

`source /etc/profile`

输入python 进行版本检查

出现安装anaconda时对应的版本即为添加变量完成

如果你想删除Anaconda，切换到你安装anaconda的目录，直接 
`rm -rf anaconda3` 
然后在去/etc/profile，把配置的删除就OK了

##  ubuntu下安装和启动anaconda-navigator图形界面

安装完成anaconda之后使用

```
conda install -C anaconda anaconda-navigator
anaconda-navigator      #启动
```

## ubuntu下安装deb包

```
在Ubuntu下安装deb包需要使用dpkg命令.Dpkg 的普通用法：
1、sudo dpkg -i <package.deb>
安装一个 Debian 软件包，如你手动下载的文件。
2、sudo dpkg -c <package.deb>
列出 <package.deb> 的内容。
3、sudo dpkg -I <package.deb>
从 <package.deb> 中提取包裹信息。
4、sudo dpkg -r <package>
移除一个已安装的包裹。
5、sudo dpkg -P <package>
完全清除一个已安装的包裹。和 remove 不同的是，remove 只是删掉数据和可执行文件，purge 另外还删除所有的配制文件。
6、sudo dpkg -L <package>
列出 <package> 安装的所有文件清单。同时请看 dpkg -c 来检查一个 .deb 文件的内容。
7、sudo dpkg -s <package>
显示已安装包裹的信息。同时请看 apt-cache 显示 Debian 存档中的包裹信息，以及 dpkg -I 来显示从一个 .deb 文件中提取的包裹信息。
8、sudo dpkg-reconfigure <package>
重新配制一个已经安装的包裹，如果它使用的是 debconf (debconf 为包裹安装提供了一个统一的配制界面)。

如果安装过程中出现问题,可以先使用命令:sudo apt-get update更新后再执行上面的命令.
```

## ubuntu下安装QQ和WeChat

首先安装wine环境，解压deepin-wine-ubuntu-master在文件夹子内./install.sh进行安装。

（git clone https://github.com/wszqkzqk/deepin-wine-ubuntu.git)

安装QQ和WECAHT只需要在终端运行等待即可安装完毕。

```
sudo dpkg -i deepin.com.qq.im_8.9.19983deepin23_i386.deb
sudo dpkg -i deepin.com.wechat_2.6.2.31deepin0_i386.deb
```

