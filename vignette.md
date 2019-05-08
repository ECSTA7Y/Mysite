---
title: "如何提取R包中的小品文"
author: " "
date: 2019-05-07
slug: vignette
categories: ["R"]
tags: ["R Markdown", "plot", "regression"]
---

```{r intro,include = F}
setwd('C:/Users/xsong/Desktop/table/new/vignette')
```

用R实现各种分析任务需要学习不同的R包。而学习R包实现方法的同时必须同时结合理论。因此仅仅看帮助文档和用户手册（Reference manual）是远远不够的。作为学习R包的重要资源，小品文（Vignettes，或翻译为简介）将统计理论、代码与示例相结合，是学习数据分析的不可多得的好材料。下文将以rpart包为例讲解如何获取R包的官方小品文。  

在CRAN上发布的R包往往会有一个官方主页。在搜索引擎中键入R rpart或CRAN rpart便能够找到此包主页。 

rpart的官方主页如下所示：  

![ ](Capture.png)

其中，Downloads下便有用户手册和小品文的下载按钮，点击即可下载。  

![ ](Capture2.png)

但，这种方法其实是多此一举了！

因为我们在下载R包时，已经将小品文下载下来了。我们可以使用utils包中的vignette函数自动提取小品文。但首先我们需要提取R包的小品文名称，代码如下：  

```{r a,message = F,prompt=T,warning = F, include = T,error = T,echo = T,eval = F}
#install.packages('utils')#没安装先安装包
#library(utils)#加载包
vignette(, package = "rpart")#提取rpart包的小品文名称

```

输出结果如下所示：  


```{r b,warning = F,prompt = T, include = T,error = T,echo = T,eval = T,results = 'hide'}
Vignettes in package ‘rpart’:

longintro   Introduction to Rpart 
            (source, pdf)
usercode    User Written Split
            Functions (source, pdf)
```

可以发现，rpart包有两篇小品文，《Introduction to Rpart》和《User Written Split Functions》。分别简称为"longintro"和"usercode"。现在，就可以根据简称提取小品文了，输入：

```{r c,message = F,prompt=T, include = T,error = T,echo = T,eval = F,results = 'hide'}
vignette("longintro", package = "rpart")
```

第一篇《Introduction to Rpart》的pdf便会自动跳出：  
![ ](Capture3.png)
  
便可以阅读了。

很多R包的小品文是pdf版本，当然还有很多是html版的，如ggplot2的小品文：  


```{r d,message = F,prompt=T, include = T,error = T,echo = T,eval = F,results = 'hide'}
vignette("ggplot2-specs", package = "ggplot2")
```
  
![ ](Capture4.png)
  
看起来这个小品文是用R Markdown写的。






