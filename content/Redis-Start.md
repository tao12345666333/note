+++
title = "Redis Start"
draft = false
date = "2017-02-23T00:54:21+08:00"
categories = [ "Database" ]
tags = ["Redis"]

+++

> Redis 是一个开源（BSD许可）的，内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件。 它支持多种类型的数据结构，如 字符串（strings）， 散列（hashes）， 列表（lists）， 集合（sets）， 有序集（sorted sets） 


# Redis 介绍

# Reids 安装及启动

# 常用数据结构及其用法

## String

Reids 中的基本数据结构，set/get 用于存取数据

## Hash

一般用于存储对象，类似Python中的字典

## List

列表， 可用作 FIFO 或者 LIFO 使用

## Set

集合，提供了一般集合的常规运算

## Sorted Set

可排序的集合

# HA 方案

* 主从

    配置 slaveof 即可

* 哨兵

    一个特殊状态的 redis-server, 监听 master 的心跳包， 如果 master 挂了，则进行主从切换

* 集群 cluster


# Reids 数据持久化

## RDB

## AOF
