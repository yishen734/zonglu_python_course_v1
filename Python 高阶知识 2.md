# Python 高阶知识 2

## 继承
Inheritance allows us to define a class that inherits all the methods and properties from another class.
Parent class is the class being inherited from, also called base class.
Child class is the class that inherits from another class, also called derived class.

![image](https://user-images.githubusercontent.com/70382342/216195958-1227ae1e-9d77-493b-b033-cfdab815c728.png)

### 创建父类
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname

  def printname(self):
    print(self.firstname, self.lastname)

x = Person("John", "Doe")
x.printname()
```


### 创建子类
```python
class Employer(Person):
  def __init__(self, firstname, lastname, age):
    super().__init__(firstname, lastname)
    self.age = age

  def printInfo(self):
    print("This is {} {}, and I am {}".format(self.firstname, self.lastname, self.age))
```


## 多态
多态性依赖于继承。从一个父类派生出多个子类，可以使子类之间有不同的行为，这种行为称之为多态。

更直白的说，就是子类重写父类的方法，使子类具有不同的方法实现。子类与父类拥有同一个方法，子类的方法优先级高于父类，即子类覆盖父类。
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname

  def printname(self):
    print(self.firstname, self.lastname)
    
class Employer(Person):
  def __init__(self, firstname, lastname, year):
    super().__init__(firstname, lastname)
    self.graduationyear = year

  def printname(self):
    print("Employer: ", self.firstname, self.lastname)
    
class Employee(Person):
  def __init__(self, firstname, lastname, age):
    super().__init__(firstname, lastname)
    self.age = age

  def printname(self):
    print("Employee: ", self.firstname, self.lastname)
    
person = Person("John", "Doe")
student = Employer("Jack", "Li", 30)
teacher = Employee("Jason", "Mooney", 25)
```
