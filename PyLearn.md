# Python 语法
## 关键字
### import

 &emsp;导入其他文件中的代码供我们使用，例如在test文件中我们有个test1方法:  
 ```python
def test1():  
    return 1
```
 &emsp;假如我们在其他的文件里想使用这个test文件中的test方法,那么我们就需要导入:  
 ```python
import test

test.test1() # 这里由于我们导入了整个test文件，所以我们在使用的时候要指定一下test.test1来使用
```
 &emsp;或者:  
 ```python
from test import test1

test1() # 这里我们只导入了test文件中的test1方法，所以可以直接使用
```
>> 自动化测试常用包  
```python
import sys # python系统操作模块，exit()退出程序，
import time # 时间模块 程序睡眠等
import xlrd  # 操作excel模块，不支持xlsx
from appium import webdriver # 从appium导入webdriver驱动 查找操作元素
from appium.webdriver.common.touch_action import TouchAction #导入长按等触屏操作需要用的类
from openpyxl import load_workbook # 操作excel模块，支持xlsx
from selenium.common.exceptions import NoSuchElementException # 导入appium找不到元素的异常然后捕捉，让提示更友好
from selenium.webdriver.common.by import By
from xlutils.copy import copy # 复制excel数据，用来保存新excel
import json # 导入json类库 解析json数据
import requests # 导入http请求模块，发送http请求
import random #导入获取随机数模块
import threading #导入多线程模块
import pymysql # 导入操作mysql的模块

```  
 ### and
 &emsp;and关键字属于逻辑运算符，通常的结构为 '条件表达式1` and '条件表达式2' and '条件表达式3 ...'，只有当所有的条件
 表达式的结果都为True时得到的结果才是True，否则就是False
 ```python
if test == 1 and test == 2: #因为test同一时间只会有一个值，所以得到的结果是False
    pass
```  
### or
 &emsp;or关键字属于逻辑运算符，通常的结构为 '条件表达式1` or '条件表达式2' or '条件表达式3 ...'，与and相反只要有一
 个表达式的结果为True时得到的结果就是True，所有的表达式都为False才是False
 ```python
if test == 1 or test == 2: #当test等于1或者2时，结果为True
    pass
```  
### not
&emsp;在python中not是逻辑判断词，用于布尔型True和False，not True为False，not False为True，以下是几个常用的not的用法:  
>not与逻辑判断句if连用，代表not后面的表达式为False的时候，执行冒号后面的语句。比如：
```python
a = False
if not a:  #这里因为a是False，所以not a就是True
   print("hello") #这里就能够输出结果hello
```
>判断元素是否在列表或者字典中，if a not in b，a是元素，b是列表或字典，这句话的意思是如果a不在列表b中，那么就执行冒号后面的语句，比如：
```python
a = 5
b = [1, 2, 3]
if a not in b:
   print("hello")  #这里也能够输出结果hello
```
### if
```python
if test == 1:
    print("test")
```  
 &emsp;if关键字后面跟着的一定是一个bool值或者条件表达式，就如同本例中的'test == 1'这个条件表达式一样，得到的结果
 一定是True或者False,当结果为True的时候会执行if下的代码，即本例中的'print("test")',否则就跳过  

### else
&emsp;else关键字必须要跟if关键字配合使用，作用是当if中的条件不为True是就执行else中的语句。下面例子中当test的值不为1
的时候打印的就是'test!=1'
```python
if test == 1:
    print("test=1")
else:
    print("test!=1")
```  
### elif
&emsp;elif关键字其实是else if的缩写，必须要跟if关键字配合使用，作用是当if中的条件不为True时就继续判断elif中的语句。如下例：
```python
if test == 1:  # 先判断test是否等于1，
    print("test=1")
elif test == 2:  # test不等于1时继续判断test是否等于2，
    print("test=2")
elif test == 3:  # test不等于2时继续判断test是否等于3，
    print("test=3")
else:  
    print("test") # 当test不等于1，2，3中的任意一个值是，执行else语句

```  
### while
&emsp;while 语句用于循环执行程序，即在某条件下，循环执行某段程序，以处理需要重复处理的相同任务,基本形式为：
```python
while a < 10:  #判断条件，为True是执行字句，每次执行完字句就会再次判断条件是否满足
    print(a)   #执行子句

```  
执行过程如GIF所示：  

![while](http://www.runoob.com/wp-content/uploads/2014/05/006faQNTgw1f5wnm06h3ug30ci08cake.gif)
### for
&emsp;for循环可以遍历任何序列的项目，如一个列表或者一个字符串,基本形式为：  
```python
a = 'qwertyuiop'  # 这里的a会被当作一个字符数组
for char in a:    # 依次遍历，并将当前的值赋予char变量以供执行字句使用
    print(char)   # 执行字句

```
### break
&emsp;break语句用来终止循环语句，即循环条件没有False条件或者序列还没被完全递归完，也会停止执行循环语句。
break语句用在while和for循环中,如果使用嵌套循环，break语句将停止执行最深层的循环
```python
for num in range(10):  # range(10)得到的是0到9的数组
    if num == 5:       # 当num=5的时候跳出循环，也就是5之后的数字不在打印
        break
    print(num)

```  
或者  
```python
array = ['apple', 'bike', 'alibaba']
for word in array:           # 外循环，依次遍历array里的单词
    for char in word:        # 内循环，依次遍历单词中的字符
        if char == 'a':      # 当字符等于a时跳出内循环，继续执行下次外循环
            break
        print(char)          # 所以只会打印b,i,k,e

```
### continue
&emsp;continue 语句用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环。continue语句用在while和for循环中
```python
for num in range(10):  # range(10)得到的是0到9的数组
    if num == 5:       # 当num=5的时候跳出本次循环，也就是说打印结果里不会有5
        continue
    print(num)
```
或者  
```python
array = ['apple', 'bike', 'alibaba']
for word in array:           # 外循环，依次遍历array里的单词
    for char in word:        # 内循环，依次遍历单词中的字符
        if char == 'a':      # 当字符等于a时中断本次内循环，继续执行下次内循环
            continue
        print(char)          # 所以会打印出除a之外的所有字符
```   
### in
&emsp;in 关键字是判断是否包含
```python
a = [1,2,3]
print(1 in a)  #输出True,因为a包含了1
```
### is
&emsp;is 关键字是判断内存地址,也可以理解为判断是否为同一对象
```python
a = User('132')
b = a
print(a is b) # 打印的将是True，因为b = a，所以a is b
```  
### pass
&emsp;pass 关键字作用相当于占位符，例子：
```python
def ex():
    pass
```
例如例子中的ex方法，我只想声明一个空方法不做任何实现，但假如这里没有任何代码的话不符合python的语法会报错，
所以就有了pass关键字，表示是个占位符
### global  
&emsp;global 关键字是为了在函数里改变全局变量的值而存在的  
```python
hehe=6
def f():
    hehe=2
    print(hehe) #这里打印的将是2，优先使用局部变量

def next():
    global hehe #这里的global声明就是使用全局的那个hehe变量
    print(hehe)
```