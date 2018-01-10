---
title: git遇到的问题
date: 2016-02-24 18:00:51
categories:
  - 新随笔
tags: [git]
---
最近有点闲，正好让我写写博客，熟悉下 `markdown` 加上把今天遇到的奇奇怪怪的问题记录下，从昨天下午开始至今天上午，一直在弄万恶的git 所出现的疑难杂症.
不久前建了个用 `gh-pages` 并且利用`hexo`搭建了个博客，就是此站点了...,
自从博客建好后，许久没有发布到远程，昨天一试，将写好的博客发布上去,既然提示说没有权限访问~~~~

提示如下

![](http://7xr7h9.com1.z0.glb.clouddn.com/blog4.png "assert函数效果图")
看着意思是需要 ` remote ` 呗，好吧，试了下

     $ git remote add origin git@github.com:***.git

<!--more-->


结果 ` git push  ` 时又报错，这是权限问题，提示如下，ai。。。 没爱了~~~不过还好，我继续百度吧
意思是说没有写入权限，这该怎么解决了，本地文件夹吗？设为了只读吗？还是远程设置了只读??? 不知道了~，继续百~
![](http://7xr7h9.com1.z0.glb.clouddn.com/blog11.png "assert函数效果图")

问群了，说是  `github ssh  `权限问题，是设置了  `ssh key  `, 好吧，把之前的key都删了吧，重新生成个key

运行如下：

    $ ssh-keygen -t rsa -C "username"

把key也拷到github上(右上角setting)，然后也拷到了本项目中的 <strong> `Deploy keys  `</strong>中

接下来再次push，我的天，换了个姿势继续报错中呢
![](http://7xr7h9.com1.z0.glb.clouddn.com/blog23.png "assert函数效果图")
说的是 密钥别拒绝，就是说还是没有写入的全选呗，完了，各种都试了，该咋办呐，百度吧
得出如下 ，不管了，运行看看

    eval `ssh-agent -s`
    ssh-add

push时真是急了，竟然还是不行，最后不懂英文的我，看了个国外的网站，英文不认识，但代码命令还是认识点的吧，哈哈~~

http://stackoverflow.com/questions/17846529/could-not-open-a-connection-to-your-authentication-agent
我看呐看，看到了个不一样的， `eval $(ssh-agent) ` 还说在win7下，我运行了，然后push,,,,
![](http://7xr7h9.com1.z0.glb.clouddn.com/blog2.png "assert函数效果图")

结果问题又来了，还真是问题源源不断呐，，，如图
![](http://7xr7h9.com1.z0.glb.clouddn.com/blog112.png "assert函数效果图")
输入什么都不管用，按 `ctrl+c `停止也不管用，百度不了吧这，果断问群，最后大神告诉 输入 `:q ` 回车


太棒了，push成功。。。。哦耶。。。顿时心情美美哒，感谢大神，节日给你大大的红包哈~
![](http://7xr7h9.com1.z0.glb.clouddn.com/blog18.png "assert函数效果图")

对于新手，其实挺讨厌看见各种报错，各种短路的，
明明之前都可以push,明明之前都一切正常，明明。。。只能说 ：现实是残酷的


不过还好最后完美的解决了，哈~哈~哈~