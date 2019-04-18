[Argparse 教程](https://docs.python.org/zh-cn/3/howto/argparse.html#id1)

[Python-argparse-命令行与参数解析](https://zhuanlan.zhihu.com/p/34395749)

[argparse 解析](http://wiki.jikexueyuan.com/project/explore-python/Standard-Modules/argparse.html)

[python argparse用法总结](https://www.jianshu.com/p/fef2d215b91d)

[argparse --- 命令行选项、参数和子命令解析器](https://docs.python.org/zh-cn/3/library/argparse.html)


## 1.初探命令行

> <<C语言程序设计:现代方法>> 13.7.1 命令行参数

<img src="https://github.com/shawshanks/Python-Programming/blob/master/image/%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B0.png" width=80%>
<img src="https://github.com/shawshanks/Python-Programming/blob/master/image/%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B02.png" width=80%>
<img src="https://github.com/shawshanks/Python-Programming/blob/master/image/%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B03.png" width=80%>

执行程序时，可以从命令行传值给 C 程序。这些值被称为命令行参数.

在C中, 访问命令行其实是向C中`int main(argc, *argv[])`传参数. 其中 `argc`指示命令行参数的数量,`argv`是指向命令行参数的的指针.


在Python中,与C中`*argv[]`相仿的是:sys.argv, 它是一个列表，其中包含了被传递给 Python 脚本的命令行参数。 argv[0] 为脚本的名称（是否是完整的路径名取决于操作系统）。如果是通过 Python 解释器的命令行参数 -c 来执行的， argv[0] 会被设置成字符串 '-c' 。如果没有脚本名被传递给 Python 解释器， argv[0] 为空字符串。

## Argparse 模块
**用途**: argparse 模块可以让人轻松编写用户友好的命令行接口。程序定义它需要的参数，然后 argparse 将弄清如何从 sys.argv 解析出那些参数。 argparse 模块还会自动生成帮助和使用手册，并在用户给程序传入无效参数时报出错误信息。

### 使用方法
#### 1. 创建 ArgumentParser() 对象
[ArgumentParser 对象 官方文档](https://docs.python.org/zh-cn/3/library/argparse.html)

#### 2. 调用 add_argument() 方法添加参数
[调用 add_argument()] (https://docs.python.org/zh-cn/3/library/argparse.html)
作用: 定义单个的命令行参数应当如何解析
