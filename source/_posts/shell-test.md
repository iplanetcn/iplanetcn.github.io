---
title: Shell测试(test)命令
date: 2019-02-28 15:10:16
categories: Shell
tags:
	- shell
	- linux
	- unix
	- test
---

#### 格式
格式一:

```bash
test expression
```

格式二:

```bash
[ expression ]    //⚠️ 注意左方括号后及右方括号前有一个[空格]
```

#### 说明

test是linux系统内置(builtin)的命令,用于评估表达式(expression)参数(parameter),
表达式expression的参数值(argument)包括:
文件测试参数,字符串测试参数,数字测试参数,参数组合运算符,退出状态码参数
*多个测试语句之间可以使用逻辑运算符(!, &&, ||)连接, 优先级: ! > && > ||*

#### 文件测试参数

| 操作符 | 描述 |
| --- | --- |
| -b file | 如果file是文件并且是特殊块文件，则返回true</div>|
| -c file | 如果file是字符文件，则返回true |
| -d file | 如果file存在且是目录，则返回true |
| -a/-e file | 如果file存在，则返回true |
| -f file | 如果file存在且是常规文件，则返回true |
| -g file | 如果file的GroupId已设置，则返回true |
| -h/-L file | 如果file是一个符号链接，则返回true |
| -k file | 如果file文件存在且粘滞位已设置，则返回true |
| -p file | 如果file是命名管道（FIFO），则返回true |
| -r file | 如果file文件存在且可读，则返回true |
| -s file | 如果file文件大小不为零，则返回true |
| -t file | 如果file已打开并与终端关联，则返回true |
| -u file | 如果file的UserId已设置，则返回true  |
| -w file | 如果file文件存在且可写，则返回true |
| -x file | 如果file文件存在且可执行，则返回true |
| file1 -ot file2 | 如果file1比file2旧，则返回true |
| file1 -nt file2 | 如果file1比file2新，则返回true |
| file1 -ef file2 | 如果file1是file2的符号链接或硬链接，则返回true |


#### 字符串测试参数

| 操作符 | 描述 |
| --- | --- |
| -n string | 如果字符串长度非零，则返回true |
| -z string | 如果字符长度为零，则返回true |
| string1 = string2 | 如果两个字符相同，则返回true |
| string1 != string2 | 如果两个字符不相同，则返回true |
| string | 如果字符非空，则返回true |

#### 数值比较测试参数

| 操作符 | 描述 |
| --- | --- |
| num1 -eq num2 | 如果连个数值相等，则返回true |
| num1 -ne num2 | 如果连个数值不等，则返回true |
| num1 -gt num2 | 如果num1大于num2，则返回true |
| num1 -ge num2 | 如果num1大于或等于num2，则返回true |
| num1 -lt num2 | 如果num1小于num2，则返回true |
| num1 -le num2 | 如果num1小于或等于num2，则返回true |


#### 组合运算符参数（用于单个或多个测试）

| 操作符 | 描述 |
| --- | --- |
| !expression | 一元否定运算符 |
| expression1 -a expression2 | 二元与运算符 |
| expression1 -o expression2 | 二元或运算符 |
| \\ (Expression\\) | 必须使用反斜杠转义分组括号 |

例1：

```bash
if test ! -s "$1"
then
    echo $1 does not exist or is empty.
fi
```

例2：

```bash
if [ $# -lt 2 -o ! -e "$1" ]
then
    exit
fi
```


#### 退出码参数

| 操作符 | 描述 |
| --- | --- |
| 0 | 返回true |
| 1 | 返回false |
| >1 | 发生错误 |

