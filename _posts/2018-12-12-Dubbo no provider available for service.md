---
layout: post
title:  "Dubbo no provider available for service"
date:   2018-12-12 13:31:01 +0800
categories: java
tag: dubbo
---

* content
{:toc}




### Dubbo no provider available for service

- 原因一：使用端和广播端的xxxService类名以及路径不匹配

```
<!-- 广播端：xxxService 以及 version 必须与使用端一致-->
<dubbo:service interface="com.demo.service.DemoService" ref="demoService" version="1.0"/>
<!-- 使用端：xxxService 以及 version 必须与广播端一致-->
<dubbo:reference id="demoService" check="false" interface="com.demo.service.DemoService" version="1.0"/>
```

- 原因二：使用端和广播端的广播地址不匹配

```
<!-- 广播端：使用 multicast 广播注册中心暴露服务地址 (224.0.0.0 - 239.255.255.255) -->
<dubbo:registry address="multicast://224.5.6.7:1234?unicast=false"/>
<!-- 使用端：配置服务注册中心，必须有广播端一致 -->
<dubbo:registry address="multicast://224.5.6.7:1234?unicast=false"/>
```

- 原因三：该地址在网络中已被占用；改用其他地址(224.0.0.0-239.255.255.255之间)

> 注：如果还不好用，可以直接改成直连

```
<!-- 广播端：直连模式 -->
<dubbo:registry address="N/A"/>
<!-- 使用端：直连模式 在 dubbo:reference中 加上url="dubbo://127.0.0.1:20880" -->
<dubbo:reference id="demoService" check="false" interface="com.demo.service.DemoService" version="1.0" url="dubbo://127.0.0.1:20880"/>
```
- 原因四：使用了其他虚拟机之类的软件

> 把管理控制台中dubbo/webapps/ROOT/WEB-INF/dubbo.properties文件中加入dubbo.protocol.host=192.168.23.180，然后在Dubbo服务的dubbo配置文件<dubbo:protocol name=”dubbo” port=”20883″ />中加入 host=”192.168.23.180″，在Dubbo消费者端加入<dubbo:protocol host=”192.168.0.123″ />的配置。然后重启Dubbo管理员控制台、停止消费者端，停止服务提供端，启动服务提供端，再启动消费者端。 参考配置如下： 服务提供者provider.xml
```
<!-- 用dubbo协议在20880端口暴露服务 -->
<dubbo:protocol name="dubbo" host="192.168.23.180" port="20883" />
```

- consumer.xml

```
<dubbo:protocol host="192.168.23.180" />
```

> 配置完了后在dubbo-admin控制台可以看到服务提供者注册到zookepper上的dobbo服务已经是正常的192.168.23.180。消费者显示的还是consumer://124.232.132.94/* 但不影响调用