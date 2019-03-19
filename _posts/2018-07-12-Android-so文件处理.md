---
layout: post
title:  "android so文件处理"
date:   2018-07-12 11:31:01 +0800
categories: java
tag: android
---

* content
{:toc}




##### android so文件处理

如果项目只包含了 armeabi，那么在所有Android设备都可以运行； 如果项目只包含了 armeabi-v7a，除armeabi架构的设备外都可以运行； 如果项目只包含了 x86，那么armeabi架构和armeabi-v7a的Android设备是无法运行的； 如果同时包含了 armeabi， armeabi-v7a和x86，所有设备都可以运行，程序在运行的时候去加载不同平台对应的so，这是较为完美的一种解决方案，同时也会导致包变大。