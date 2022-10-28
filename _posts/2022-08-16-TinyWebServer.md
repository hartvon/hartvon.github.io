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

## HTTP 报文处理流程

1. 客户端发出 HTTP 连接请求，主线程创建 HTTP 对象接收请求并将所有数据读入对应 buffer，
将该对象插入任务队列，随后工作线程从任务队列中取出一个任务进行处理。

2. 工作线程取出任务后，调用 `process_read` 函数，通过主、从状态机对请求报文进行解析
   - 主状态机内部调用从状态机，从状态机驱动主状态机
   - 从状态机负责读取报文的一行，主状态机负责对该行数据进行解析

3. 解析完之后，跳转 `do_request` 函数生成响应报文，通过 `process_write` 写入buffer，返回给浏览器端

## 定时器

服务器主循环为每一个连接创建一个定时器，并对每个连接进行定时。另外，利用升序时间链表容器将所有定时器串联起来，若主循环接收到定时通知，则在链表中依次执行定时任务。
> 定时器处理非活动连接：
> - 定时方法与信号通知流程
> - 定时器及其容器设计与定时任务的处理

## 信号通知流程

**统一事件源**

具体的，信号处理函数使用管道将信号传递给主循环，信号处理函数往管道的写端写入信号值，主循环则从管道的读端读出信号值，使用I/O复用系统调用来监听管道读端的可读事件，这样信号事件与其他文件描述符都可以通过epoll来监测，从而实现统一处理。

**信号通知逻辑**

1. 创建管道，信号处理函数向管道写端写入信号值，I/O 复用系统从管道读端读取信号值
2. 注册 SIGALRM 和 SIGTERM 信号的信号处理函数
3. 利用I/O复用系统监听管道读端文件描述符的可读事件
4. 信息值传递给主循环，主循环再根据接收到的信号值执行目标信号对应的逻辑代码 

## 代码剖析

- `extern` 关键字

1. 拓宽变量/函数的可见性
2. 函数在整个程序上可见，隐式声明为 `extern`

> https://www.geeksforgeeks.org/understanding-extern-keyword-in-c/
> https://cplusplus.com/forum/general/212303/#msg992731