---
layout: post
title:  "android 包相关命令签名工具"
date:   2017-03-12 11:31:01 +0800
categories: java
tag: android
---

* content
{:toc}


---

- 查看包相关信息

```
aapt dump badging .apk
```
- android 签名

```
jarsigner -verbose -keystore test.keystore -signedjar -TestSigned.apk TestSign.apk test
```

- android 查看证书签名

```
keytool -list -keystore -v -keystore D:\workspace\BH_YB_SFSS_DAT-AS\FastInsSS -v
keytool -list -keystore -v -keystore C:\Users\Administrator\Desktop\test.jks
```
- 查看app内签名

```
keytool -printcert -file C:\Users\Administrator\Desktop\test\META-INF/CERT.RSA
```