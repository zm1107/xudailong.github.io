---
layout: post
title:  "中国大学MOOC：python语言程序设计学习笔记（01）"
date: 2018-05-16 01:14:54 +0800 #时间bug，换算后UTC日期会超出
categories: 技术
tags: python 笔记
excerpt: Python基本图形绘制，turtle库与简单的循环语句
mathjax: true
---



python计算生态=标准库+第三方库
标准库：随解释器直接安装到操作系统中的功能模块。
第三方库：需要经过安装才能使用的功能模块。

库：Library、包：Package、模块：Module，统称为模块（入门级）。

##turtle库基本介绍
turtle绘图体系：1969年诞生，也叫做海龟绘图体系。
python的标准库

### turtle绘图窗体
最小单位是1像素
计算机屏幕左上角坐标为（0,0）
turtle.setup(width，heigth,startx,starty)
原点在绘图窗口的左上角
如果不指定原点位置，默认原点在屏幕中心。
如
turtle.setup(400,300)

turtle空间坐标体系

绝对坐标：海龟初始位置（原点），在窗口中心


turtle.goto(x,y)

``` py
import turtle
turtle.goto(100, 100)
turtle.goto(100,-100)
turtle.goto(-100,-100)
turtle.goto(-100,100)
turtle.goto(0,0)

```


### import 


### ​range()函数
``` py
range(N)  #作用：产生0至N-1的整数序列，共N个
# 例如：
range(5) #产生0,1,2,3,4
# 产生0，1，2，3，4 共五个数字序列


range(M,N)  #作用：产生M到N-1的整数序列，共N-M个
···



