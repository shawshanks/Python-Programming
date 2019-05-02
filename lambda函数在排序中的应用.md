在看Python cookbook 的 [1.8 字典的运算](https://python3-cookbook.readthedocs.io/zh_CN/latest/c01/p08_calculating_with_dict.html)
遇到了这个问题:

```python
prices = {
    'ACME': 45.23,
    'AAPL': 612.78,
    'IBM': 205.55,
    'HPQ': 37.20,
    'FB': 10.75
}
```

```python 
min(prices, key=lambda k: prices[k]) # Returns 'FB'
max(prices, key=lambda k: prices[k]) # Returns 'AAPL'
```

一直没想明白k是什么. 找到了这篇帖子 [请问这个例子中的 lambda 表达式是怎么起作用的？](https://www.v2ex.com/t/377926) 
终于搞懂了.

答案:
> k 是 min/max 调用 key 回调函数时传入的参数，这个参数就是前面的 iterable 参数的每个值。dict 是 iterable 的并且每个值等于其 key。

## dictionary的iterable
[Python Dictionaries](https://medium.com/python-pandemonium/python-dictionaries-45cacc2b76aa)
6. Iteration
> A dictionary by itself is an iterable of its keys.
