- [操作系统接口](#%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E6%8E%A5%E5%8F%A3)
        - [os](#os)
        - [shutil](#shutil)
- [文件通配符](#%E6%96%87%E4%BB%B6%E9%80%9A%E9%85%8D%E7%AC%A6)
        - [glob](#glob)
- [命令行参数](#%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B0)
        - [sys](#sys)
- [错误输出重定向和程序终止](#%E9%94%99%E8%AF%AF%E8%BE%93%E5%87%BA%E9%87%8D%E5%AE%9A%E5%90%91%E5%92%8C%E7%A8%8B%E5%BA%8F%E7%BB%88%E6%AD%A2)
        - [sys](#sys)
- [字符串正则匹配](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%AD%A3%E5%88%99%E5%8C%B9%E9%85%8D)
        - [re](#re)
- [数学](#%E6%95%B0%E5%AD%A6)
        - [math](#math)
        - [random](#random)
- [互联网访问](#%E4%BA%92%E8%81%94%E7%BD%91%E8%AE%BF%E9%97%AE)
        - [urilib.request](#urilibrequest)
        - [smtplib](#smtplib)
- [日期和时间](#%E6%97%A5%E6%9C%9F%E5%92%8C%E6%97%B6%E9%97%B4)
        - [datetime](#datetime)
- [数据压缩](#%E6%95%B0%E6%8D%AE%E5%8E%8B%E7%BC%A9)
        - [zlib](#zlib)
- [性能度量](#%E6%80%A7%E8%83%BD%E5%BA%A6%E9%87%8F)
        - [timeit](#timeit)
- [自动化测试](#%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95)
        - [doctest](#doctest)
        - [unittest](#unittest)
---
## 操作系统接口
### os
- `os`模块提供了与操作系统交互的函数。
```py
>>> import os
>>> os.getcwd()      # Return the current working directory
'C:\\Python35'
>>> os.chdir('/server/accesslogs')   # Change current working directory
>>> os.system('mkdir today')   # Run the command mkdir in the system shell
0
```
- 在使用一些像os这样的大型模块时内置的`dir()`和`help()`函数非常有用。
```py
>>> import os
>>> dir(os)  #returns a list of all module functions
>>> help(os)  #returns an extensive manual page created from the module's docstrings
```
### shutil
- 针对日常的文件和目录管理任务，`shutil`模块提供了一个易于使用的高级接口。
```py
>>> import shutil
>>> shutil.copyfile('data.db', 'archive.db')
'archive.db'
>>> shutil.move('/build/executables', 'installdir')
'installdir'
```
---
## 文件通配符
### glob
- `glob`模块提供了一个函数用于从目录通配符搜索中生成文件列表。
```py
>>> import glob
>>> glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']
```
---
## 命令行参数
### sys
- 通用工具脚本经常调用命令行参数。这些命令行参数以链表形式存储于`sys`模块的`argv`变量。例如在命令行中执行 `python demo.py one two three` 后可以得到以下输出结果:
```py
>>> import sys
>>> print(sys.argv)
['demo.py', 'one', 'two', 'three']
```
---
## 错误输出重定向和程序终止
### sys
- `sys` 还有`stdin`，`stdout`和`stderr`属性，即使在`stdout`被重定向时，后者也可以用于显示警告和错误信息：
```py
>>> sys.stderr.write('Warning, log file not found starting a new one\n')
Warning, log file not found starting a new one
```
- 大多脚本的直接终止都使用`sys.exit()`。
---
## 字符串正则匹配
### re
- `re`模块为高级字符串处理提供了正则表达式工具。
```py
>>> import re
>>> re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')
['foot', 'fell', 'fastest']
>>> re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
'cat in the hat'
```
- 只需简单的操作时，字符串方法最好用。
```py
>>> 'tea for too'.replace('too', 'two')
'tea for two'
```
---
## 数学
### math
- `math`模块为浮点运算提供了对底层C函数库的访问。
```py
>>> import math
>>> math.cos(math.pi / 4.0)
0.70710678118654757
>>> math.log(1024, 2)
10.0
```
### random
- `random`提供了生成随机数的工具。
```py
>>> import random
>>> random.choice(['apple', 'pear', 'banana'])
'apple'
>>> random.sample(range(100), 10)   # sampling without replacement
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
>>> random.random()    # random float
0.17970987693706186
>>> random.randrange(6)    # random integer chosen from range(6)
4
```
---
## 互联网访问
### urilib.request
- 用于处理从`urls`接收的数据。
```py
>>> from urllib.request import urlopen
>>> for line in urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl'):
...     line = line.decode('utf-8')  # Decoding the binary data to text.
...     if 'EST' in line or 'EDT' in line:  # look for Eastern Time
...         print(line)

<BR>Nov. 25, 09:43:32 PM EST
```
### smtplib
- 用于发送电子邮件。
```py
>>> import smtplib
>>> server = smtplib.SMTP('localhost')
>>> server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
... """To: jcaesar@example.org
... From: soothsayer@example.org
...
... Beware the Ides of March.
... """)
>>> server.quit()
```
---
## 日期和时间
### datetime
- `datetime`模块为日期和时间处理同时提供了简单和复杂的方法。
```py
>>> # dates are easily constructed and formatted
>>> from datetime import date
>>> now = date.today()
>>> now
datetime.date(2003, 12, 2)
>>> now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
'12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'

>>> # dates support calendar arithmetic
>>> birthday = date(1964, 7, 31)
>>> age = now - birthday
>>> age.days
14368
```
---
## 数据压缩
### zlib
- 以下模块直接支持通用的数据打包和压缩格式：`zlib`，`gzip`，`bz2`，`lzma`，`zipfile`以及`tarfile`。
```py
>>> import zlib
>>> s = b'witch which has which witches wrist watch'
>>> len(s)
41
>>> t = zlib.compress(s)
>>> len(t)
37
>>> zlib.decompress(t)
b'witch which has which witches wrist watch'
>>> zlib.crc32(s)
226805979
```
---
## 性能度量
### timeit
- 使用元组封装和拆封来交换元素看起来要比使用传统的方法要诱人的多。`timeit`证明了后者更快一些。
```py
>>> from timeit import Timer
>>> Timer('t=a; a=b; b=t', 'a=1; b=2').timeit()
0.57535828626024577
>>> Timer('a,b = b,a', 'a=1; b=2').timeit()
0.54962537085770791
```
- 相对于`timeit`的细粒度，`profile`和`pstats`模块提供了针对更大代码块的时间度量工具。
---
## 自动化测试
### doctest
- `doctest`模块提供了一个工具，扫描模块并根据程序中内嵌的文档字符串执行测试。测试构造如同简单的将它的输出结果剪切并粘贴到文档字符串中。通过用户提供的例子，它发展了文档，允许`doctest`模块确认代码的结果是否与文档一致。
```py
def average(values):
    """Computes the arithmetic mean of a list of numbers.

    >>> print(average([20, 30, 70]))
    40.0
    """
    return sum(values) / len(values)

import doctest
doctest.testmod()   # automatically validate the embedded tests
```
### unittest
- `unittest`模块不像`doctest`模块那么容易使用，不过它可以在一个独立的文件里提供一个更全面的测试集。
```py
import unittest

class TestStatisticalFunctions(unittest.TestCase):

    def test_average(self):
        self.assertEqual(average([20, 30, 70]), 40.0)
        self.assertEqual(round(average([1, 5, 7]), 1), 4.3)
        with self.assertRaises(ZeroDivisionError):
            average([])
        with self.assertRaises(TypeError):
            average(20, 30, 70)

unittest.main() # Calling from the command line invokes all tests
```