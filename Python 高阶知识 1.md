# 方程 (Function)
简单来说，方程就是一块可执行代码，并且只要当我们去它的时候，它才会被执行。

我们可以给方程传递数据，于此同时，方程也可以再执行完毕之后返回值。


## 方程的定义和调用
```python3
def my_function1():
    print("Hello from a function 1")
    
def my_function2():
    print("Hello from a function 2")

def my_function3():
    print("Hello from a function 3")
  
my_function1()
my_function2()
my_function3()
```


## 方程的 Parameter
我们可以将数据传递给方程的 ```parameters``` 当中。```Parameters``` 通常在方程名的括号中被定义。我们可以添加任意数量的 ```parameter```，只需要用逗号将它们隔开即可。
```python3
# 下面这个方程有一个 parameter，叫做 name
def my_function(name):
    print("Hello ", name)
  
my_function("Jack")
my_function("Tom")
my_function("Lily")
```


## Argument 和 Paramters 的区别是什么
从方程的角度来看：

Paramter 是方程定义的时候括号内列出的变量。

Argument 则是调用函数时发送给函数的值

默认情况下，必须使用正确数量的 argument 调用函数。

这意味着如果函数需要 2 个 parameter，我们需要使用 2 个 argument 调用该函数，不能多也不能少 （对于有默认值的 paramter 除外）。


## Keyword Arguments
我们在给方程传递 ```arguments``` 的时候可以用 ```key = value``` 的语法。
这样我们就可以使得 argument 的顺序变得是可以任意的。
```python3
def my_function(child3, child2, child1):
    print("The youngest child is " + child3)

my_function(child1 = "Jack", child2 = "Tom", child3 = "Lily")
```


## 方程的默认值
```python3
def my_function(country = "China"):
    print("I am from " + country)

my_function("US")
my_function("India")
my_function("UK")
my_function()
```


## 方程可以接受任何类型参数
我们可以把任意类型的 argument 传递给方程 (string, number, list, dictionary etc.)

下面的例子中我们将一个 list 作为 argument 进行了传递，在 function 的 paramter ```food``` 接受了这个 argument 之后，自己也随之被转化成为了 list
```python
def my_function(food):
    for x in food:
        print(x)
        
fruits = ["apple", "banana", "cherry"]
my_function(fruits)
```


## 方程的返回值
方程不仅仅可以接受值，同时也可以返回值
```python3
def my_function(x):
    return 5 * x

print(my_function(3))
print(my_function(5))
print(my_function(9))
```

### 习题 1
设计一个方程，参数是一个数字 num。如果 num 是奇数，则打印 “这是个奇数”，否则则打印 “这是个偶数” 


### 习题 2
设计一个方程 get_max() 可以计算三个数值的最大值并且将其返回
```
例子：list = [1, 2, 3], ans = 3
```

### 习题 3
设计一个方程 multiply()，其接受一个 list 作为参数，然后返回 list 中所有数的乘积
```
例子：list = [1, 2, 3, 4, 5], ans = 120
```

### 习题 4
设计一个方程 string_reverse(), 其接受一个 string 作为参数，然后把其反转过后的 string 返回
```
例子：orginal_str = '1234abcd', reversed_str = 'dcba4321'
```

### 习题 5
算法经典入门题：两数之和

给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
我们可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
```
例子:
给定 nums = [2, 7, 11, 15], target = 9
由于 nums[0] + nums[1] = 2 + 7 = 9, 所以返回 [0, 1]
```




# 面对对象编程
一讲到面向对象编程，我们就需要知道什么是 ```对象（obejct）``` 以及什么是 ```类(class)```。


## 对象 （Object）
一个对象可以由两个特点来描述：
1. ```属性（Attributes）```
2. ```行为（Behavior）```

猫的例子：

一只猫有 ```大小```，```体重```，```颜色```等等的这些属性。与此同时，猫可以```走```，```跑```，```跳```，```吃饭```，```喝水```。我们把这些东西称之为它的```行为```
世上任何事物都可以用 ```属性``` 和 ```行为``` 来表示，这也是为什么我们在面对对象编程里面老是说 ```世间万物皆为对象```


## 类 （Class）
类就是对一类有共同属性和行为的对象的总称，相当于对象的蓝图。我们则根据这个蓝图去构造我们想要的对象
比如：猫，狗，狮子，老虎，等等这一些我们可以定义一个共同的类来描述它们，Class animal；在这个类里面我们可以定义一些描述这个动物的属性和方法。


## 属性（Attributes）
比如动物就包含大小（size）和体重（weight）这两个属性
```python3
class animal:
    # 这是类的构造器
    def __init__(self, size, weight):
        self.size = size
        self.weight = weight
        
cat = animal(1, 2)
print(cat.size)
print(cat.weight)
```


## 方法（Method）
而我们则用之前学习到的方程（在 class 中也叫做 method）来描述一个对象的行为
```python3
class animal:
    def __init__(self, size, weight):
        self.size = size
        self.weight = weight
    
    def display_info(self):
        print("My size is {}, and weight is ".format(self.size, self.weight))
        
cat = animal(1, 2)
cat.display_info()
```


### 习题 6
定义一个类叫做 car, 其拥有 ```size```，```color```，```brand```，```price```，```current_direction``` 五个属性，```current_direction``` 的默认值为 ```none```
与此同时，定于以下 methods:
1. ```launch()``` -> 调用的时候会打印 ```汽车已经启动```, 并且把 ```current_direction``` 设置为 ```forward```
2. ```turn_around()``` -> 调用后会把 ```current_direction``` 进行反转，i.e. 如果之前是 ```forward```，则变成 ```backward```，之前是 ```backward```，那么现在就变为 ```forward```
3. ```stop()``` -> 调用后会打印 ```汽车已经停止```，并且把 ```current_direction``` 设置为 ```backward```
4. ```sell()``` -> 接受一个 number 作为参数，如果其值大于汽车的 ```price```，打印 ```汽车成功出售```，否则打印 ```金钱不足, 出售失败```
