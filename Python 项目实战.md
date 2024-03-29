# Python 项目实战 - 贪吃蛇
## 游戏开发的一些基本概念介绍

### 为什么我们可以看见游戏里的角色？
我们的屏幕就像是一个巨大的网格，由非常多的像素组成。比如分辨率为 ```1920 x 1080``` 的屏幕，横轴就拥有 ```1920``` 个像素，纵轴就拥有 ```1080``` 个像素。屏幕内部的电路通过控制每一个像素块的亮度以及颜色来制造出图像。

![image](https://user-images.githubusercontent.com/70382342/221387658-b2de4db7-c566-4247-9f6f-e352f78efac8.png)


### 为什么游戏里面的物体可以动？

其本质其实就像计算机每秒通过极快的速度不断的去更新画面 (就像小时候玩的连环画一样)，从而营造出 "动的感觉"

http://www.happyjuzi.com/article-107660.html

![image](https://user-images.githubusercontent.com/70382342/221380493-9c2336c1-1a54-423a-87c9-3a573feef0fb.png)

游戏里面的帧函数使用的是同样的道理

## 脑暴 - 贪吃蛇游戏的主要功能 - 给我们自己提供一种开发的方向
1. 玩家的输入 - 玩家可以通过键盘的上下左右对贪吃蛇进行方向的控制 
2. 蛇的表达形式 - 用 list 线状的数据结构，一开始 list 里面只有 N 个元素，长度为 N （e.g. 3），吃到食物后用增加新的元素 - list 里面的第一个元素代表蛇头，其他的地方代表的是蛇的身体
3. 玩家有一个分数，这个分数代表着蛇吃到的食物的数量
4. Leaderboard - 记录玩家的最高分数
5. 在我们的帧函数里面，我们会每一帧的检查蛇头正在交互的对象是什么？有三种可能性：（1）空白 （2）墙 （3）食物
6. 空白 - 什么都不发生，蛇继续前进
7. 食物 - 蛇的长度加一 （在尾巴的位置），以此同时玩家的分数加一。把所有的食物都放在一个 list 里面
8. 墙 - 屏幕上会出现 game over 的 text，玩家失败，游戏重新开始，刷新一下 leaderboard。把所有的墙也都放在一个 list 里面
9. 蛇吃到食物之后，一个新的食物会在空白的区域（非墙，非食物）生成出来
10. 死亡的逻辑 （分数归零，蛇的长度变成初始值）触发条件：（1）蛇头撞到了墙 （2）蛇头撞到了自己的身体 （3）蛇头撞到了游戏界面的边界
11. 暂停：按了 F8，游戏会暂停，所有控制蛇移动的 input 都会无效，蛇不再移动。再按一下 F8，暂停结束，游戏恢复正常
12. 游戏重开：按了 F9，游戏会从第一个关卡重新开始
13. 我们可以给每一个关卡设置一个分数的 threshold，如果达到了这个 threshold，就会进入到下一个关卡。高级别的关卡会越来越难 （蛇的移动速度会越来越快，墙的数量会更多，食物会更少）
14. 开始游戏时候的时候，我们有一个 hero selection。我可以让玩家去选择 “hero” （蛇），玩家可以装扮这个蛇的外貌 （颜色）

## 项目开发的项目
### 游戏框架: 
```pygame```

### 安装流程
1. ```python --version```: 检查 python 是否被安装成功
2. ```pip --version```: 查 pip 是否被安装成功
3. ```pip install pygame```: 装 pygame
4. 尝试是否可以成功 ```import pygame```
