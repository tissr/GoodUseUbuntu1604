# GoodUseUbuntu1604
打造宜居 Ubuntu16.04

> Windows用腻了，试试Ubuntu吧！

> ![Windows用腻了，试试Ubuntu吧](http://upload-images.jianshu.io/upload_images/3203841-ff147839ac0fc38f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 更换国内镜像源
##### 1. 备份/etc/apt/sources.list的源内容
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back 
```

#### 2. 更改源文件内容 
> 以管理员权限打开
```
sudo vim /etc/apt/sources.list 
```
>  删除原内容，替换为以下内容
```
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
```

##### 3.更新镜像源
```
sudo apt update 
```

## 科学上网(师夷长技以制夷)

> ![ss](http://upload-images.jianshu.io/upload_images/3203841-773fb44e17e137a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 1.首先使用快捷键ctrl+alt+t，打开我们的终端窗口 
##### 2.接着安装shadowsocks-qt5（先在路由器设置好代理，才能进行这一步）
```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```
##### 3.然后安装genpac
```
sudo apt-get install python-pip
sudo pip install genpac
```
##### 4.接下来使用genpac生成autoproxy.pac
```
genpac -p "SOCKS5 127.0.0.1:1080" --output="autoproxy.pac"
```
> 该命令会在/home/xxx/下生成autoproxy.pac（其中xxx是用户名，比如我的是/home/zhao/） 
#####5.运行shadowsocks-qt5（可通过搜索功能找到），填写server address,server port,password,Encryptioin Method等信息，其他的使用默认的就行了。 
##### 6.最后一步，打开SystemSetting->Network->Network Proxy，将Method改为Automatic，Configuration Url填”file:///home/xxx/autoproxy.pac”，然后Apply System Wide即可 
##### 7.打开浏览器，现在可以开始科学上网了

## 安装美化主题
##### 1.安装主题管理器 unity-tweak-tool

> ![安装主题管理器 unity-tweak-tool](http://upload-images.jianshu.io/upload_images/3203841-18c9240837603399.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> ![主题管理器](http://upload-images.jianshu.io/upload_images/3203841-9f59a7c0a1b7984e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



```
sudo apt-get install unity-tweak-tool
```

##### 2. 安装扁平化主题Flatabulous 及配套图标

```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install flatabulous-theme

sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update
sudo apt-get install ultra-flat-icons
```

> 安装完成后，打开unity-tweak-tool软件，修改主题和图标：

> ![进入“主题”](http://upload-images.jianshu.io/upload_images/3203841-f3febb913dbff457.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 进入“主题”，修改为Flatabulous


![修改为Flatabulous](http://upload-images.jianshu.io/upload_images/3203841-a330b62fad159145.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 在此界面下进入Icons栏
> 



> ![进入Icons栏](http://upload-images.jianshu.io/upload_images/3203841-f3c569f5f1a95a16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 修改为Ultra-flat:
![修改为Ultra-flat](http://upload-images.jianshu.io/upload_images/3203841-d34c9c0070333f06.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#####  3. 美化终端
> 首先，安装zsh：
```
sudo apt-get install zsh
```
> 先安装git

```
sudo apt-get install git
```
> 再安装oh-my-zsh

```
sudo wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

> 切换到 zsh 模式
```
chsh -s /usr/local/bin/zsh
```

> 修改终端配色
>

> ![修改终端配色](http://upload-images.jianshu.io/upload_images/3203841-24fc64178fbdc521.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 文字和背景采用系统主题，透明度约左侧20%即可，下面的palette样式采用Tango

> ![透明度约左侧20%](http://upload-images.jianshu.io/upload_images/3203841-7b628a0c10d3a2c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> ubuntu自带的字体不太好看，可以采用文泉译微米黑字体替代

```
sudo apt-get install fonts-wqy-microhei
```
> 然后通过unity-tweak-tool来替换字体


> ![通过unity-tweak-tool来替换字体](http://upload-images.jianshu.io/upload_images/3203841-37efae9d49bbca9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



> ![更改字体属性](http://upload-images.jianshu.io/upload_images/3203841-b49b79d08fb8cee8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



####  安装docky
> 模仿Mac底边的dock栏


> ![Mac底边的dock栏](http://upload-images.jianshu.io/upload_images/3203841-6f0ed7f8397ba191.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



```
apt install docky
```


## 配置开发环境

##### 安装编辑器之神vim
```
sudo apt update

sudo apt remove vim

sudo apt install vim
```

#####  安装sublime text 3

> ![安装sublime text 3](http://upload-images.jianshu.io/upload_images/3203841-92e800a3d56a5a84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 链接：
> [sublime text 3有多好用？](http://www.jianshu.com/p/24067c7330ae)

> Sublime是非常流行的一款代码编辑器，它拥有漂亮的用户界面和强大的功能，支持迷你地图、多选择、Python插件、代码高亮、代码收起等等，完全可自定义按键绑定

```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

sudo apt-get install apt-transport-https

echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list

sudo apt-get update
sudo apt-get install sublime-text

```

##### 安装Wireshark(网络分析工具)

> ![Wireshark](http://upload-images.jianshu.io/upload_images/3203841-3e8bf8ee81a67038.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




链接：["杀手级"抓包软件wireshark入门](http://www.jianshu.com/p/28035d90c3c8)

```
sudo add-apt-repository ppa:wireshark-dev/stable
sudo apt-get update
sudo apt intall wireshark

sudo wireshark
```




## 安装常用软件

##### 安装搜狗输入法

https://pinyin.sogou.com/linux/?r=pinyin



> ![搜狗输入法](http://upload-images.jianshu.io/upload_images/3203841-560caeaff7f6f561.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>下载后，会自动跳转到，安装指导页面，按照指示安装即可。


> ![搜狗](http://upload-images.jianshu.io/upload_images/3203841-298dafad6a629cf9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


安装完成后，默认按shift切换输入法，如果依然不出现，重启试试，如果依然不出现，就去系统设置，按下图调整设置




##### 安装网易云音乐

https://music.163.com/#/download





> ![网易云音乐](http://upload-images.jianshu.io/upload_images/3203841-0c39a827048c5856.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


网页云音乐，良心软件，下载后直接双击安装即可！


##### 安装ＷＰＳ
http://community.wps.cn/download/

![ＷＰＳ](http://upload-images.jianshu.io/upload_images/3203841-6935406412bac9b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下载后双击安装即可

##### 安装有道词典

http://cidian.youdao.com/index-linux.html


![有道词典](http://upload-images.jianshu.io/upload_images/3203841-c4744b70c45a4e67.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


下载后双击安装即可

##### 安装虚拟机软件virualbox



> ![虚拟机软件virualbox](http://upload-images.jianshu.io/upload_images/3203841-72a6c0779ee951d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 终端依次执行以下命令
```
sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian xenial contrib" >> /etc/apt/sources.list.d/virtualbox.list'

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

sudo apt update

sudo apt install virtualbox-5.1
```

##### 安装浏览器chrome(可以用来学编程)
链接：[用chrome学编程](http://www.jianshu.com/p/216539baebb8)


> ![浏览器chrome](http://upload-images.jianshu.io/upload_images/3203841-103e509dd99f5998.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 终端依次执行以下命令

```
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/

wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -


sudo apt-get update

sudo apt-get install google-chrome-stable

```


##### 安装视频播放器mpv


> ![播放器mpv](http://upload-images.jianshu.io/upload_images/3203841-18cdb095c7d83e6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 终端依次执行以下命令
```
sudo add-apt-repository ppa:mc3man/mpv-tests
sudo apt update
sudo apt install mpv
```

#####  安装ＱＱ


>  ![ＱＱ](http://upload-images.jianshu.io/upload_images/3203841-6aff06fc8af74e7a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



> 这一版的QQ并不好用，作者在虚拟机里安装的QQ

在文章底部找到我提供的资源包，下载后双击安装即可

##### 安装截图软件shutter


>  ![截图软件shutter](http://upload-images.jianshu.io/upload_images/3203841-e3daebdf94d80555.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update
sudo apt-get install shutter

```

#####安装动GIF图，截图软件Silentcast

> 效果

> ![GIF图软件Silentcast](http://upload-images.jianshu.io/upload_images/3203841-d8090e034408e37c.gif?imageMogr2/auto-orient/strip)


```
sudo add-apt-repository ppa:sethj/silentcast
sudo apt-get update
sudo apt-get install silentcast
```



#####  安装快速搜索工具Albert


> ![快速搜索工具Albert](http://upload-images.jianshu.io/upload_images/3203841-018b4784507a909b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install albert
```
`
##### 标题栏显示实时系统监控（安装indicator-sysmonitor）

> ![实时监控（indicator-sysmonitor）](http://upload-images.jianshu.io/upload_images/3203841-2a4bfb2b1bb8f5c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
sudo apt-get update
sudo apt-get install indicator-sysmonitor

indicator-sysmonitor
```


> 设置开机启动（重启生效！）
> 


> ![开机启动](http://upload-images.jianshu.io/upload_images/3203841-b24dc1aec53edd20.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



> 显示实时网速，CPU,内存，使用率`N:{net} C: {cpu} M: {mem}`


> ![配置显示,实时网速，CPU,内存](http://upload-images.jianshu.io/upload_images/3203841-0e1d8083ad7770f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 安装Steam
http://store.steampowered.com/about/

> ![Steam](http://upload-images.jianshu.io/upload_images/3203841-9a4db6024cff4c84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


下载后双击安装即可

－－－－先写这些，不定时更新－－－

> 文章涉及到的资源我会通过百度网盘分享，为便于管理,资源整合到一张独立的帖子，链接如下:
http://www.jianshu.com/p/4f28e1ae08b1