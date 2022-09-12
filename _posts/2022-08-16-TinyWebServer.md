---
layout: post
title: "TinyWebServer"
categories: networking
toc: true
---

## 环境配置

1. 安装MySQL并创建一个数据库

```bash
# Under wsl2
$ sudo apt install mysql-server  # install
$ sudo service mysql status  # check
$ sudo service mysql restart  # start

$ sudo mysql
mysql> create database mydb;
mysql> USE mydb;
mysql> CREATE TABLE user(
    -> username char(50) NULL,
    -> passwd char(50) NULL
    -> )ENGINE=InnoDB;
mysql> INSERT INTO user(username, passwd) VALUES('name', 'passwd');
```
2. 编译源码并运动

```bash
# Rename file main.c to main.cpp and update Makefile
# Then make
$ make server
$ sudo ./server port  # Running with SUDO due to `sudo mysql`
```

## 代码剖析

- `extern` 关键字

1. 拓宽变量/函数的可见性
2. 函数在整个程序上可见，隐式声明为 `extern`

> https://www.geeksforgeeks.org/understanding-extern-keyword-in-c/
> https://cplusplus.com/forum/general/212303/#msg992731