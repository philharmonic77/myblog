---
author: "philharmonic77"
title: "写python经常出错的一些问题"
date: "2023-04-24"
description: ""
tags: ["python"]
hideMeta: false
searchHidden: false
ShowBreadCrumbs: false
---

# 1.函数作用域
（1）函数内部可以读取全局变量；
（2）python假定在函数定义体中赋值的变量是局部变量；
（3）如果在函数中赋值时想让解释器把 b 当成全局变量，要使用 global 声明；
``` python
## example 1
>>> def f1(a):
... print(a)
... print(b)
...
>>> b = 6 ## 必要的一步，否则报错
>>> f1(3)
3
6

## example 2 
>>> b = 6
>>> def f2(a):
... print(a)
... print(b)
... b = 9 ## 被当作了局部变量
...
>>> f2(3)
3
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<stdin>", line 3, in f2
UnboundLocalError: local variable 'b' referenced before assignment

## example 3

>>> b = 6
>>> def f3(a):
... global b
... print(a)
... print(b)
... b = 9 
...
>>> f3(3)
3
6
>>> b
9
>>> f3(3)
3
9
>>> b = 30
>>> b
30
```
* 参考资料：《流畅的python》第一版第7章里关于“函数作用域规则”的部分。