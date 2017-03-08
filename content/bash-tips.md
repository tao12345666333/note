+++
title = "Bash 使用技巧"
draft = true
date = "2017-03-08T22:48:36+08:00"

+++

> 这是一篇 Bash 的使用技巧内容，部分内容需要先具备一些基础知识及 Linux 的基础操作能力

# 操作快捷键(emacs 模式)

* Ctrl + a : 光标返回首位
* Ctrl + e : 光标移至末尾
* Ctrl + p : 上一个命令
* Ctrl + n : 下一个命令
* Ctrl + l : 清屏
* Ctrl + h : 回退一位
* Ctrl + b : 光标向左一位
* Ctrl + f : 光标向右一位
* Ctrl + u : 剪切光标前的内容(全部)
* Ctrl + w : 剪切光标前的内容(按词)
* Ctrl + k : 剪切光标后的内容
* Ctrl + y : 将剪切的内容复制到光标后
* Ctrl + t : 交换光标前的两个字符顺序


# 设置操作模式为 Vi 模式

`set -o vi`


# 搜索

Ctrl + r : 搜索历史中输入过的命令


# 利用 bash 编程达到的便利

* !! 上条命令
* !\$ 上条命令的最后一个
* !* 上条命令所有参数
* !n !-n 第n个和倒数第n个
* ^old^new  替换旧命令
* !:index 上条命令索引的内容
* !:a-b 上条命令索引的内容
* !:gs/old/new 替换

* ![!|[?]string|[-]number] 引用
* :[n|x-y|^|\$|*|n*|%]   :[h|t|r|e|p|s|g]  前面选择后面修饰

* !name  name 开头的命令
* !?name  包含name的命令
