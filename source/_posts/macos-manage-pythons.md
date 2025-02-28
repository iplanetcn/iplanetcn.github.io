---
title: macOS 安装和管理多个Python版本
date: 2018-07-09 09:56:46
categories: Python
tags:
  - homebrew
  - python
  - pyenv
  - macos
---
#### 说明
目前Python同时更新与维护Python2和Python3，选择Python2还是选择Python3，取决于当前要使用的库、框架支持哪个版本，所以经常会遇到切换版本的情况。

那么应该怎样有效的更改呢？很多小伙伴一定会想到修改环境变量，指定Python的默认路径，这样当然可以，然而不够优雅。那么怎样的方法才算优雅呢？当然是一条命令了👻。

这里通过brew安装pyenv，再用pyenv安装管理Python。

#### 安装步骤
- ##### 安装[homebrew](https://brew.sh/)：🚀
 ```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew -v
Homebrew 1.6.9
Homebrew/homebrew-core (git revision 5707e; last commit 2018-07-09)
```
注：Homebrew 是macOS下非常高效的命令行软件包管理器，mac必安装工具之一。

- ##### 安装[pyenv](https://github.com/pyenv/pyenv)：🛰
```bash
$ brew update
$ brew install pyenv
$ pyenv -v
pyenv 1.2.5
```

- ##### 安装管理多个Python：
```bash
$ pyenv install 2.7.15
$ pyenv install 3.7.0
$ pyenv versions
  system
  2.7.15
* 3.7.0 (set by /Users/john/.pyenv/version)
```
注：星号指定当前的版本

- ##### 切换版本：
```bash
$ pyenv global 2.7.15
$ pyenv versions
  system
* 2.7.15 (set by /Users/john/.pyenv/version)
  3.7.0
$ python --version
Python 2.7.15
```

- ##### pyenv常用的命令说明：
 ```bash
使用方式: pyenv <命令> [<参数>]

命令:
   commands    查看所有命令
   local       设置或显示本地的Python版本
   global      设置或显示全局Python版本
   shell       设置或显示shell指定的Python版本
   install     安装指定Python版本
   uninstall   卸载指定Python版本)
   version     显示当前的Python版本及其本地路径
   versions    查看所有已经安装的版本
   which       显示安装路径
```
注：使用local、global、shell，设置python版本时需要跟上参数（版本号），查看则不需要。
