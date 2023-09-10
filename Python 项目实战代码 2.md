```python3
# python --version => 检查 python 是否被安装成功
# pip --version => 检查 pip 是否被安装成功
# pip install pygame => 安装 pygame
# 尝试是否可以成功 import pygame

import random
import pygame
from pygame.color import THECOLORS as COLORS
from pygame.locals import *


"""
和画相关的方程
"""
def draw_background():
    # 游戏的背景色
    screen.fill(COLORS['white'])
    
    # 计分板
    pygame.draw.rect(
        screen, 
        COLORS['black'], 
        (-100, GAME_SIZE[1], 2000, 200), 
        0
    )

def draw_wall():
    for x, y in wall_list:
        pygame.draw.rect(
            screen,
            COLORS['black'],
            (x - WALL_WIDTH / 2, y - WALL_HEIGHT / 2, WALL_WIDTH, WALL_HEIGHT),
            WALL_WIDTH
        )

def draw_food():
    for x, y, color_index in food_list:
        pygame.draw.rect(
            screen,
            FOOD_COLORS[color_index],
            (x - FOOD_WIDTH / 2, y - FOOD_HEIGHT / 2, FOOD_WIDTH, FOOD_HEIGHT),
            0
        )
        
def draw_snake():
    # 画蛇的头部 （圆形）
    head_x, head_y = snake_list[0]
    pygame.draw.circle(
        screen,
        COLORS['red'],
        (head_x, head_y),
        int(SNAKE_WIDTH / 2),
        0
    )
    
    # 画蛇的身体 (矩形)
    for x, y in snake_list[1:]:
        pygame.draw.rect(
            screen,
            COLORS['darkblue'],
            (x - SNAKE_WIDTH / 2, y - SNAKE_HEIGHT / 2, SNAKE_WIDTH, SNAKE_HEIGHT),
            2
        )

def draw_context():
    text_string = "Snake Length: " + str(len(snake_list))
    text = FONT_M.render(text_string, True, COLORS['lightblue'])
    x, y = 10, GAME_SIZE[1] + int(CONTEXT_AREA_HEIGHT / 2)
    y = int(y - FONT_M.size(text_string)[1] / 2)
    screen.blit(text, (x, y))

def draw_pause():
    surface = pygame.Surface(SIZE, pygame.SRCALPHA)
    surface.fill((255, 255, 255, 220))
    screen.blit(surface, (0, 0))    
    text_string = "PAUSE"
    text = FONT_M.render(text_string, True, COLORS['darkgray'])
    x, y = SIZE[0] / 2, SIZE[1] / 2
    x = int(x - FONT_M.size(text_string)[0] / 2)
    y = int(y - FONT_M.size(text_string)[1] / 2)
    screen.blit(text, (x, y))

def draw_dead():
    surface = pygame.Surface(SIZE, pygame.SRCALPHA)
    surface.fill((255, 255, 255, 240))
    screen.blit(surface, (0, 0))    
    text_string = "YOU DEAD"
    text = FONT_M.render(text_string, True, COLORS['black'])
    x, y = SIZE[0] / 2, SIZE[1] / 2
    x = int(x - FONT_M.size(text_string)[0] / 2)
    y = int(y - FONT_M.size(text_string)[1] / 2)
    screen.blit(text, (x, y))


"""
和蛇核心逻辑相关的方程
"""
def check_food():
    snake_head_x, snake_head_y = snake_list[0]
    snake_head_rect = (snake_head_x - SNAKE_WIDTH / 2, snake_head_y - SNAKE_HEIGHT / 2, SNAKE_WIDTH, SNAKE_HEIGHT)
    for i in range(len(food_list)):
        food_x, food_y, _ = food_list[i]
        food_rect = (food_x - FOOD_WIDTH / 2, food_y - FOOD_HEIGHT / 2, FOOD_WIDTH, FOOD_HEIGHT)
        if rect_intersect(snake_head_rect, food_rect):
            add_body()
            del food_list[i]
            return True
    return False

def add_body(length = 1):
    for _ in range(length):
        last1, last2 = snake_list[-1], snake_list[-2]
        last1_x, last1_y = last1
        last2_x, last2_y = last2
        # 尾部的方向朝上或者朝下
        if last1_x == last2_x:
            # 尾部朝下
            if last1_y < last2_y:
                snake_list.append([last1_x, last1_y - SNAKE_HEIGHT])
            # 尾部朝上
            else:
                snake_list.append([last1_x, last1_y + SNAKE_HEIGHT])
        # 尾部的方向朝左或者朝右 
        else:       
            # 尾部朝右
            if last1_x < last2_x:
                snake_list.append([last1_x - SNAKE_WIDTH, last1_y])
            # 尾部朝左
            else:
                snake_list.append([last1_x + SNAKE_WIDTH, last1_y])

def add_food():
    while(True):
        new_food = [random.choice(X_LIST), random.choice(Y_LIST), random.choice([i for i in range(len(FOOD_COLORS))])]  
        new_food_xy = [new_food[0], new_food[1]]
        if new_food_xy not in wall_list:
            food_list.append(new_food)
            break
    
def check_dead():
    snake_head_x, snake_head_y = snake_list[0]
    snake_head_rect = (snake_head_x - SNAKE_WIDTH / 2, snake_head_y - SNAKE_HEIGHT / 2, SNAKE_WIDTH, SNAKE_HEIGHT)
    
    # 检查蛇头和边缘有没有碰撞
    if (snake_head_x < 0 or snake_head_x > GAME_SIZE[0] or snake_head_y < 0 or snake_head_y > GAME_SIZE[1]):
        return True
    # 检查蛇头和墙壁有没有碰撞
    for wall_x, wall_y in wall_list:
        wall_rect = (wall_x - WALL_WIDTH / 2, wall_y - WALL_HEIGHT / 2, WALL_WIDTH, WALL_HEIGHT)
        if rect_intersect(snake_head_rect, wall_rect):
            return True    
    # 检查蛇头和蛇自己的身体有没有碰撞
    for snake_body_x, snake_body_y in snake_list[1:]:
        snake_body_rect = (snake_body_x - SNAKE_WIDTH / 2, snake_body_y - SNAKE_HEIGHT / 2, SNAKE_WIDTH, SNAKE_HEIGHT)
        if rect_intersect(snake_head_rect, snake_body_rect):
            return True
    return False    

 
"""
工具类方程
"""       
def rect_intersect(rect1, rect2):
    x1, y1, w1, h1 = rect1
    left_x1 = int(x1)
    right_x1 = int(x1 + w1)
    up_y1 = int(y1)
    down_y1 = int(y1 + h1)
        
    x2, y2, w2, h2 = rect2
    left_x2 = int(x2)
    right_x2 = int(x2 + w2)
    up_y2 = int(y2)
    down_y2 = int(y2 + h2)
    
    hasNoIntersect = (left_x2 >= right_x1 or right_x2 <= left_x1 or down_y2 <= up_y1 or up_y2 >= down_y1)
    return not hasNoIntersect

# 程序的入口
if __name__ == "__main__":
    # 利用 pygame 去对游戏进行一个初始化
    pygame.init()
    
    # 定义所有需要的常量
    GAME_SIZE = [900, 900]
    X_LIST = [x for x in range(GAME_SIZE[0])]
    Y_LIST = [y for y in range(GAME_SIZE[1])]
    CONTEXT_AREA_HEIGHT = 100
    SIZE = [GAME_SIZE[0], GAME_SIZE[1] + CONTEXT_AREA_HEIGHT]
    FONT_S = pygame.font.SysFont("Times", 50)
    FONT_M = pygame.font.SysFont("Times", 90)
    FOOD_COLORS = [(46, 139, 87), (199, 21, 133), (25, 25, 112), (255, 215, 0)]
    
    # 创建屏幕
    screen = pygame.display.set_mode(SIZE)
    
    # 定义一下关卡相关的信息
    frame = 0.05
    count_time = 0
    
    # 表达墙
    WALL_WIDTH, WALL_HEIGHT = 30, 30
    wall_list = [[100, 200], [600, 500], [350, 200], [500, 800]]
    
    # 表达食物 (x, y, color_index)
    FOOD_WIDTH, FOOD_HEIGHT = 14, 14
    food_list = [(150, 200, 0), (300, 500, 1), (740, 542, 2), (300, 600, 3), (700, 600, 1)]
    
    # 表达蛇
    SNAKE_WIDTH, SNAKE_HEIGHT = 12, 12
    snake_list = [[100, 100], [100 - SNAKE_WIDTH * 1, 100], [100 - SNAKE_WIDTH * 2, 100], [100 - SNAKE_WIDTH * 3, 100], [100 - SNAKE_WIDTH * 4, 100]]
    
    # 主循环 （帧函数）
    running = True
    pause = False
    dead = False
    direction = 'right'
    while running:
        # 检测游戏里面发生的事件 （event）
        for event in pygame.event.get():    
            # 退出游戏 (如果不加这个，我们将无法通过常规的操作去关闭游戏)
            if event.type == pygame.QUIT:
                running = False
                break
            # 玩家是否按了上下左右的方向键
            elif event.type == pygame.KEYUP:
                # 玩家按了方向键上
                if event.key == K_UP:
                    if direction in ['left', 'right']:
                        direction = 'up'
                # 玩家按了方向键下
                elif event.key == K_DOWN:
                    if direction in ['left', 'right']:
                        direction = 'down'
                # 玩家按了方向键左
                elif event.key == K_LEFT:
                    if direction in ['up', 'down']:
                        direction = 'left'
                # 玩家按了方向键右
                elif event.key == K_RIGHT:
                    if direction in ['up', 'down']:
                        direction = 'right'
                # 玩家按了暂停键
                elif event.key == K_SPACE:
                    pause = not pause
                # 玩家按了 ESC：退出游戏
                elif event.key == K_ESCAPE:
                    running = False
                    break
            
        # 更新数据 - 让蛇动起来
        if not pause and not dead:
            count_time += frame
            head_x, head_y = snake_list[0]  # 前一帧蛇头的位置
            
            # 让蛇的身体动起来
            snake_list[1:] = snake_list[:-1] 
            
            # 让蛇的头部动起来
            if direction == 'up':
                snake_list[0] = [head_x, head_y - SNAKE_HEIGHT]
            elif direction == 'down':
                snake_list[0] = [head_x, head_y + SNAKE_HEIGHT]
            elif direction == 'left':
                snake_list[0] = [head_x - SNAKE_WIDTH, head_y]
            elif direction == 'right':
                snake_list[0] = [head_x + SNAKE_WIDTH, head_y]
            
        # 画背景 
        draw_background()
        
        # 画墙
        draw_wall()
        
        # 画食物
        draw_food()
        
        # 画蛇
        draw_snake()
        
        # 画分数
        draw_context()
        
        # 画暂停的文字
        if not dead and pause:
            draw_pause()
            
        # 画死亡的文字
        if dead:
            draw_dead()
            
        # 检查是否死亡
        dead = check_dead()
        
        # 检查一下是否吃到了食物
        if check_food():
            add_food()
            
        pygame.display.flip()
        pygame.time.delay(int(frame * 1000))
    pygame.quit()
```
