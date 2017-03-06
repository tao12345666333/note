+++
title = "利器系列-终端分屏神器 Tmux"
draft = true
date = "2017-03-06T22:35:21+08:00"

+++


> 这是利器系列的第 1 篇，当然还是要写每天都在用的 Tmux 咯! 当时我不会介绍 Tmux 的全部内容。
> 第 0 篇是 [利器系列-更高效的Vim](http://moelove.info/2016/09/16/%E5%88%A9%E5%99%A8%E7%B3%BB%E5%88%97-%E6%9B%B4%E9%AB%98%E6%95%88%E7%9A%84Vim/)


# 终端分屏

首先，我们先来了解下终端分屏是什么。顾名思义，终端分屏就是把一个终端屏幕拆解为多个窗口，并且可以进行切换。

* 为什么要进行终端分屏呢？

看过我介绍或者看过我之前文章的，应该都知道我是个 Vim 党，日常工作也都是在终端下，在终端下使用编辑器而不使用 GUI 或者 IDE，第一是因为在终端下我可以使用全键盘控制，不需要鼠标之类的，效率很高；第二，在终端下可以更灵活的配合系统工具完成我所需要的一切，包括测试之类的；第三，IDE 的功能太过繁琐，占用资源很多，而对我来说，这些都是累赘。第四，因为我长期都在 Linux 下，而且更多时间在考虑效率，默认情况下，终端内的 Vim 要比其他各种 IDE 要看着顺眼的多。


* 为什么不使用 iTerm2 呢？

iTerm2 是一个纯粹的 GUI 工具，它的切割是真正对窗口的切割，而非对终端的切割，并且它也不能保存会话信息。为什么我一直在说会话信息呢？你有没有试过 **结对编程** ？ （看我纯洁的微笑 :-） 用 Tmux 绝对是利器！


# Tmux 简介

Tmux 不仅仅是一款终端分屏软件(终端复用器)，同时 Tmux 也可以随时断开或者进入会话，即终端会话保持（可能你会想到 Screen 但 Tmux 却可以做到更多）。想想你有没有遇到过在服务器上编译调试，去接了杯水回来发现 `Write failed: Broken pipe` 连接断开了，又得重新开始。如果你有过类似经历，那么还是把后面的内容看完，并开始使用 Tmux 吧！ 下面我们先来聊一下 Tmux 中的一些基本概念:


## Session 会话

一组窗口或者说一个 Tmux 实例。当你每次输入 `tmux` 的时候，便打开了一个会话。
类似的还有以下命令：

`tmux attach-session` 将会进入一个会话
`tmux list-sessions` 将列出所有会话

## Window 窗口

一个可用于执行任务的窗口。 使用 `<bind-key> c` 可以创建一个新的窗口, 将 `c` 换为 `n` 或 `p` 可以进行前后切换。

## Pane 窗格

切割成小块的窗口，可类比 Vim 中的窗口切割. `<bind-key> "` 或者 `<bind-key> %` 可以进行水平或者垂直分屏。


# 安装

## Mac

```
brew install tmux
```

## Linux

```
sudo apt-get install tmux  # Debian/Ubuntu

sudo yum install tmux  # CentOS/Fedora
```

## 配置

可以创建一个 `$HOME/.tmux.conf` 的文件， 配置项可以 `man tmux` 查看，或者直接使用我的

```
wget https://raw.githubusercontent.com/tao12345666333/dotfiles/master/tmux/tmux.conf -O $HOME/.tmux.conf
```

### 常用配置的说明


# 使用

在终端输入下面的命令就可以开始使用 tmux 了

```
➜  ~ tmux
```

而想要退出的时候，也只要输入 exit 即可

```
➜  ~ exit
```

> 注意:在Linux下，默认$TERM 是xterm， 直接启动tmux并且打开vim的话， 会出现颜色不对的情况。使用tmux -2 启动， 强制启动256色。


# 应用

* 窗格同步

```
<bind-key> :set synchronize-panes on
```

执行这条命令可以让所有窗格内容同步。多用于一些批量环境命令之类的。


* 使用下面的代码，做多ssh连接

```
starttmux() {
    if [ -z "$HOSTS" ]; then
       echo -n "Please provide of list of hosts separated by spaces [ENTER]: "
       read HOSTS
    fi

    local hosts=( $HOSTS )
    echo ' >>> will connnect to'
    echo '------'
    echo ${hosts[@]}
    echo '------'


    tmux new-window "ssh -p 31220 tao@${hosts[0]}"
    unset hosts[0];
    for i in "${hosts[@]}"; do
        tmux split-window -h  "ssh -p 31220 tao@$i"
        tmux select-layout tiled > /dev/null
    done
    tmux select-pane -t 0
    tmux set-window-option synchronize-panes on > /dev/null

}

HOSTS=${HOSTS:=$*}

starttmux

```


# 使用截图

![my tmux](http://moelove.qiniudn.com/my_tmux.png)


备注：以上内容会持续更新完善。请留意 http://moelove.info
