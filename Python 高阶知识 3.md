# 访问限制的概念
- ```Public```: 可以从类外部访问。在 ```Python``` 中，```public``` 是默认修饰符

- ```Protected```: 只能类的内部或者派生类中访问

- ```Private```: 只能从类的内部访问，不允许外部访问。

访问限制符主要是为了实现数据的封装，让数据可以更安全的被访问和使用。如果没有访问限制符 (即所有的成员变量和方法都是公开的)，这意味着我们可以随意篡改类里面的一些核心数值，这是一种很危险的行为。这就引入了 ```getter``` 和 ```setter``` 的概念。


## Getter 和 Setter
想要获得私有变量的值，必须通过 ```getter``` 来获得。同理，想要修改私有变量的值，需要通过 ```setter``` 来修改。```setter``` 在大多数情况下充当着一个 ```数据合法验证``` 的作用，保证用户传入的数值是合法的。


## Python 的访问限制符
很多面向对象的语言都提供了 ```public```，```private``` 和 ```protected``` 等关键字来限定类方法和属性的访问方式。

其中，类的 ```private``` 成员是无法在类外被访问或调用的，他们只允许在类内进行访问和调用。类的 ```public``` 成员允许在类外被访问和调用。

这一机制使得我们可以用 ```公有（public）方法``` 间接访问 ```私有（private）实例变量``` 来实现数据的封装。

类的 ```protected``` 成员除了可以在类内访问和调用，还可以在子类中进行操作。这些保证了父类的一些资源可以被继承到子类。

那么 ```python``` 中有类似的关键字来控制类内资源的访问权限吗？答案是没有。```python``` 并没有提供类似的机制。一般我们采用在实例变量名和方法名前面加下滑线的方式来模仿 ```private``` 的机制

```python3
class Person:
    def __init__(self, firstname, lastname, age):
        self.firstname = firstname
        self.lastname = lastname
        self._age = age
    
class Employee(Person):
    def __init__(self, firstname, lastname, age, salary):
        super().__init__(firstname, lastname, age)
        self.__salary = salary

  # getter: 借助 public 方程去访问私有变量
  def get_salary(self):
      return self.__salary
  
  # setter: 借助 public 方程去改变私有变量
  def set_salary(self, new_salary):
      if (new_salary >= 0):
          self.__salary = new_salary
      
# 创建 Person 实例
bob = Person("Bob", "Male", 22)
print(bob.firstname)
print(bob.lastname)

# 创建 Employee 实例
jason = Employee("jason", "Male", 24, 100000)
# print(jason.__salary)  # 直接访问私有变量会报错
print(jason._age)
print(jason.get_salary())
jason.set_salary(150000)
print(jason.get_salary())
```

&emsp;
# Python 里面的模块概念
```Python 模块``` 是包含 Python 定义和语句的文件。一个模块可以定义函数、类和变量，也可以包括可执行的代码。将相关的代码分组到一个模块中，使得代码更容易理解和使用，同时也使得代码更具有逻辑性。比如所有和数学运算相关的方程都被放到了 ```math``` 的模块里面。当我们想借助 python 的一些自带方程实现一些数学运算的时候，我们第一时间想到的就是导入 ```math``` 模块，然后调用里面的方程

如果不对代码进行模块上的划分，而是全部写在一个文件里，会对代码的可读性产生巨大的负面影响，也非常的难维护。幻想一下，如果 python 的开发者把所有的 python 源码都放在一个单独的文件里，维护的难度以及出 bug 的可能性想想就觉得恐怖。

```python3
# 一个简单的 module: calculation.py
def add(x, y):
    return x + y
 
def subtract(x, y):
    return x - y
    
def multiple(x, y):
    return x * y

def square(x):
    return x * x
```


## 模块的导入
### 模块的整个导入
```python3
# 导入 module calculation.py
import calculation
 
print(calculation.add(1, 2))
```

```python3
from calculation import *
 
print(add(1, 2))
print(square(4))
```

### 模块的部分导入
```python3
# 从 calculation module 里面只导入 add() 和 square() 方程
from calculation import add, square

# 如果我们写的是 “import calculation”，那么我们在调用方程的时候就需要写 calculation.add(1, 2) 和 calculation.square(4)
print(add(1, 2))
print(square(4))
```
