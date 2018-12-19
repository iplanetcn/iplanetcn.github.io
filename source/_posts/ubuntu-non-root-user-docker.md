---
title: Ubuntu中以非root用户身份管理Docker
date: 2018-12-19 00:11:24
categories: Docker
tags:
    - ubuntu
    - docker
---

#### 说明

Docker守护程序绑定到Unix套接字而不是TCP端口。默认情况下，Unix套接字由root拥有，而非用户只能通过sudo使用它。Docker守护程序始终以root用户身份运行。

如果不想在docker命令前加上sudo，可创建一个名为docker的Unix用户组并向其添加当前用户。当Docker守护程序启动时，它会创建一个可由该docker组成员访问的Unix套接字。

#### 执行步骤

- ##### 添加docker用户组 (ubuntu16.04安装docker后,默认会创建该用户组)
```bash
$ sudo groupadd docker
```

- ##### 将当前用户加入到docker用户组中
```bash
$ sudo usermod -aG docker $USER
```

- ##### 重启服务
```bash
$ sudo service docker restart
```

- ##### 登录至新的docker组(也可以退出并重新登录)
```bash
$ newgrp - docker
```

- ##### 确认不需要添加sudo运行docker
```bash
$ docker run hello-world
```
