# Python 基础知识2

## 0. 上一节课知识回顾和答疑


## 1. Python 的算术运算符 (加减乘除，取模， 幂，整除)
这一小节主要给大家讲讲 ```Python``` 的运算符。举个简单的例子 ```4 + 5 = 9```。 例子中，```4``` 和 ```5``` 被称为 ```操作数```，```+``` 称为 ```运算符```。
| 算术运算符   |  描述                                              |   
|  ---------  |  ------------------------------------------------  | 
|  +          |  加 - 两个数相加                                    | 
|  -          |  减 - 用一个数减去另一个数                           |
|  *          |  乘 - 两个数相乘或是返回一个被重复若干次的字符串       |
|  /          |  除 - x 除以 y                                      |
|  %          |  取模 - 返回除法的余数                               |
|  **         |  幂 - 返回 x 的 y 次幂                              |
|  //         |  整除 - 返回商的整数部分（向下取整）                  |


```python
a = 4
b = 3

# 加
c = a + b
print("c 的值为：%s" %c)

# 减
c = a - b
print("c 的值为：%s" %c)
 
# 乘
c = a * b
print("c 的值为：%s" %c)

# 除
c = a / b
print("c 的值为：%s" %c)
 
# 取模
c = a % b
print("c 的值为：%s" %c)
 
# 幂
c = a ** b 
print("c 的值为：%s" %c)

# 整除
c = a // b 
print("c 的值为：%s" %c)
```

## 2. Python 赋值运算符
| 赋值运算符   |  描述                |   例子                                   | 
|  ---------  |  ------------------- | ----------------------------------------| 
|  =          |  简单的赋值运算符     | c = a + b 将 a + b 的运算结果赋值为 c     | 
|  +=          |  加法赋值运算符      | c += a 等效于 c = c + a                  | 
|  -=          |  减法赋值运算符      | 	c -= a 等效于 c = c - a                 | 
|  *=          |  乘法赋值运算符      | c *= a 等效于 c = c * a                  | 
|  /=          |  除法赋值运算符      | 	c /= a 等效于 c = c / a                 | 
|  %=          |  取模赋值运算符      | c %= a 等效于 c = c % a                  | 
|  **=         |  幂赋值运算符       |  c **= a 等效于 c = c ** a              | 
|  //=         |  取整除赋值运算符   |	c //= a 等效于 c = c // a               | 

```python
a = 2
b = 3
 
# 简单的赋值运算符
c = a + b
print("c 简单赋值运算后的值为：%s" %c)

# 加法赋值运算符
c += a
print("c 加法赋值运算后的值为：%s" %c)

# 减法赋值运算符
c -= a
print("c 减法赋值运算后的值为：%s" %c)

# 乘法赋值运算符
c *= a
print("c 乘法赋值运算后的值为：%s" %c)
 
# 除法赋值运算符
c /= a 
print("c 除法辅助运算后的值为：%s" %c)

# 取模赋值运算符 
c %= a
print("c 取模赋值运算后的值为：%s" %c)

# 幂赋值运算符
c **= a
print("c 幂赋值运算后的值为：%s" %c)
 
# 取整除赋值运算符
c //= a
print("c 取整除赋值后的值为：%s" %c)
```

## 3. Python 的用户输入输出
```python
str = input("请输入：")
print("你输入的内容是: ", str)
```


### 习题 1
输入三个数，分别赋值给 value1, value2, value3。然后再把 value1，value2，value3 打印出来


## 4. Python 数据类型转换
有时候，我们需要对数据内置的类型进行转换，数据类型的转换，一般情况下你只需要将数据类型作为函数名即可。
</br>
Python 数据类型转换可以分为两种：
</br>
(1) 隐式类型转换 - 自动完成  
(2) 显式类型转换 - 需要使用类型函数来转换

```python
num_int = 123
num_float = 1.23
num_new = num_int + num_float

print("datatype of num_int:", type(num_int))
print("datatype of num_float:", type(num_float))

print("Value of num_new:", num_new)
print("datatype of num_new:", type(num_new))

# num_int 数据类型为: <class 'int'>
# num_flo 数据类型为: <class 'float'>
# num_new: 值为: 124.23
# num_new 数据类型为: <class 'float'>

# 可以发现新的变量 num_new 是 浮点型（float），这是因为 Python 会将较小的数据类型转换为较大的数据类型，以避免数据丢失。
```

```python
num_int = 123
num_str = "456"

print("Data type of num_int:", type(num_int))
print("Data type of num_str:", type(num_str))
print(num_int + num_str)
# num_int 数据类型为: <class 'int'>
# num_str 数据类型为: <class 'str'>
# TypeError: unsupported operand type(s) for +: 'int' and 'str'

# 在显式类型转换中，用户将对象的数据类型转换为所需的数据类型。 我们使用 int()、float()、str() 等预定义函数来执行显式类型转换。
# int() 强制转换为整型：
x = int(1)    
y = int(2.8)
z = int("3")
print(x)  # x 输出结果为 1
print(y)  # y 输出结果为 2
print(z)  # z 输出结果为 3

# float() 强制转换为浮点型：
x = float(1)
y = float(2.8)
z = float("3")
w = float("4.2")
print(x)  # x 输出结果为 1.0
print(y)  # y 输出结果为 2.8
print(z)  # z 输出结果为 3.0
print(w)  # w 输出结果为 4.2

# str() 强制转换为字符串类型：
x = str("s1")
y = str(2)
z = str(3.0)
print(x)  # x 输出结果为 's1'
print(y)  # y 输出结果为 '2'
print(z)  # z 输出结果为'3.0'
```


### 习题 2
输入三个数，分别赋值给 value1, value2, value3。然后再把 value1，value2，value3 从 str 类型强转成 int 类型，分别赋值给 a，b， c， 并且打印出来


## 5. Python 的条件语句
Python 条件语句是通过一条或多条语句的执行结果（True 或者 False）来决定执行的代码块。
![image](https://user-images.githubusercontent.com/70382342/212439046-208bbb84-78c8-48bd-bba3-c7386912c847.png)
```python
if 判断条件：
    执行语句……
else：
    执行语句……
```


### 例子
```python
flag = False
name = "Jack"
if name == "Python":         # 判断变量是否为 python 
    flag = True              # 条件成立时设置标志为真
    print("Welcome!")        # 并输出欢迎信息
else:
    print(name)              # 条件不成立时输出变量名称
print(flag)
```


### 习题 3
输入三个数，然后再输出三个数中最大的数作为结果


```python
if 判断条件1:
    执行语句 1...
elif 判断条件2:
    执行语句 2...
elif 判断条件3:
    执行语句 3...
else:
    执行语句 4...
```

```python
num = 5     
if num == 3:            # 判断 num 的值
    print("A")        
elif num == 2:
    print("B")
elif num == 1:
    print("C")
elif num < 0:           # 值小于零时输出
    print("Error")
else:
    print("Python")     # 条件均不成立时输出
```


## 6. Python 的逻辑运算符 (and, or, not)
```python
num = 9
if num >= 0 and num <= 10:    # 判断值是否在 0 ~ 10 之间
    print("A")
# 输出结果: A
 
num = 10
if num < 0 or num > 10:    # 判断值是否在小于 0 或大于 10
    print("A")
else:
    print("B")
# 输出结果: B
 
num = 8
# 判断值是否在 0 ~ 5 或者 10 ~ 15 之间
if (num >= 0 and num <= 5) or (num >= 10 and num <= 15):    
    print("A")
else:
    print("B")
# 输出结果: B

num = 8
if (not num >= 0):    
    print("A")
else:
    print("B")
```


### 习题 4
编码一个年龄判断器: 即输入一个年龄
(1) 如果年龄在 60 岁以及 60 岁以上，打印 “老年”
(2) 如果年龄在 35 ~ 59 岁之间，打印 “中年”
(3) 如果年龄在 18 ~ 34 岁之间，打印 “青年”
(4) 如果年龄在 7 ~ 17 岁之间， 打印 "少年"
(4) 否则打印 "儿童"


## 7. Python 里的循环语句 (for, while)
| 循环类型     |  描述                                             |   
|  ---------  |  ------------------------------------------------ | 
|  while 循环 |  在给定的判断条件为 true 时执行循环体，否则退出循环体  | 
|  for 循环   |  重复执行语句                                       |
|  嵌套循环    | 你可以在循环体中嵌套其他循环                         |

```python
# While 循环
count = 0
while (count < 5):
    print("count:" + count)
    count = count + 1
print("Good bye")

# For 循环 - 非索引
fruits = ['banana', 'apple',  'mango']
for fruit in fruits:
    print("当前水果: " + fruit)

# For 循环 - 索引
fruits = ['banana', 'apple',  'mango']
for index in range(len(fruits)):
    print ("当前水果:" + fruits[index])
```

### 习题 5
通过循环的方式把 26 个字母打印出来


## 8.循环控制语句 (break, continue)
| 控制语句         |  描述                                                      |   
|  ---------      |  ------------------------------------------------          | 
|  break 语句     |  在语句块执行过程中终止循环，并且跳出整个循环                  | 
|  continue 语句  |  在语句块执行过程中终止当前循环，跳出该次循环，执行下一次循环。  |

```python
count = 0
while (count < 10):
    if (count == 5):
        break;
    print("count: %s" %count)
    count = count + 1

count = 0
while (count < 10):
    count = count + 1
    if (count % 2 == 0):
        continue;
    print("count: %s" %count)
```

### 习题 6
分别用 ```for``` 和 ```while``` 求 1 ~ 100 所有数的和


### 习题 7：
重复打印 M ⾏，每行 N 个星星
比如: M = 5, N = 5
```python
*****
*****
*****
*****
*****
```


### 习题 8：
重复打印 M ⾏，第一行有 1 个 星星，然后后面每行的星星比上一行多一个
比如: M = 5
```python
*
**
***
****
*****
```


### 习题 9：
输入任意一个正整数，求它是几位数
比如: 30 是 2 位数， 300 是 3 位数


### 习题 10：
打印出九九乘法表

