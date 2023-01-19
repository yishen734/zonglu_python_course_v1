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

### List (列表)
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

访问列表中的值
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

# 判断一个元素是否在列表里
thislist = ["apple", "banana", "cherry"]
if "apple" in thislist:
  print("Yes, 'apple' is in the fruits list")
```python

获得列表的长度
```python
list1 = ["apple", "banana", "cherry"]
print(len(list1))
```

更新列表
```python
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "mango"]
thislist[1:3] = ["blackcurrant", "watermelon"]
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.insert(2, "watermelon")
print(thislist)
```

插入列表元素
```python
thislist = ["apple", "banana", "cherry"]
thislist.append("orange")
print(thislist)

thislist = ["apple", "banana", "cherry"]
thislist.insert(2, "watermelon")
print(thislist)
```

移除列表元素
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

循环一个列表
```python
thislist = ["apple", "banana", "cherry"]
for x in thislist:
  print(x)
  
thislist = ["apple", "banana", "cherry"]
for i in range(len(thislist)):
  print(thislist[i])
```
