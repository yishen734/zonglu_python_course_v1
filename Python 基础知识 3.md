# Python 基础知识 3

## 0. 上一节课知识回顾和答疑

## 1. Python 字符串操作


## 2. Python 的高级数据类型 (List, Tuple, Sets and Dictionary)
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

</br>
创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：
```python
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5, 6]
list3 = ["a", "b", "c", "d"]
```

### 访问列表中的值
```
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
```python

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

### 循环一个列表
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
元组里面的元素是 ```有序的```， ```可不以改变的```，但```允许重复的```
与此同时，元组元素是索引的，第一个元素的索引为 0，第二个为 1，以此类推

</br>
### 创建元组
```python
thistuple = ("apple", "banana", "cherry")
print(thistuple)
```

### 访问元组中的值
```
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

```
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

### 循环一个列表
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

### 列表的其他操作
![image](https://user-images.githubusercontent.com/70382342/213334232-c9351a25-7360-413d-b754-7c403fc7666b.png)
