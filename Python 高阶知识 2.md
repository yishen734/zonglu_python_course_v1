# Python 高阶知识 2

## 继承 (Inheritance)
继承允许我们定义一个类，该类继承另一个类的所有属性 （attribute） 和方法 （method）。 父类是被继承的类，也叫作基类。 子类是继承自另一个类的类，也称为派生类。

![image](https://user-images.githubusercontent.com/70382342/216195958-1227ae1e-9d77-493b-b033-cfdab815c728.png)

对于 ```Employee``` 来说，```Person``` 就是它的父类，对于 ```Person``` 来说，```Employee``` 就是它的父类。然后对于 ```Developer``` 来说，```Employee``` 就是它的子类，而对于 ```Employee``` 来说， ```developer``` 就是它的子类。

继承最大的好处是子类获得了父类的全部功能。比如说 ```Person``` 有 ```run()``` 这个方法，那么，```Employee```, ```Customer``` 作为它的子类，什么额外的事情也不需要做，就自动拥有了 ```run()``` 方法，这帮助我们大量减少了代码重复的问题。

我自己在游戏开发过程中遇见的真实案例：
- ```BaseCharacter``` - 最基本的类，有一些最基本的功能，比如可以行走，收到伤害，但是不可以攻击对方
- ```CombatCharacter``` - 继承于 ```BaseCharacter```，拥有 ```BaseCharacter``` 的所有功能的同时也可以进行攻击
- ```AIEnemyCharacter``` - 继承于 ```CombatCharacter```，拥有 ```CombatCharacter``` 的所有功能的同时还有一些 AI 的行为，比如巡逻
- ```PlayerCharacter``` - 继承于 ```CombatCharacter```，拥有 ```CombatCharacter``` 的所有功能的同时还有一些玩家独有的能力，比如可以被控制器操控，有自己的装备栏，有自己的仓库系统等等

## 组合 (Composition)
和继承有所不一样的是，组合更加强调解耦性。即把各种功能或者能力拆分成一个个有的拼图，需要什么的时候直接像插入 USB 一样直接激活就行。
- ```BaseCharacter``` - 最基本的类，有一些最基本的功能，比如可以行走，收到伤害，但是不可以攻击对方
- ```CombatCharacter``` - 在 ```BaseCharacter``` 的基础上，插了一个 ```CombatComponent``` 从而赋予其可以攻击的能力
- ```AIEnemyCharacter``` - 在 ```BaseCharacter``` 的基础上，插了一个 ```CombatComponent``` 赋予其可以攻击的能力，并且插了一个 ```AIComponent``` 赋予其类似巡逻这种的 AI 行为
- ```PlayerCharacter``` - 在 ```BaseCharacter``` 的基础上，插了一个 ```CombatComponent``` 赋予其可以攻击的能力，并且插了一个 ```ControlComponent``` 赋予其可以被玩家控制的能力，还差了一个比如叫做 ```WallClimbComponent``` 去赋予其可以攀爬墙壁的能力

组合这一概念在游戏开发中使用的非常频繁，其最大的优势就是非常的灵活，可以做到即插即拔。在游戏开发领域，很多开发者都会把自己做的小插件封装成为一个 component，然后其他玩家购买之后可以直接像 USB 一样插到自己的游戏角色中去赋予其有些比较特定的能力 (比如可以爬墙，可以跳伞，可以释放爪钩等等)


### 创建父类
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname
    
  def run(self):
    print("Person: I am running")

person = Person("John", "Doe")
person.run()
```


## 继承 - 创建子类
```python
class Employer(Person):
  # __init__ 是 python 的构造器，如果我们在子类里面将其省略，那么父类的构造器会被自动调用。如果我们没有省略，那么新加的构造器会将父类的构造器进行重载
  def __init__(self, firstname, lastname, age):
    # 我们也可以通过 super 来显性的调用父类的构造器
    super().__init__(firstname, lastname)
    self.age = age

  def printInfo(self):
    print("This is {} {}, and I am {} years old".format(self.firstname, self.lastname, self.age))
```


## 继承 - 多态
多态性依赖于继承。从一个父类派生出多个子类，可以使子类之间有不同的行为，这种行为称之为多态。
更直白的说，就是子类重写父类的方法，使子类具有不同的方法实现。子类与父类拥有同一个方法，子类的方法优先级高于父类，即子类覆盖父类。
```python
class Person:
  def __init__(self, firstname, lastname):
    self.firstname = firstname
    self.lastname = lastname

  def run(self):
    print("Person: I am running")
    
class Employer(Person):
  def __init__(self, firstname, lastname, year):
    super().__init__(firstname, lastname)
    self.graduationyear = year

  def run(self):
    print("Employer: I am running")
    
class Employee(Person):
  def __init__(self, firstname, lastname, age):
    super().__init__(firstname, lastname)
    self.age = age

  def run(self):
    print("Employee: I am running")
     
person = Person("John", "Doe")
student = Employer("Jack", "Li", 30)
teacher = Employee("Jason", "Mooney", 25)
person.run()
student.run()
teacher.run()
```

### 习题 1
设计一个基类叫做 ```Animal```, 拥有以下 methods
1. ```构造器 __init__``` - 接受三个参数，```size```，```color```, ```name``` 并将其赋值给自身的 ```attributes```
2. ```Eat()``` - 打印 ```"Animal is eating"```

设计一个子类叫做 Dog, 继承 Animation, 并且重载 ```Eat()``` - 打印 ```"Dog is eating"```，并且拥有以下新 ```attributes```
1. ```height``` 并且重载父类 ```__init__``` 接受一个新的参数 ```Height```

和以下新方程
1. ```Bark()``` - 打印 ```"{name} is barking"```

设计另外一个子类叫做 Cat, 继承 Animation, 并且重载 ```Eat()``` - 打印 ```"Cat is eating"```，并且拥有以下新 ```attributes```
1. ```age``` 并且重载父类 ```__init__``` 接受一个新的参数 ```age```

并且拥有一个新方程
1. ```Sleep()``` - 打印 ```"{name} is sleeping"```



