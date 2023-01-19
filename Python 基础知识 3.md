# Python 基础知识 3

## 0. 上一节课知识回顾和答疑

## 1. Python 的高级数据类型 (List, Tuple, Sets and Dictionary)
Python 中主要有 8 种数据类型：
- 简单数据类型: ```Number (数字, 其中又包括 int, float, complex), Boolean(布尔值), String (字符串), None（空值)```
- 复杂数据类型: ```List (列表), Set(集合), Tuple (元组), Dict (字典)```

| 数据类型        |  例子                                          |   
|  ------------  |  --------------------------------              |
|  Number (int)  |  ```举例: 1, 2, 3, 201, 2100```                |  
|  Number (float)|  ```举例: e.g. 1.0, 2.3, 3.1415926```          |  
|  Boolean       |  ```举例: True, False```                       |   
|  String        |  ```举例: "apple", 'banana' ```                |
|  None          |  ```举例: None ```                             |
|  List          |  ```举例: ["apple", "banana", "cherry"] ```    |
|  Set           |  ```举例: {"apple", "banana", "cherry"} ```    |
|  Tuple         |  ```举例: ("apple", "banana", "cherry") ```    |
|  Dict          |  ```举例: {"name" : "John", "age" : 36} ```    |

## List (列表)
列表是最常用的 ```Python``` 数据类型，它可以作为一个方括号内的逗号分隔值出现。

列表里面的元素是 ```有序的```， ```可以改变的```，并且```允许重复的```

与此同时，列表元素是索引的，第一个元素的索引为 0，第二个为 1，以此类推

创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：
```python
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5, 6]
list3 = ["a", "b", "c", "d"]
```

### 访问列表中的值
```python
# 正向索引
thislist = ["apple", "banana", "cherry"]
print(thislist[1])

# 反向索引
thislist = ["apple", "banana", "cherry"]
print(thislist[-1])

# 范围性正向索引
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(thislist[2:5])

thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(thislist[:4])

# 范围性反向索引
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(thislist[-4:-1])

# 判断一个元素是否存在
thislist = ["apple", "banana", "cherry"]
if "apple" in thislist:
    print("Yes, 'apple' is in the fruits list")
```

### 获得列表的长度
```python
list1 = ["apple", "banana", "cherry"]
print(len(list1))
```

### 更新列表
```python
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "mango"]
thislist[1:3] = ["blackcurrant", "watermelon"]
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.insert(2, "watermelon")
print(thislist)
```

### 插入列表元素
```python
thislist = ["apple", "banana", "cherry"]
thislist.append("orange")
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.insert(2, "watermelon")
print(thislist)
```

### 移除列表元素
```python
thislist = ["apple", "banana", "cherry"]
thislist.remove("banana")
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.pop(1)
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.pop()
print(thislist)

thislist = ["apple", "banana", "cherry"]
del thislist[0]
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.clear()
print(thislist)
```

### 遍历一个列表
```python
thislist = ["apple", "banana", "cherry"]
for x in thislist:
    print(x)
  
thislist = ["apple", "banana", "cherry"]
for i in range(len(thislist)):
    print(thislist[i])
```

### List Comprehension
```python
# newlist = [expression for item in iterable if condition == True]
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = [x for x in fruits if "a" in x]
print(newlist)

newlist = [x for x in range(10)]
print(newlist)

newlist = [x for x in range(10) if x < 5]
print(newlist)
```

### 列表的其他操作
![image](https://user-images.githubusercontent.com/70382342/213333538-5b81f54d-34c2-4b68-b2c0-13b0db46729b.png)


## Tuple (元组)
元组里面的元素是 ```有序的```， ```可以改变的```，但```允许重复的```

与此同时，元组元素是索引的，第一个元素的索引为 0，第二个为 1，以此类推


### 创建元组
```python
thistuple = ("apple", "banana", "cherry")
print(thistuple)
```

### 访问元组中的值
```python
# 正向索引
thistuple = ("apple", "banana", "cherry")
print(thistuple[1])

# 反向索引
thistuple = ("apple", "banana", "cherry")
print(thistuple[-1])

# 范围性正向索引
thistuple = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(thistuple[2:5])

thistuple = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(thistuple[:4])

# 范围性反向索引
thistuple = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(thistuple[-4:-1])

# 判断一个元素是否存在
thistuple = ("apple", "banana", "cherry")
if "apple" in thistuple:
    print("Yes, 'apple' is in the fruits tuple")
```

### 更新元组
元组是不可变的, 只可以先转化成为 list，进行改变，再转变回来。同时，我们还可以将多个元组进行拼接

```python
# 先转化成为 list，进行改变，再转变回来
thistuple = ("apple", "banana", "cherry")
y = list(thistuple)
y.append("orange")
thistuple = tuple(y)

# 把两个 tuple 进行拼接
thistuple = ("apple", "banana", "cherry")
y = ("orange",)
thistuple += y
```

### 元组元素的解耦
```python
fruits = ("apple", "banana", "cherry")

(green, yellow, red) = fruits
print(green)
print(yellow)
print(red)
```

### 遍历一个元组
```python
# 直接遍历，不通过索引
thistuple = ("apple", "banana", "cherry")
for x in thistuple:
    print(x)
 
# 通过索引
thistuple = ("apple", "banana", "cherry")
for i in range(len(thistuple)):
    print(thistuple[i])
```

### 元组的其他操作
![image](https://user-images.githubusercontent.com/70382342/213334232-c9351a25-7360-413d-b754-7c403fc7666b.png)



## Set (集合)
集合里面的元素是 ```无序的```， ```不可以改变的```，且```不可以重复的```

由于集合是无序的，里面的元素没有索引

### 创建集合
```python
thisset = {"apple", "banana", "cherry"}
print(thisset)
```

### 访问集合中的值
```python
# 每一次的结果都可能不同
thisset = {"apple", "banana", "cherry"}
for x in thisset:
    print(x)
  
# 由于集合无序，所以其元素没有索引，我们不可以通过索引对元素进行访问

# 判断一个元素是否存在
thisset = {"apple", "banana", "cherry"}
print("banana" in thisset)
```

### 给集合添加元素
```python
# 添加一个元素
thisset = {"apple", "banana", "cherry"}
thisset.add("orange")
print(thisset)

# 把集合 B 的元素都添加给集合 A
thisset = {"apple", "banana", "cherry"}
tropical = {"pineapple", "mango", "papaya"}
thisset.update(tropical)
print(thisset)
```

### 给集合移除元素
```python
# 通过 remove 移除，如果不存在会报错
thisset = {"apple", "banana", "cherry"}
thisset.remove("banana")
print(thisset)

# 通过 remove 移除，如果不存在不会报错
thisset = {"apple", "banana", "cherry"}
thisset.discard("banana")
print(thisset)

# 通过 clear() 清空所有元素 
thisset = {"apple", "banana", "cherry"}
thisset.clear()
print(thisset)

# 删除整个集合
thisset = {"apple", "banana", "cherry"}
del thisset
print(thisset)
```

### 遍历一个集合
```python
# 每一次的结果都可能不同
thisset = {"apple", "banana", "cherry"}
for x in thisset:
    print(x)
```

### 集合的其他操作
![image](https://user-images.githubusercontent.com/70382342/213335038-57858b7b-1500-430f-aa42-e8fa1d90edf9.png)



## Dictionary (字典)
字典里面的元素是 ```有序的```， ```可以改变的```，但```不可以重复的```

字典里面的元素通过 ```Key``` 和 ```value``` 组成的 ```pair``` 来构成

### 创建字典
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}
print(thisdict)
```

### 访问字典中的值
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

# 通过 key 来访问的两种办法
x = thisdict["model"]
x = thisdict.get("model")

# 获得所有的 key
car = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

x = car.keys()
print(x)
car["color"] = "white"
print(x)

# 获得所有的 value
car = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

x = car.values()
print(x)
car["year"] = 2020
print(x)

# 获得所有的元素
car = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

x = car.items()
print(x)
car["year"] = 2020
print(x)

# 判断一个 key 是否存在
if "model" in thisdict:
    print("Yes, 'model' is one of the keys in the thisdict dictionary")
```

### 改变字典里面的内容
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}
thisdict["year"] = 2018
```

### 给字典添加元素
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

thisdict["color"] = "red"
print(thisdict)
```

### 给字典移除元素
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

# 通过 pop
thisdict.pop("model")
print(thisdict)

# 通过 del
del thisdict["year"]
print(thisdict)
```

### 遍历一个字典
```python
thisdict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}

# 遍历所有的 key
for x in thisdict:
    print(x)

# 遍历所有的 value
for x in thisdict.values():
    print(x)

# 遍历所有的 item
for x, y in thisdict.items():
    print(x, y)
```

### 字典的其他操作
![image](https://user-images.githubusercontent.com/70382342/213336048-32d07a64-92df-49fe-9c2a-ab2332d28939.png)
