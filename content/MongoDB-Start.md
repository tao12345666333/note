+++
title = "MongoDB Start"
draft = false
date = "2017-02-22T23:53:31+08:00"
categories = [ "Database" ]
tags = ["MongoDB"]

+++

> MongoDB 是基于分布式文件存储的由 C++ 编写的数据库. 目标是提供可扩展的高性能数据存储解决方案

# NoSQL 介绍

NoSQL (Not Only SQL) 非关系型数据库, 与之相对应的就是传统的关系型数据库. 那我们在什么场景下可能选择 NoSQL 呢？在数据需求尚不明确或者需要存储大量非结构化数据， 那么使用非关系型数据库可能对我们更有利一些。

# MongoDB 介绍

现代化的面向文档的非关系型数据库，数据格式采用 BSON（类 JSON）的格式存储，MongoDB shell 中可使用 JavaScript 语法.

# MongoDB 安装及启动

## 安装

* [官方文档--支持大多数发行版](https://docs.mongodb.com/manual/installation/)
* [源码编译安装](http://moelove.info/2015/09/13/%E6%BA%90%E7%A0%81%E7%BC%96%E8%AF%91MongoDB/)

## 启动

可以直接执行 `mongod` 启动，如果不指定 `dbpath` 则默认为当前目录（建议手动指定，部分版本可能会有行为差异）

`sudo mongod --dbpath=/tmp`


# 连接

    * MongoDB shell
    * `mongodb://[username:password@]host1[:port1],...[,hostN[:portN]]][/[database][?options]]`
    * 各语言驱动客户端

# 基本操作 (CRUD)

# 集群操作
