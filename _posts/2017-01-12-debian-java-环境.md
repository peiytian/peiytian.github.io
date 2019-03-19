---
layout: post
title:  "debian 安装java环境"
date:   2017-01-12 11:31:01 +0800
categories: java
tag: java
---

* content
{:toc}


1. 首先切换到root用户
```
su root
```

获取root用户权限，当前工作目录不变(需要root密码)
2. 在usr目录下建立java安装目录
```
　　cd /usr
　　mkdir java
```
3. 将jdk-8u60-linux-x64.tar.gz拷贝到java目录下(这里需要自己去官网下载java jdk 二进包)
　

```
cp /mnt/hgfs/linux/jdk-8u60-linux-x64.tar.gz /usr/java/
```
4. 解压jdk到当前目录,得到文件夹 jdk1.8.0_*　　(注意：下载不同版本的JDK目录名不同！)
```
　　tar -zxvf jdk-8u60-linux-x64.tar.gz
```
5. 安装完毕为他建立一个链接以节省目录长度
```
　　ln -s /usr/java/jdk1.8.0_60/ /usr/jdk
```
6. 编辑配置文件，配置环境变量
```
　　vim /etc/profile
```

在文本的末尾添加如下内容：
```
JAVA_HOME=/usr/jdk
CLASSPATH=$JAVA_HOME/lib/
PATH=$PATH:$JAVA_HOME/bin
export PATH JAVA_HOME CLASSPATH
```
7. 重启机器或执行命令 ：
```
    source /etc/profile
　　sudo shutdown -r now
```
8. 查看安装情况

　　`java -version`

出现下面文字:证明已经成功
```
　　java version "1.8.0_60"
　　Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
　　Java HotSpot(TM) Client VM (build 25.60-b23, mixed mode)
```