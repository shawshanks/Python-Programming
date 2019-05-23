
[Python Read File: In-Depth Tutorial on Working with Files in Python](https://blog.udemy.com/python-read-file/)

[Opening and Closing a File in Python](https://realpython.com/read-write-files-python/)

[Strip Newline in Python | 4 Example Codes (Remove Trailing & Leading Blank Line)](https://statistical-programming.com/python-strip-remove-newline-from-string)

## 如何从命令行 将一个只有整数的txt文件  中的整数读取到数组中
### 1. 从命令行中选定文件
[Python 命令行参数](https://docs.python.org/zh-cn/3/tutorial/stdlib.html#command-line-arguments)
使用`sys.argv`参数. 

命令行中的参数 按照顺序被存储在`sys.argv`列表中.

### 2. 从文件中读取数据
### 2.1 打开关闭文件
打开文件后要记得关闭,虽然Python的垃圾处理器会自动帮你关闭,但是不保证关闭的时间,在没有关闭的情况下,文件内容可能会发生改变.

通常的模式为:
```python
file = open(filename)
try:
  # do something
finally:
  file.close()
```
在处理文件对象时，最好使用 with 关键字。 优点是当子句体结束后文件会正确关闭，即使在某个时刻引发了异常。 
而且使用 with 相比等效的 try-finally 代码块要简短得多:
```python 
with open(filename) as file:
  # do something
```

### 3. 处理输入字符 然后强制类型转换为整数
在文本模式下读取时，默认会把平台特定的行结束符 (Unix 上的 \n, Windows 上的 \r\n) 转换为 \n。在文本模式下写入时，默认会把出现的 \n 转换回平台
特定的结束符。

数字之间可能有换行符，或者空格，这些都是所谓的 [whitespaces](https://infohost.nmt.edu/tcc/help/pubs/python/web/whitespace.html)

>A string containing all ASCII characters that are considered whitespace. This includes the characters space, tab, linefeed,
>return, formfeed, and vertical tab.
>包含被认为是 whitespace的所有ASCII字符的字符串是 whitesapce.包括空格，tab，换行，回车，换页符, 竖直tab

可以使用内建函数`strip()`来进行处理。

```
array = []
with open(sys.argv[n]) as f:
    for line in f:
        if not f == '\n':   # 防止数据中有多余的 行结束符'\n'
            array.append(int(line.strip()))  
```
