---
layout: post
category : Linux
tags : [Linux， CLI， 我爱命令行]
date: 2013-12-29 18:40:00
---
{% include JB/setup %}

古语有云：不会命令行的码农不是好的设计师。在命令行下把键盘敲的啪啪响，那是一种怎样的逼格？为了体现自己苦逼的码农身份，同志们，我们必须把命令行学会学好！！

怎么才能用好命令行？当然是要用*NIX的操作系统了！！什么？要网购？要看片？要游戏？没关系，我们有[Cmder](http://bliker.github.io/cmder/)！！

我们可以用Cmder在Windows下模拟Linux的Shell，大家看下面的图感受一下：

![](http://bliker.github.io/cmder/img/git_thumb.png)

下面跟着老残我一步一步整起来，走起！

	1. 下载Cmder：
		http://bliker.github.io/cmder/
		可以下载一个完整的安装包，这样基本命令，包括git就都全了。
	2. 解压缩：
		C:\cmder
		貌似不能解压缩到“Program Files”，带空格的不认。
	3. 运行Cmder.bat
	
以上三步其实就已经把cmder给用起来了，大家可以执行ls、pwd感受下。 就这么简单？就这么简单！

如果嫌自带的命令不够，本着不作死就不会死的精神一定要尽情折腾的话，用Chocolatery吧。

	1. 安装
		@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%systemdrive%\chocolatey\bin
	2. 没有了

装好了咋用啊？

很简单：

	装vim：
		cinst vim
	装node.js：
		cinst nodejs.install

具体有多少package能装，自己上http://chocolatey.org/去看吧。另外，用clist可以搜索支持的package，比方说我要装ruby的devkit，可以clist devkit。

有些在中文Windows环境下折腾的tx也许会发现ls出来的中文文件目录咋全是问号呢？执行一条命令出来的中文提示咋都挤在一块看不清楚呢？vi打开的中文文件咋都是乱码呢？

小意思！！

	1. 在Cmder窗口右键打开Settings，把‘Monospace’勾选去掉。
	2. 编辑cmder安装目录下的config/aliases，加上：
		ls=ls --show-control-chars -F --color $*
		ll=ls -alF --show-control-chars
		实际上起作用的就是--show-control-chars，这个比较苦逼。
	3. 编辑~/.vimrc，没有这个文件的就新建一个，加上：
		let &termencoding=&encoding
		set fileencodings=utf-8,gbk

好了。再ls、vim看看感受一下。
