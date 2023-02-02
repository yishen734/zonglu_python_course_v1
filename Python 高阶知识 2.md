# Python 高阶知识 2

## 继承
继承允许我们定义一个类，该类继承另一个类的所有属性 （attribute） 和方法 （method）。 父类是被继承的类，也叫作基类。 子类是继承自另一个类的类，也称为派生类。

![image](https://user-images.githubusercontent.com/70382342/216195958-1227ae1e-9d77-493b-b033-cfdab815c728.png)

对于 ```Employee``` 来说，```Person``` 就是它的父类，对于 ```Person``` 来说，```Employee``` 就是它的父类。然后对于 ```Developer``` 来说，```Employee``` 就是它的子类，而对于 ```Employee``` 来说， ```developer``` 就是它的子类。

继承最大的好处是子类获得了父类的全部功能。比如说 ```Person``` 有 ```run()``` 这个方法，那么，```Employee```, ```Customer``` 作为它的子类，什么额外的事情也不需要做，就自动拥有了 ```run()``` 方法，这帮助我们大量减少了代码重复的问题。

我自己在游戏开发过程中遇见的真实案例：
- ```BaseCharacter``` - 最基本的类，有一些最基本的功能，比如可以行走，收到伤害，但是不可以攻击对方
- ```CombatCharacter``` - 继承于 ```BaseCharacter```，拥有 ```BaseCharacter``` 的所有功能的同时也可以进行攻击
- ```AIEnemyCharacter``` - 继承于 ```CombatCharacter```，拥有 ```CombatCharacter``` 的所有功能的同时还有一些 AI 的行为，比如巡逻
- ```PlayerCharacter``` - 继承于 ```CombatCharacter```，拥有 ```CombatCharacter``` 的所有功能的同时还有一些玩家独有的能力，比如可以被控制器操控，有自己的装备栏，有自己的仓库系统等等


### 创建父类
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname
    
  def run():
    print("Person: I am running")

person = Person("John", "Doe")
person.run()
```


### 创建子类
```python
class Employer(Person):
  def __init__(self, firstname, lastname, age):
    super().__init__(firstname, lastname)
    self.age = age

  def printInfo(self):
    print("This is {} {}, and I am {} years old".format(self.firstname, self.lastname, self.age))
```


## 多态
多态性依赖于继承。从一个父类派生出多个子类，可以使子类之间有不同的行为，这种行为称之为多态。
更直白的说，就是子类重写父类的方法，使子类具有不同的方法实现。子类与父类拥有同一个方法，子类的方法优先级高于父类，即子类覆盖父类。
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname

  def run():
    print("Person: I am running")
    
class Employer(Person):
  def __init__(self, firstname, lastname, year):
    super().__init__(firstname, lastname)
    self.graduationyear = year

  def run():
    print("Employer: I am running")
    
class Employee(Person):
  def __init__(self, firstname, lastname, age):
    super().__init__(firstname, lastname)
    self.age = age

  def run():
    print("Employee: I am running")
     
person = Person("John", "Doe")
student = Employer("Jack", "Li", 30)
teacher = Employee("Jason", "Mooney", 25)
person.run()
student.run()
teacher.run()
```
