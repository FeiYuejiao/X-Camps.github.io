+++
title = "Hugo+Github+Netlify+freenom"
draft = "false"
description = "整套IT技术复盘"
categories = ["lession2"]
tag = ["fupan","IT"]
date = "2017-10-13"
+++

### 概述

只因我在群里炫耀了一句，于是招来了一个大活儿：在一个不冷不热的下午，面对一个从未接触过代码及相关工具的文科女，我花三个小时教会了她关于编辑器、Hugo、Git、Netlify、Freenom整套技术的使用方法，并成功帮其搭建了一个网站。<br/>

#### 话说“要把大象装冰箱，总共分三步。。。” 哪有那么简单的事儿，且听我慢慢道来吧！<br/>

* * *

### 第一步：轻松注册github
1，登录www.github.com，注册一个属于自己的账号；<br/>
2，新建一个库（repository）,假设库名（name）为myWeb，描述（description）可以不写；<br/>
3，新建成功后，把当时页面中的库地址和常用操作命令行例子copy下来，保存到自己的一个文本里备用。<br/>
* * *
### 第二步：搭建hugo环境（例：本机为win10系统为例）
1，在本机创建几个空目录（以C盘为例）：<br/>
	C:\hugo\ <br/>
	C:\hugo\bin\ <br/>
	C:\hugo\sites\ <br/>
2，查看本机的“我的电脑”的右键-属性：确定系统是64位 window10。<br/>
3，打开浏览器，进入 https://github.com/gohugoio/hugo/releases   找到 hugo_0.29_Windows-64bit.zip 版本并将其下载到本机。<br/>
4，将刚下载的 hugo_0.29_Windows-64bit.zip 解压后，将其 hugo.exe 文件copy到 C:\hugo\bin\ 中。<br/>
5，环境变量设置：<br/>
	a)“我的电脑”的右键-属性-左侧“高级系统设置”-环境变量，打开环境变量设置窗口；<br/>
	b)在窗口下半部分的“系统变量”总找到“Path”，双击其右侧的值，打开Path设置窗口；<br/>
	c)“新建”一个值：填入"C:\hugo\bin"<br/>
	d)一路确定，环境设置完毕。<br/>

6，顺便在网上百度并下载个notepad++编辑器，在本机安装作为编辑文件使用。<br/>
* * *
### 第三步：通过克隆（clone）现成主题，准备一个自己的博客型网站内容
1，浏览器地址栏输入https://github.com/feiyuejiao/x-camp/  能看到这个库的内容（这些库都是public的）<br/>
2，点击右上角的clone or download 按钮将整个x-camp网站下载到自己电脑上。<br/>
3，将x-camp的压缩包解压出来，其文件夹名默认是x-camp-master，为了好区分，将其改为你自己网站的名字myWeb，然后整体copy到C:\hugo\sites\下。<br/>
4，把C:\hugo\sites\myWeb\content\ 下的page和post目录下中一堆无关的文件和文件夹都删掉，保留about-me.md可以作为模板参考，可在里面编辑自己的title和内容。
   然后把about-me.md文件copy到post目录下，改个名字比如first.md，然后把里面的title和内容也改一改，加一些你自己想展示的文字。<br/>
5，把C:\hugo\sites\myWeb\static\ 下除了assets之外的其他内容都删掉，因为那都是x-camp的博客内容；<br/>
6，用编辑器打开 C:\hugo\sites\myWeb\config.toml，将title修改为自己的主题，并删除那几个[[menu.main]]中明显属于x-camp的几块，比如rules、学员名单；<br/>
7，通过windows的“开始-cmd”打开dos控制台窗口，首先cd 到 C:\hugo\sites\myWeb 目录下；<br/>
8，然后在控制台中输入hugo回车（这一步是编译本地网站），等待执行完毕，此时你会发现 C:\hugo\sites\myWeb\ 下多了一个public文件夹以及里面的很多内容，不用去管。<br/>
9，然后在控制台中输入hugo server（这一步是运行本地网站），等待执行完毕，会提示你网站已经在本机启动运行（通过ctrl+c可以停止），地址为localhost:1313。<br/>
10，在浏览器中输入 localhost:1313，恭喜你，你可看到自己的第一个网站了！是不是很神奇？<br/>
    只不过这个网站是在你本机上运行的，这个网址只对你自己有用，别人看不到的。要想让你的网站运行在公网上让别人也看到，那就要借助git和netlify了。<br/>
* * *
### 第四步：用git将网站内容上传到github库
git的使用是这一系列技术当中，相对来说难度最大的环节，命令行复杂抽象，容易出错，还要长期用到，对非技术人员来说就是天书，何况是女生。。。<br/>
1，打卡网址 https://msysgit.github.com ，点“download”按钮，网页会自动判断你的操作系统，并自动给你下载对应版本的git安装包（我的是Git-2.14.2-64-bit.exe）。<br/>
2，正常安装过程，一路默认（中间有个创建桌面快捷方式的选项，可以选上，方便使用）；<br/>
3，安装完毕后，在“开始-所有程序-Git”中，可以看到有三个git应用入口，我习惯命令行，所以我把“Git bush”用右键拖到桌面上作为快捷方式。<br/>
4，打开git bush(以后简称git），首先cd 到  C:\hugo\sites\myWeb 目录下，依次输入运行一下命令：<br/>

	git init // 初始化库 <br/>
	git add . //添加所有文件准备上传 <br/>
	git commit -m'First commit' //申请提交 <br/>
		注意：初次使用，此时可能会提示你使用下面命令来输入你在github上的邮箱、账号名<br/>
		git config --global user.email "you@example.com"<br/>
		git config --global user.name "Your Name"<br/>
		注：执行完上述命令后，可能还会弹出登录github账号密码的提示框，你正常登录就行了。<br/>
		
	git remote add origin https://github.com/<账号名>/myWeb.git  
		//这一步是将本地的库关联到你在github上新建的库，这个url你在建库的时候copy过。<br/>
	git push origin master  
		//将准备提交的所有文件传送到github关联库中（master代表主分支，不解释）<br/>
	
5，然后就是等。。。执行完毕后，看提示100%上传了就到网址："https://github.com/<账号名>/myWeb" 里看一眼，正常来说，你本地网站上的内容已经上传成功。<br/>

当然，使用git的过程经常会由于一些不确定因素导致各种问题和失败，除了考研你的智慧之外，我总结如下：
##		看反馈、思可能、RSA、多试试！<br/>

* * *
### 第五步：用Netlify发布大家看得见的网站
首先，这里有两个关系我提醒一下：Github跟hugo是好基友；而Netlify跟Github也是好基友（当然它的基友不止这一个）。<br/>
别问我为什么，我们只管用就行了。步骤如下：<br/>

1，打开网址 www.netlify.com，点击首页上的“Get start for free”按钮，如果是初次进入，就进到了登录页面；<br/>
2，在登录页面上点击上面第一个按钮：Github  （这一步的意思是用Github的第三方账户登录）；<br/>
3，接下来，需要第三方账户登录和授权（在同一个浏览器下，netlify会探测到你已登录github，直接要求你授权），你点授权（Authorized）就行了；<br/>
4，接下来点击“New site from git”按钮（那么大一个按钮，别说看不见）；<br/>
5，接下来再选一次“Github”，然后可能还需要你再点击同意授权；<br/>
6，然后你就看到了你的Github账户名以及你刚新建并已经上传了网站文件的那个库：<账户名>/myWeb； 不用犹豫，点它；<br/>
7，接下来页面会让你填两个空：build command （填：hugo）和Publish directory（填：public），照我说的填，别问什么；<br/>
8，完成后点击“deploy site”按钮，netlify开始执行编译网站，等待。。。<br/>
9，等页面自动跳转，你会发现上面有一行橙色字体：“Site deploy in progress”，它下面有两个带小齿轮的按钮，此时请你点击左边那个“Site settings”；<br/>
10，在setting页面找左侧列表中的“Build&deploy”，点击它；<br/>
11，然后看右侧出现的页面，向下拉一拉，会发现有个"Build environment variables"部分，点击这部分底部的那个“Edit variables”按钮；<br/>
12，再点开的两个输入框中：左边的输入 HUGO_VERSION，右边的输入 0.29 ，然后点保存（save）。<br/>
13，然后点两次返回，返回到第9步的那个页面，刷新页面，发现橙色字体变成了红色字体“Site deploy failed”；<br/>
14，点击这行红色字体，页面右端出现一个“Trigger deploy”按钮，点击它，弹出框中再继续点“Trigger deploy”，就会重新执行编译；<br/>
15，然后等。。。十几秒钟后依然没反应，就刷新该页面，如果页面上方显示"Published deploy"，类似下图的内容（如果不是这样，那就继续等会儿再刷新）：<br/>
<img src="/post/published_deploy.png"/><br/>
说明你的网站编译成功了，而那个类似“https://xxxx-xxxx-xxxxx.netlify.com” 的网址，就是你的blog类型网站的公开网址，点开看看，是不是成功了？<br/>
#### 恭喜你，你的网站整个互联网都能看到了！前提是他们知道并要输入这个复杂的网址。。。<br/>

16，怎么样让网址变得简单易记呢？这就要用到freenom了，不得不说：freenom和netlify也是好基友。。。<br/>

* * *
### 第六步：用freenom申请你的免费域名并关联指向你自己刚刚发布的网站
##### 时间已经过去了三个小时。。。还剩最后半小时了。。。

1，首先打开www.freenom.com（国外网站，有时候网很慢，甚至连不上）；<br/>
2，然后请输入一个你想要的域名，比如gebilaowang.tk（因为tk可以免费用一年），具体步骤请参考一篇很不错的教程文章：
<a href="https://www.freehao123.com/freenom-tk-ml-ga-cf-gq/">新Freenom免费域名申请与DNS解析设置</a><br/>
 但是，这个教程中有几步我需要强调以下几点（不然你还可能在某些地方懵逼）：<br/>
#####  a）在文章第一条、第6步中，填好邮箱然后点“验证邮箱”按钮后，一定要用你的PC浏览器去登录你的邮箱，点击里面的验证连接，会直接跳到freenom页面，顺着填写信息、往下操作就行了。否则在手机中那么多信息填起来很不方便，万一出什么幺蛾子，当你再回到PC登录邮箱，这个验证就可能会成为僵尸连接。<br/>
##### b）文章中最后设置第三方DNS的过程是以DNSPOD为例的，而我们要用netlify的NS服务器，所以你看文章时，只需要跳着看如下两处内容就足够了：<br/>
	第三条第1步 直接跳到 第四条第2步。

但是，第四条第2步中要输入的几个NS服务器当然不能填DNSPOD的（那是教程的例子），而应该填netlify的，怎么获取这几个服务器呢？别急，应该恭喜一下，现在至少你已经拥有了一个自己的域名gebilaowang.tk！跟着我往下走。。。
	
3，打开www.netlify.com，刚才登陆过，所以你能在这个页面看到你刚搭建成功的那个网站 https://xxxx-xxxx-xxxxx.netlify.com <br/>
4，点击它，进入这个网站的配置页面，会看到类似下图所示：<br/>
<img src="/post/published_deploy2.png"/><br/>
5，点击“Domain settings”按钮，新页面中继续点击“Set a custom domain”按钮，在输入框中填入你刚申请的域名 gebilaowang.tk ，然后点保存（Save）。<br/>
6，然后继续点击“Use Netlify DNS”按钮，几秒种后就会出现类似下面的一列NS服务器（通常就是四个）：<br/>
dns1.p08.nsone.net<br/>
dns2.p08.nsone.net<br/>
dns3.p08.nsone.net<br/>
dns4.p08.nsone.net<br/>
##### 	注意：这四个NS服务器对于每个人的网站都可能不同，直接抄我的没用。。。

7，回到freenom里，按照前面我推荐的教程文章中的第四条第2步，将你从netlify从获得的这四个NS服务器分别copy到前四个输入框中，点下面的按钮即刻生效。<br/>
8，一切就绪：你在浏览器中输入你的域名网址：<a href="http://gebilaowang.tk">gebilaowang.tk</a>，你自己的网站将会神奇的呈现在你面前！（这个网站和你长得不一样，不要奇怪，因为我用了不同的模板）<br/>
## 到此为止，大功告成，激动不？

* * *
### 最后：出于良知，我再说说如何在这个网站中更新blog（俗称“帖子”）
1，在C:/hugo/sites/myWeb 中，content里用编辑器修改任何一个.md的文档，或者增加新的.md文档，保存；<br/>
2，打开git bush控制台，cd到C:/hugo/sites/myWeb 下；<br/>
3，依次执行下列命令：<br/>

	git add .
	git commit -m‘xxxxxx’ //引号里面就是个备注，随便填点什么，便于查看提交历史
	git push origin master
	
#####  齐活儿！维护一个自己的blog 就这么简单！再不懂就问度娘和谷哥，一直写到大半夜，哥也累了。。。

* * *
## 结束语：桃李不言，下自成蹊，基因传播，子孙满堂。。。别问我是谁，我是雷锋~

