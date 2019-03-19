---
layout: post
title:  "java.lang.NoClassDefFoundError"
date:   2019-11-12 11:31:01 +0800
categories: java
tag: android
---

* content
{:toc}




Android中引入第三方Jar包的方法(java.lang.NoClassDefFoundError解决办法)
1. 在工程下新建lib文件夹，将需要的第三方包拷贝进来。
2. 将引用的第三方包，添加进工作的build path。
3. （关键的一步）将lib设为源文件夹。如果不设置，则程序编译可以通过，但运行的时候，会报：
java.lang.NoClassDefFoundError