---
layout: post
title: "vscode中python配置"
date:   2021-3-13
tags: [geek]
comments: true
author: yikun
---

问题：在安装好python插件及配置好json文件后，发现一些包如opencv、numpy在vscode按F5运行时无法导入。错误及提示如下：

![image-20210305145217795](C:\Users\86135\AppData\Roaming\Typora\typora-user-images\image-20210305145217795.png)

解决思路：在最开始经过拖延及一顿乱搞之后，只发现了vscode的F5键和run code按钮不太一样，然而这个并无卵用。

没有办法，只能强迫着自己看报错提示，发现提示给得也太详细了。。。。

检查到F5用的python版本(3.8)和自己装在环境里的版本(3.7.0)不一样后，发现了问题。经过网上搜索，知道Anaconda自带了一个python.exe，即F5键使用的；而自己使用的是3.7.0版本的，通过“pip list”查询安装的包发现，果然numpy、opencv包都装在3.7.0版本的python.exe里。因此接下来只要让F5启用环境中的python.exe即可。

![image-20210305153103083](C:\Users\86135\AppData\Roaming\Typora\typora-user-images\image-20210305153103083.png)

在设置中点击右上角“打开设置json”按钮，生成settings.json文件。

![image-20210305153209466](C:\Users\86135\AppData\Roaming\Typora\typora-user-images\image-20210305153209466.png)

添加上述内容更改使用的python路径为3.7.0的python.exe，发现可以成功导入numpy、cv2，问题得到解决。

还有一个小bug是，打开的目录是OpenCVcourse，运行lab1下的test1.py文件，会找不到test.png(vscode错当成是OpenCVcourse下的test.png)，可以在lanuch.json文件下添加以下配置：

![image-20210305154456115](C:\Users\86135\AppData\Roaming\Typora\typora-user-images\image-20210305154456115.png)



心得：一定要学会看报错信息！！这应该是解决问题最快的方式了。