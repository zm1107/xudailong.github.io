---
layout: post
title:  中国大学MOOC：《三国演义》人物出场次数统计
date:   2019-04-25 21:34:54 +0800
categories: 技术 学习
tags: python 编程 
excerpt: 嵩天老师给的答案，第20名是夏侯惇，我算出来前20里面，多个刘禅，就挤掉了夏侯惇		
mathjax: true
---

《三国演义》人物出场次数统计：

无关词语已经加入excludes集合

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @File  : 三国演义出场人物统计.py
# @Time  : 2019-04-25 21:28
# @Author: weibaba    
# @Site  : http://www.weibaba.org
import jieba
file_name = "../resource/threekingdoms.txt"
txt  = open(file_name,"r",encoding="utf-8").read()
excludes={"将军","将军","却说","荆州","二人","不可","不能","如此","这般","不久","商议","如何","主公","军马","引兵","军士","左右","次日",\
          "大喜","天下","东吴","于是","今日","不敢","魏兵","陛下","一人","人马","不知","汉中","只见","众将","蜀兵","上马","大叫","太守",\
          "此人","夫人","先生","先主","后人","城中","背后","天子","一面","何不","大军","忽报","百姓","何故","然后","先锋","不如","赶来",\
          "原来","令人","江东","下马","喊声","正是","徐州","忽然","因此","成都","不见","未知","大败","之后","大事","一军","引军","起兵",\
          "以为","大怒","不得","军中","接应","进兵","大惊","可以","心中","下文","一声","追赶","粮草","一齐","分解","回报","分付","只得",\
          "出马","三千","大将","许都","随后","报知","前面","之兵","且说","众官","洛阳","领兵","何人","星夜","精兵","城上","之计","不肯",\
          "相见","其言","一日","而行","文武","襄阳","准备","若何","出战","亲自","必有","此事","之中","伏兵","祁山","乘势","忽见","大笑",\
          "樊城","兄弟","结义","首级","立于","西川","朝廷","三军","大王","传令","当先","五百","一彪","坚守","此时","之间","投降","五千",\
          "埋伏","长安","三路","遣使","回见","大将军","必然","将士","是夜","小路","英雄","望见","无不","有人","马下","江南","下寨",\
          "杀出","中原"}
words = jieba.lcut(txt)
counts = {}
for word in words :
    if len(word) == 1 :
        continue
    elif word =="诸葛亮" or word =="孔明曰" or word == "卧龙" or word == "孔明":
        rword = "孔明"
    elif word == "关公" or word == "云长" or word == "云长曰":
        rword = "关羽"
    elif word == "阿斗" or word == "后主":
        rword = "刘禅"
    elif word == "玄德" or word == "玄德曰" or word == "刘皇叔" :
        rword = "刘备"
    elif word == "孟德" or word == "丞相" :
        rword = "曹操"
    elif word == "子龙" or word == "子龙曰" or word == "赵子龙" or word == "赵云" :
        rword = "赵云"
    elif word == "翼德" or word == "翼德曰":
        rword = "张飞"
    elif word == "士元" or word == "凤雏" or word == "士元曰":
        rword = "庞统"
    elif word == "仲谋" or word == "仲谋曰":
        rword = "孙权"
    elif word == "奉先" or word == "温侯" or word == "吕布曰" or word == "奉先曰" :
        rword = "吕布"
    elif word == "公瑾" or word == "都督" or word == "公瑾曰":
        rword = "周瑜"
    else :
        rword = word
    counts[rword] = counts.get(rword,0) + 1
for word in excludes :
    del counts[word]

list_number = eval(input("你需要显示前多少位出场人物？"))
items = list(counts.items())
items.sort(key=lambda x:x[1],reverse=True)
for i in range(list_number) :
    word,count=items[i]
    print("第{0:^5}位 姓名：{1:<6},一共出场{2:<4}次".format(i+1,word,count))
```

运行结果：

```shell
Building prefix dict from the default dictionary ...
Loading model from cache C:\Users\zm110\AppData\Local\Temp\jieba.cache
Loading model cost 1.389 seconds.
Prefix dict has been built succesfully.
你需要显示前多少位出场人物？20
第  1  位 姓名：曹操    ,一共出场1451次
第  2  位 姓名：孔明    ,一共出场1425次
第  3  位 姓名：刘备    ,一共出场1288次
第  4  位 姓名：关羽    ,一共出场784 次
第  5  位 姓名：周瑜    ,一共出场470 次
第  6  位 姓名：张飞    ,一共出场376 次
第  7  位 姓名：赵云    ,一共出场352 次
第  8  位 姓名：吕布    ,一共出场311 次
第  9  位 姓名：孙权    ,一共出场266 次
第 10  位 姓名：刘禅    ,一共出场255 次
第 11  位 姓名：司马懿  ,一共出场221 次
第 12  位 姓名：袁绍    ,一共出场191 次
第 13  位 姓名：马超    ,一共出场185 次
第 14  位 姓名：魏延    ,一共出场180 次
第 15  位 姓名：黄忠    ,一共出场168 次
第 16  位 姓名：姜维    ,一共出场151 次
第 17  位 姓名：马岱    ,一共出场127 次
第 18  位 姓名：庞德    ,一共出场122 次
第 19  位 姓名：孟获    ,一共出场122 次
第 20  位 姓名：刘表    ,一共出场120 次

Process finished with exit code 0
```

