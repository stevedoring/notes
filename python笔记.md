- [列表转字符串](#列表转字符串)
- [获取当前文件路径及该路径下子目录和文件的方法](#获取当前文件路径及该路径下子目录和文件的方法)
- [判断文件或文件夹是否存在的方法](#判断文件或文件夹是否存在的方法)
- [安装PyQt5](#安装pyqt5)
- [module和package](#module和package)
- [import和from import用法](#import和from-import用法)
- [正则表达式](#正则表达式)
---
## 列表转字符串

```py
>>> ls1 = ['a', 1, 'b', 2]
>>> ls2 = [str(i) for i in ls1] #将列表的所有值都转成字符
>>> ls2
['a', '1', 'b', '2']
>>> ls3 = ''.join(ls2)# 将列表的字符拼接成字符串
>>> ls3
'a1b2'
```

---

## 获取当前文件路径及该路径下子目录和文件的方法

```py
import os
os.path.dirname(__file__) #获取当前路径
os.path.dirname(os.path.dirname(__file__)) #获取上一级路径
os.listdir(os.path.dirname(__file__)) #列出当前路径下所有子目录和文件
for root,dirs,files in os.walk(os.path.dirname(__file__)):
    print(root) #当前路径
    print(dirs) #当前路径下子目录
    print(files) #当前路径下文件及子目录下文件
# 显示的格式为：
# 根目录路径
# 子目录名1
# 文件
# 子目录路径
# 文件
# ......
```

---

## 判断文件或文件夹是否存在的方法

```py
import os

os.path.exists(file_name&dir_name) # 判断当前路径下是否存在文件或者文件夹
os.path.isdir(dir_name) #判断文件夹是否存在
os.path.isfile(file_name) #判断文件是否存在

os.access(path,mode) #通过mode判断文件是否可进行相应操作
# mode有以下几种模式：
# os.F_OK: 检查文件是否存在
# os.R_OK: 检查文件是否可读
# os.W_OK: 检查文件是否可以写入
# os.X_OK: 检查文件是否可以执行
```

---

## 安装PyQt5

```py
pip3 install PyQt5
pip3 install PyQt5-tools
```

---

## module和package

- module
    > module就是一个.py文件
- package
    > package就是一个包含.py文件的文件夹，文件夹中还包含一个__init__.py文件
---

## import和from import用法

```py
import package #True
import moudle #True
from module import function #True
from package import module #True
from package import * #True
import module.function #False
```

---

## 正则表达式

```
\d表示可以匹配1个数字，\w表示可以匹配1个字母或者数字，\s表示可以匹配1个空格
.表示可以匹配1个任意字符
*表示可以匹配任意个字符
+表示可以匹配至少1个字符
?表示可以匹配0个或1个字符
{n}表示可以匹配n个字符，{n,m}表示可以匹配n~m个字符
A|B表示可以匹配A或者B
^表示行的开头，^\d表示必须以数字开头
$表示行的结尾，\d$表示必须以数字结尾
[0-9a-zA-Z\_]可以匹配一个数字、字母或者下划线
[a-zA-Z\_][0-9a-zA-Z\_]*可以匹配由字母或下划线开头，后接任意个由一个数字、字母或者下划线组成的字符串
[a-zA-Z\_][0-9a-zA-Z\_]{0, 19}更精确地限制了变量的长度是1-20个字符（前面1个字符+后面最多19个字符）
```