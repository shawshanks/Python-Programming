## 推荐文档
[Select 模型简介](http://python.jobbole.com/84058/)  
[ select — 高效地等待 I/O](https://learnku.com/docs/pymotw/select-wait-for-io-efficiently/3429#f37ac7)  
[Python网络编程中的select 和 poll I/O复用的简单使用](https://www.cnblogs.com/coser/archive/2012/01/06/2315216.html)  
[python select模块详解](https://www.cnblogs.com/huchong/p/8613308.html)



## 一些翻译
[ select — Waiting for I/O completion](https://docs.python.org/3.6/library/select.html)
select -等待 I/O 完成

这个模块提供 select() 和 poll()函数,在大多数操作系统上都是可用的. 

在Windows上, 仅适用于sokect;在其他OS上, 它也使用于其他文件类型(特别来说,它适用于管道).

这个模块定义了以下内容:
>`select.poll()`

> (不是所有的操作系统都适用). 返回一个polling对象, 此对象支持registering和unregistering(注册和接触注册)文件描述符(file descriptors), 然后
polling them for I/O events; 查看Polling Object一节以获取polling object所支持的方法.


> select.select(rlist, wlist, xlist[, timeout])  
这是一个非常直接的对Unix `select()`系统调用的接口. 前三个参数是'waitable objects'的序列: 要么是表示文件描述符的整数,要么是有着无参数方法
fileno()的对象,fileno()会返回这样的一个整数:
- rlist: 等待到准备好读
- wlist: 等待到准备好写
- xlist: 等待一个"特殊条件"

> 空序列是被允许的, 但是这三个空序列的接受度是跟平台相关的.(对Unix来说可以工作,但是对Windows就不行了). 可选参数 timeout 指定了超时时间,以秒
为单位的浮点数. 当timeout参数被省略, 这个函数一直阻塞到至少一个文件描述符准备好. timeout的值为0指定了一个poll并且永不阻塞.

返回值是就绪对象的三倍列表:第一个三个参数的自己.
