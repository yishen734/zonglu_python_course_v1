# Python 高阶知识 3
## 访问限制符概念
- ```Public```: 可以从类外部访问。在 ```Python``` 中，```public``` 是默认修饰符

- ```Protected```: 只能类的内部或者派生类中访问

- ```Private```: 只能从类的内部访问，不允许外部访问。

访问限制符主要是为了实现数据的封装，让数据可以更安全的被访问和使用

## Python 的访问限制符
很多面向对象的语言都提供了 ```public```，```private``` 和 ```protected``` 等关键字来限定类方法和属性的访问方式。

其中，类的 ```private``` 成员是无法在类外被访问或调用的，他们只允许在类内进行访问和调用。类的 ```public``` 成员允许在类外被访问和调用。

这一机制使得我们可以用 ```公有（public）方法``` 间接访问 ```私有（private）实例变量``` 来实现数据的封装。

类的 ```protected``` 成员除了可以在类内访问和调用，还可以在子类中进行操作。这些保证了父类的一些资源可以被继承到子类。

那么 ```python``` 中有类似的关键字来控制类内资源的访问权限吗？答案是没有。```python``` 并没有提供类似的机制。一般我们采用在实例变量名和方法名前面加下滑线的方式来模仿 ```private``` 的机制

```python3
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname
    
class Employee(Person):
  def __init__(self, firstname, lastname, salary):
    super().__init__(firstname, lastname)
    self.__salary = salary

  # 借助 public 方程去访问私有变量
  def get_salary(self):
      return self.__salary
      
# 创建 Person 实例
bob = Person("Bob", "Male")
print(bob.firstname)
print(bob.lastname)

# 创建 Employee 实例
jason = Employee("jason", Male, 100000)
# print(jason.__salary)
print(jason.gey_salary())
```

## Python 里面的模块概念
Python 模块是包含 Python 定义和语句的文件。一个模块可以定义函数、类和变量，也可以包括可执行的代码。将相关的代码分组到一个模块中，使得代码更容易理解和使用，同时也使得代码更具有逻辑性。

```python3
# 一个简单的 module: calc.py
def add(x, y):
    return x + y
 
def subtract(x, y):
    return x - y
```

## 模块的导入
### 模块的整个导入
```python3
# 导入 module math.py
import math
 
print(math.sqrt(16))
```

```python3
from math import *
 
print(sqrt(16))
print(factorial(6))
```

### 模块的部分导入
```python3
# 从 math module 里面只导入 sqrt() 和 factorial 方程
from math import sqrt, factorial

# 如果我们写的是 “import math”，那么我们在调用方程的时候就需要写 math.sqrt(16) 和 math.factorial()
print(sqrt(16))
print(factorial(6))
```
