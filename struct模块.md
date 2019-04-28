[Python使用struct处理二进制](https://www.cnblogs.com/gala/archive/2011/09/22/2184801.html)  

[Python ctypes+struct实现类c的结构化数据串行处理](https://blog.csdn.net/machael_sonic/article/details/50266499)


[廖雪峰 struct](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431955007656a66f831e208e4c189b8a9e9f3f25ba53000)

[浅析Python中的struct模块](https://www.cnblogs.com/coser/archive/2011/12/17/2291160.html)

[Python3 HowTo: Data Structures](https://pymotw.com/3/struct/)

# [官方部分文档翻译](https://docs.python.org/3/library/struct.html)
## Struct--将字节解释为压缩二进制数据
这个模块在Python的值和C语言中structs中转化, 其中C语言的struct被表示为Python的bytes对象. struct模块可以被用于处理储存在文件中的二进制数据,或者网络连接, 或者其他来源. Struct模块使用 Format Strings 作为C structs和想要(被)转化为Python 值的布局简洁描述.

### Format Strings
Format Strings是一种机制,当要压缩(packing)或者解压(unpacking)数据时,它用于指定预期的布局. Forat Strings建立在Format characters之上, Format Characters指定了被压缩或者解压的数据类型.  此外,也有一些特殊字符用于控制 Byte Order, Size 和对齐方式(alignment).

### Format Characters
Format Characters有如下意思:
在已知值的数据类型的情况下,值在C和Python 之间的转换应该明确的. 'Standard Size '那一列指的是,当使用standard size时,被压缩的值以字节作为单位的大小(多少个字节长). 当使用standard size时 即指当format string 以  '<', '>', '!' or '='其中之一 作为开头时.


