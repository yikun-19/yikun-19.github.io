---
layout: post
title: "《趣味算法》学习"
date:   2021-3-14
tags: [algorithm]
toc: true
comments: true
author: yikun
---



﻿@[TOC](文章目录)

<hr style=" border:solid; width:100px; height:1px;" color=#000000 size=1">

# 一、算法之美
## 1.1 打开算法之门
  瑞士著名的科学家 N.Wirth 教授曾提出：数据结构+算法=程序。

  数据结构是程序的骨架，算法是程序的灵魂。

## 1.2 算法复杂性
  算法只是对问题求解方法的一种描述，它不依赖于任何一种语言，既可以用自然语言、程序设计语言（C、C++、Java、Python 等）描述，也可以用流程图、框图来表示。一般为 了更清楚地说明算法的本质，我们去除了计算机语言的语法规则和细节，采用“伪代码”来描述算法。

算法具有以下特性： 
（1）**有穷性**：算法是由若干条指令组成的有穷序列，总是在执行若干次后结束，不可能永不停止。 
（2）**确定性**：每条语句有确定的含义，无歧义。 
（3）**可行性**：算法在当前环境条件下可以通过有限次运算实现。 
（4）**输入输出**：有零个或多个输入，一个或多个输出。

有些算法，如排序、查找、插入等算法，可以分为最好、最坏和平均情况分别求算法渐近复杂度，但我们考查一个算法通常考查最坏的情况，而不是考查最好的情况。**最坏情况对衡量算法的好坏具有实际的意义。**

空间复杂度：算法占用的空间大小。一般将算法的辅助空间作为衡量空间复杂度的标准。 空间复杂度的本意是指算法在运行过程中占用了多少存储空间。算法占用的存储空间包括： 
（1）**输入/输出数据**； 
（2）**算法本身**； 
（3）**额外需要的辅助空间**。
 输入/输出数据占用的空间是必需的，算法本身占用的空间可以通过精简算法来缩减， 但这个压缩的量是很小的，可以忽略不计。而在运行时使用的辅助变量所占用的空间，即**辅助空间是衡量空间复杂度的关键因素**。

注意：递归算法中，每一次递推需要一个栈空间来保存调用记录，因此，空间复杂度需要计算**递归栈的辅助空间**。
<font color=#999AAA >提示：这里通过求n的阶乘问题简单分析了递归算法的思路和执行过程。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200928173825604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)

## 1.3 魔鬼序列
引入问题1：
**一棋盘的麦子问题**。问题关键在于对2的幂次求和。由此体现出指数的增长威力，并引出了常见的算法的阶：
（1）**常数阶**
（2）**多项式阶**
（3）**指数阶**
（4）**对数阶**
它们之间的关系为：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200928174333122.png#pic_center)
引入问题2：
**兔子数列问题**。初步考虑，可由如下递推关系设计递归算法：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200928174540343.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
分析该算法的时间复杂度时，由F(n)的通项公式，知是指数阶的：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200928174731774.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
尝试对该算法进行改进：
将递归的过程改为迭代的过程，即F(n)由F(n-1)和F(n-2)得出，而不用每次都追溯到F(1)和F(2)，这样减少了大量的重复运算，时间复杂度由指数阶降到了多项式阶。
<font color=#999AAA >提示：斐波那契数列的时间复杂度还可以降低到对数阶，这里不深入讨论。
</font>
## 1.4 几道数学题
引入问题1：
**马克思手稿中的数学题**。马克思手稿中有一道趣味数学问题：有 30 个人，其中有男人、女人和小孩，这些人在一家饭馆吃饭花了 50 先令；每个男人花 3 先令，每个女人花 2 先令，每个小孩花 1 先令； 问男人、女人和小孩各有几人？

![](https://img-blog.csdnimg.cn/20200929123509495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
**对以上方程组变换的理解**：两个三维平面，相交于一条三维直线，两个方程联立得到的组合即为过该直线的平面系，消去z表示所得的一个平面是垂直于xoy平面且过直线的平面，用该平面及初始一个平面又可以回得相交直线。

引入问题2：
**爱因斯坦的台阶**。爱因斯坦家里有一条长阶梯，若每步跨 2 阶，则最后剩 1 阶；若每步跨 3 阶，则最后剩 2 阶；若每步跨 5 阶，则最后剩 4 阶；若每步跨 6 阶，则最后剩 5 阶。只有每次跨 7 阶，最后才正好 1 阶不剩。请问这条阶梯共有多少阶？
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929123852352.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
**算法改进**：考虑到从1开始以步长为1递增寻找答案是不必要的，可以以步长为7递增寻找答案，降低常数。更进一步地，可以以2、3、5、6的公倍数t为步长，检验k*t - 1是否为7的倍数即可。

引入问题3：
**哥德巴赫猜想**。任一大于 2 的偶数，都可表示成两个素数之和。 
验证：2000 以内大于 2 的偶数都能够分解为两个素数之和。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929125207399.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929125235562.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929125436206.png#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929125330347.png#pic_center)

## 1.5 章节小结
（1）将程序执行次数作为时间复杂度衡量标准。 
（2）时间复杂度通常用渐近上界符号 f(n)表示。 
（3）衡量算法的好坏通常考查算法的最坏情况。 
（4）空间复杂度只计算辅助空间。 
（5）递归算法的空间复杂度要计算递归使用的栈空间。 
（6）设计算法时尽量避免爆炸级增量复杂度。




# 二、贪心算法
## 2.1 贪心算法概述
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200929130257401.png#pic_center)经过实践我们发现，利用贪心算法求解的问题往往具有两个重要的特性：**贪心选择性质**和**最优子结构性质**。若满足这两个性质就可以使用贪心算法了。
（1）**贪心选择**
  所谓贪心选择性质是指**原问题的整体最优解可以通过一系列局部最优的选择得到**。应用同一规则，将原问题变为一个相似的但规模更小的子问题，而后的每一步都是当前最佳的选 择。这种选择依赖于已做出的选择，但不依赖于未做出的选择。运用贪心策略解决的问题在程序的运行过程中无回溯过程。

（2）**最优子结构**
当**一个问题的最优解包含其子问题的最优解时**，称此问题具有最优子结构性质。问题的最优子结构性质是该问题是否可用贪心算法求解的关键。
例如原问题 S={a1，a2，…，ai，…，an}，通过贪心选择选出一个当前最优解{ai} 之后，转化为求解子问题 S−{ai}。

使用贪心算法，主要是以下三个步骤：
（1）**确定贪心策略**
因此根据求解目标不同，贪心策略也会不同。
（2）**得到局部最优解**
根据贪心策略，一步一步地得到局部最优解
（3）**合成全局最优解**
把所有的局部最优解合成为原来问题的一个最优解（a1，a2，…）。

如冒泡排序就采用了贪心策略。
## 2.2 最优装载问题
**问题描述**：有一批集装箱要装上一艘载重量为c的轮船。其中集装箱i的重量为Wi。最优装载问题要求确定在装载体积不受限制的情况下，将尽可能多的集装箱装上轮船。
**算法设计**：将集装箱按重量排序，每次选择剩余集装箱中重量最小的一个装入轮船，直至达到最大载重量或者集装箱全部装完时停止。
**算法优化思考**：尝试分析该问题的贪心选择性质及最优子结构性质，借此分析贪心算法的正确性。同时，也可以根据反证法，得出该算法的正确性。
## 2.3 背包问题
**问题描述**：给定n个物品和一个容量为C的背包，物品i的重量是Wi,其价值为Vi,背包问题是如何选择入背包的物品，使得装入背包的物品的总价值最大，注意和0/1背包的区别，在背包问题中可以将物品的一部分装入背包，但不能重复装入。
**算法设计**：![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001115745704.png#pic_center)
分析可知，第三种贪心策略是可行的。因此选择先把各种物品按价质比排序，优先装入价值比高的物品入背包，直至背包被装满或物品全部装入时停止。
**算法实现技巧**：
（1）用一个结构体来描述一个物品，用结构体数组来描述物品集合。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001120124673.png#pic_center)
（2）巧用STL中内置的sort()函数(两个参数的sort()函数默认升序排列)：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001120253315.png#pic_center)
**sort()函数可以这样认为：排序后的序列，从左到右方向上，任意两个相邻元素(相等除外)应用cmp()函数得到的返回值为1。**

**算法优化思考**：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001120551193.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
## 2.4 会议安排
**问题描述**：在会议安排中，每个会议 i 都有起始时间 bi和结束时间 ei，且 bi<ei，即一个会议进行的时间为半开区间[bi，ei）。如果[bi，ei）与[bj，ej）均在“有限的 时间内”，且不相交，则称会议 i 与会议 j 相容的。也就是说，当 bi≥ej或 bj≥ei时，会议 i 与会议 j 相容。会议安排问题要求在所给的会议集合中选出最大的相容活动子集，即尽可能在有限的时间内召开更多的会议。
**算法设计**：我们可以考虑以下的贪心策略：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001122235385.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
经过考虑后，我们需要选择**开始时间早+持续时间短**的会议，即选择结束时间早的会议作为算法的贪心策略。
**算法实现重点部分**：
（1）对会议集合按结束时间升序排列：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001122903735.png#pic_center)
（2）每次按贪心策略从排序后的序列中选择：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201001123020959.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYW1vemhpeWk=,size_16,color_FFFFFF,t_70#pic_center)
**算法优化思考**：暂无。

## 2.5 最短路径
## 2.6 哈夫曼编码
## 2.7 最小生成树

<font color=#999AAA >示例：pandas 是基于NumPy 的一种工具，该工具是为了解决数据分析任务而创建的。



# 三、分治法
## 1.引入库


<font color=#999AAA >代码如下（示例）：



```c
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')
import  ssl
ssl._create_default_https_context = ssl._create_unverified_context
```

## 2.读入数据

<font color=#999AAA >代码如下（示例）：



```c
data = pd.read_csv(
    'https://labfile.oss.aliyuncs.com/courses/1283/adult.data.csv')
print(data.head())
```



<font color=#999AAA >该处使用的url网络请求的数据。

<hr style=" border:solid; width:100px; height:1px;" color=#000000 size=1">


# 四、动态规划
# 五、回溯法
# 六、分支限界法
# 七、线性规划网络流
# 总结
<font color=#999AAA >提示：这里对文章进行总结：
例如：以上就是今天要讲的内容，本文仅仅简单介绍了pandas的使用，而pandas提供了大量能使我们快速便捷地处理数据的函数和方法。
