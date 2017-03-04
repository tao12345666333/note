+++
title = "Redis 协议简介"
draft = true
date = "2017-03-04T23:22:05+08:00"
categories = [ "Database" ]
tags = ["Redis"]

+++

Redis 的客户端和服务端之间采取了一种独立名为 RESP(REdis Serialization Protocol) 的协议，作者主要考虑了以下几个点：

* 容易实现
* 解析快
* 人类可读

注意：RESP 虽然是为 Redis 设计的，但是同样也可以用于其他 C/S 的软件。


RESP 主要可以序列化以下几种类型：整数，字符串，数组，错误信息。Redis 客户端向服务端发送的是一组由执行的命令组成的字符串数组，服务端根据不同的命令回复不同类型的数据。



