---
title: CUDA学习
date: 2017-10-15 11:45:18
tags:
categories:
---

* 2017-10-15 v1.0

### 线程
线程按层次从大到小分为线程格（grid），线程块（block），线程（thread）。

### 核函数
`<<<a,b>>>`，传递参数时a指开辟的线程块大小，b指每个线程块中线程的大小。

### 共享内存
同一个线程块中的线程可以共享使用共享内存中的变量。

### 第三方库
CUDA不支持Vector类，所以大多需要对向量进行封装，这就要用到thrust