+++
title = "实用型 HTTP 指北"
draft = false
date = "2017-01-16T00:29:57+08:00"
categories = [ "Web" ]

+++

如无特殊说明， 下面举例都是指 HTTP/1.1 为例。

# 简介及发展

超文本传输协议（HTTP 协议）是一个应用层的协议，也是 Web 开发中最常使用的协议之一。

HTTP/0.9 是在 1991 年发布的第一个正式版本, 只接受 `GET` 方法，且不支持请求头。
HTTP/1.0 开始在通讯中指定，有了很多目前在使用的基本结构等。
HTTP/1.1 这个版本开始默认 keep-alive 并在缓存带宽等方面都有了改进，这个版本使用的时间要长的多。
HTTP/2  这个版本相对现代化，可以参考[ wiki ](https://zh.wikipedia.org/wiki/HTTP/2)。

# 消息结构

基于 HTTP 协议的数据传输，分为请求方（一般可能是浏览器或者某客户端）和响应方（一般是服务器端）。
HTTP 使用 URI 来传输数据和建立连接。

## 请求格式

* 状态行
* 请求头
* 请求数据

## 响应格式

* 状态行
* 响应头
* 响应数据

# 请求状态行 

由 请求方法， 地址， 协议版本号构成
e.g.

```
> GET / HTTP/1.1
```


# 请求头

```
> User-Agent: curl/7.37.1
> Host: moelove.info
> Accept: */*
```


# 请求方法

## GET
## POST
## HEAD
## PUT
## DELETE
## OPTIONS
## TRACE
## CONNECT

# 响应状态行

由 协议版本号，数字状态码，及相应的描述构成
e.g.

```
> HTTP/1.1 200 OK
```

# 响应头

```
> Server: GitHub.com
> Content-Type: text/html; charset=utf-8
> Last-Modified: Sat, 31 Dec 2016 17:13:05 GMT
> Access-Control-Allow-Origin: *
> Expires: Tue, 17 Jan 2017 20:56:34 GMT
> Cache-Control: max-age=600
```

# Content-Type

标示编码方式

# HTTP 状态码

* 200 OK 请求成功
* 301 Moved Permanently 请求永久重定向
* 302 Moved Temporarily 请求临时重定向
* 304 Not Modified 文件未修改，可以直接使用缓存的文件
* 400 Bad Request 请求错误
* 401 Unauthorized 请求未授权，必须和 WWW-Authenticate 报头域一起使用
* 403 Forbidden 被拒绝，一般是权限不足
* 404 Not Found 请求的资源未找到
* 500 Internal Server Error 服务器发生未预期的错误
* 503 Service Unavailable 服务器当前不能够处理客户端的请求，在一段时间之后，服务器可能会恢复正常

# HTTPS 相关

默认端口 443， 主要是为了将传输内容加密。

# 用户认证

## basic auth
## cookie, session 等

# Web 安全相关

## CSRF
