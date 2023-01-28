# Python 高阶知识 1

## 方程 (Function)
A function is a block of code which only runs when it is called.
You can pass data, known as parameters, into a function.
A function can return data as a result.


## 方程的定义和调用
```python3
def my_function():
    print("Hello from a function")
  
 my_function()
```


## 方程的 Argument
Information can be passed into functions as arguments.
Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma.
The following example has a function with one argument (fname). When the function is called, we pass along a first name, which is used inside the function to print the full name:
```python3
def my_function(name):
    print("Hello ", name)
  
my_function("Jack")
my_function("Tom")
my_function("Lily")
```


## Argument VS Paramters
From a function's perspective:
A parameter is the variable listed inside the parentheses in the function definition.
An argument is the value that is sent to the function when it is called.
By default, a function must be called with the correct number of arguments. 
Meaning that if your function expects 2 arguments, you have to call the function with 2 arguments, not more, and not less.


## Keyword Arguments
You can also send arguments with the key = value syntax.
This way the order of the arguments does not matter.
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


## 习题 1
设计一个方程 get_max() 可以计算三个数值的最大值并且将其返回



## 把不同的结构体传给方程
You can send any data types of argument to a function (string, number, list, dictionary etc.), and it will be treated as the same data type inside the function.

E.g. if you send a List as an argument, it will still be a List when it reaches the function:
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
