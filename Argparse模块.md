[Argparse 教程](https://docs.python.org/zh-cn/3/howto/argparse.html#id1)

[知乎: Python-argparse-命令行与参数解析](https://zhuanlan.zhihu.com/p/34395749)

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

# Argparse 模块
**用途**: argparse 模块可以让人轻松编写用户友好的命令行接口。程序定义它需要的参数，然后 argparse 将弄清如何从 sys.argv 解析出那些参数。 argparse 模块还会自动生成帮助和使用手册，并在用户给程序传入无效参数时报出错误信息。

## 使用方法
### 1. 创建 ArgumentParser() 对象
[ArgumentParser 对象 官方文档](https://docs.python.org/zh-cn/3/library/argparse.html)

### 2. 调用 add_argument() 方法添加参数
[调用 add_argument()](https://docs.python.org/zh-cn/3/library/argparse.html)

作用: 定义单个的命令行参数应当如何解析

### 2.1 [metavar参数](https://docs.python.org/zh-cn/3/library/argparse.html#metavar)
当ArgumentParser生成帮助信息,它需要一些方式来引用每个预期的参数. 默认地, ArgumentParser对象使用[dest](https://docs.python.org/zh-cn/3/library/argparse.html#dest)值作为每个对象的"名称".默认地, 对于位置参数动作,dest值被直接引用, 对于可选参数动作, dest值被大写注明 因此,当单个有着`dest='bar`的位置参数,将会被引用为`bar'`. 一个单独的位置参数`--foo`,将会被引用为`FOO`. 如下例:
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo')
>>> parser.add_argument('bar')
>>> parser.parse_args('X --foo Y'.split())
Namespace(bar='X', foo='Y')
>>> parser.print_help()
usage:  [-h] [--foo FOO] bar

positional arguments:
 bar

optional arguments:
 -h, --help  show this help message and exit
 --foo FOO
```

一个替代的名字可以用`metavar`指定:
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo', metavar='YYY')
>>> parser.add_argument('bar', metavar='XXX')
>>> parser.parse_args('X --foo Y'.split())
Namespace(bar='X', foo='Y')
>>> parser.print_help()
usage:  [-h] [--foo YYY] XXX

positional arguments:
 XXX

optional arguments:
 -h, --help  show this help message and exit
 --foo YYY
```
请注意`metavar`仅仅改变显示名-parse_args()对象的属性名仍然可以被dest值决定.

不同的`nargs`的值可能导致metavar被使用多次. 给`metavar`提供一个元组对每个参数指定一个不同显示:
```python
>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-x', nargs=2)
>>> parser.add_argument('--foo', nargs=2, metavar=('bar', 'baz'))
>>> parser.print_help()
usage: PROG [-h] [-x X X] [--foo bar baz]

optional arguments:
 -h, --help     show this help message and exit
 -x X X
 --foo bar baz
```

