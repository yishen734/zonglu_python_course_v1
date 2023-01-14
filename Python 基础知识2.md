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
a = 20
b = 10

# 加
c = a + b
print("c 的值为：" + c)

# 减
c = a - b
print("c 的值为：" + c)
 
# 乘
c = a * b
print("c 的值为：" + c)

# 除
c = a / b
print("c 的值为：" + c)
 
# 取模
c = a % b
print("c 的值为：" + c)
 
# 幂
a = 2
b = 3
c = a ** b 
print("c 的值为：" + c)

# 整除
a = 10
b = 4
c = a / /b 
print("c 的值为：" + c)
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
a = 20
b = 10
 
# 简单的赋值运算符
c = a + b
print("c 的值为：" + c)

# 加法赋值运算符
c += a
print("c 的值为：" + c)

# 减法赋值运算符
c -= a
print("c 的值为：" + c)

# 减法赋值运算符
c *= a
print("c 的值为：" + c)
 
# 除法赋值运算符
c /= a 
print("c 的值为：" + c)

# 取模赋值运算符 
c = 2
c %= a
print("c 的值为：" + c)

# 幂赋值运算符
c **= a
print("c 的值为：" + c)
 
# 取整除赋值运算符
c //= a
print("c 的值为：" + c)
```


## 3. Python 的条件语句
Python条件语句是通过一条或多条语句的执行结果（True或者False）来决定执行的代码块。
![image](https://user-images.githubusercontent.com/70382342/212439046-208bbb84-78c8-48bd-bba3-c7386912c847.png)
```python
if 判断条件：
    执行语句……
else：
    执行语句……
```

### 例子
``` 
flag = False
name = 'luren'
if name == 'python':         # 判断变量是否为 python 
    flag = True              # 条件成立时设置标志为真
    print("Welcome!")        # 并输出欢迎信息
else:
    print(name)              # 条件不成立时输出变量名称
```

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
    print 'boss'        
elif num == 2:
    print 'user'
elif num == 1:
    print 'worker'
elif num < 0:           # 值小于零时输出
    print 'error'
else:
    print 'roadman'     # 条件均不成立时输出
```

```python
num = 9
if num >= 0 and num <= 10:    # 判断值是否在 0 ~ 10 之间
    print 'hello'
# 输出结果: hello
 
num = 10
if num < 0 or num > 10:    # 判断值是否在小于 0 或大于 10
    print 'hello'
else:
    print 'undefine'
# 输出结果: undefine
 
num = 8
# 判断值是否在 0 ~ 5 或者 10 ~ 15 之间
if (num >= 0 and num <= 5) or (num >= 10 and num <= 15):    
    print("hello")
else:
    print("undefine")
# 输出结果: undefine
```
## 4. Python 的逻辑运算符 (and, or, not)
## 5. Python 里的循环语句 (for, while, do while, break, continue)
## 6. Python 的用户输入输出
