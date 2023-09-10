```python3
import pygame
from pygame.color import THECOLORS as COLORS
from pygame.locals import *

def draw_background():
    # 游戏的背景色
    screen.fill(COLORS['white'])

def draw_snake():
    head = snake_list[0]
    pygame.draw.circle(screen, COLORS['darkred'], (head[0], head[1]), int(SNAKE_WIDTH / 2),0)
    for xy in snake_list[1:]:
        pygame.draw.rect(screen, COLORS['darkred'], (xy[0] - SNAKE_WIDTH/2, xy[1]-SNAKE_WIDTH / 2,SNAKE_WIDTH,SNAKE_HEIGHT) ,2)

if __name__ == "__main__":
    # 初始化游戏
    pygame.init()
    
    # 定义所有的常数变量
    GAME_SIZE = [900, 900]
    FONT_S = pygame.font.SysFont('Times', 50)
    FONT_M = pygame.font.SysFont('Times', 90)
    DIRECTION = ['up', 'right', 'down', 'left']
    X_LIST = [x for x in range(GAME_SIZE[0])]
    Y_LIST = [y for y in range(GAME_SIZE[1])]
    FOOD_COLORS = ((46, 139, 87), (199, 21, 133), (25, 25, 112), (255, 215, 0))

    # 墙
    WALL_WIDTH, WALL_HEIGHT = 30, 30
    wall_list = [[100, 200], [600, 500], [350, 200], [500, 800]]

    # 食物
    FOOD_WIDTH, FOOD_HEIGHT = 15, 15
    food_list = [(150, 200, 1), (300, 500, 1), (740, 542, 1), (300, 600, 1), (700, 600, 1)]

    # 蛇
    SNAKE_WIDTH, SNAKE_HEIGHT = 12, 12
    snake_list = [[100 + 12 * 4, 100], [100 + 12 * 3, 100], [100 + 12 * 2, 100], [100 + 12 * 1, 100], [100, 100]]
    snake_v = 0
    count_time = 0

    # 关卡信息
    frame = 0.05
    level = 1

    # 创建屏幕
    screen = pygame.display.set_mode(GAME_SIZE)

    # 主循环
    running = True
    pause = False
    dead = False
    head = 'right'
    while running:
        # 检测游戏里面的事件
        for event in pygame.event.get():
            # 退出游戏 (如果不加这个将无法通过常规操作关闭游戏)
            if event.type == pygame.QUIT:
                running = False
                break
            # 玩家按了暂停
            elif event.type == pygame.MOUSEBUTTONDOWN:
                pause = not pause
            # 玩家按了上下左右方向键
            elif event.type == pygame.KEYUP:
                # 玩家按了方向键上
                if event.key == K_UP:
                    if head in ['left','right']:
                        head = 'up'
                # 玩家按了方向键下
                elif event.key == K_DOWN:
                    if head in ['left','right']:
                        head = 'down'
                # 玩家按了方向键左
                elif event.key == K_LEFT:
                    if head in ['up','down']:
                        head = 'left'
                # 玩家按了方向键右
                elif event.key == K_RIGHT:
                    if head in ['up','down']:
                        head = 'right'
                # 玩家按了 ESC: 退出游戏
                elif event.key == K_ESCAPE:
                    running = False
                    break

        # 更新数据 - 让蛇移动起来
        if not pause and not dead:
            count_time += frame * level
            first = snake_list[0]
            snake_list[1:] = snake_list[:-1]
            if head == 'up':
                snake_list[0] = [first[0], first[1] - SNAKE_WIDTH]
            elif head == 'down':
                snake_list[0] = [first[0], first[1] + SNAKE_WIDTH]
            elif head == 'left':
                snake_list[0] = [first[0] - SNAKE_WIDTH, first[1]]
            elif head == 'right':
                snake_list[0] = [first[0] + SNAKE_WIDTH, first[1]]

        # 画背景
        draw_background()

        # 画蛇
        draw_snake()
        pygame.display.flip()
        pygame.time.delay(int(frame / level * 1000))
    pygame.quit()
```
