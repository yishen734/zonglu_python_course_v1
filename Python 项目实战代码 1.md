```python3
import pygame
from pygame.color import THECOLORS as COLORS
from pygame.locals import *

def draw_background():
    screen.fill(COLORS['white'])

def draw_snake():
    # 画蛇的头
    head = snake_list[0]
    pygame.draw.circle(screen, COLORS['red'], (head[0], head[1]), int(SNAKE_WIDTH / 2), 0)

    # 画蛇的身体
    for x, y in snake_list[1:]:
        pygame.draw.rect(
            screen, 
            COLORS['darkblue'], 
            (x - SNAKE_WIDTH / 2, y - SNAKE_WIDTH / 2, SNAKE_WIDTH, SNAKE_HEIGHT), 
            2
        )

if __name__ == "__main__":
    # 初始化游戏
    pygame.init()
    
    # 创建屏幕
    GAME_SIZE = [900, 900]
    screen = pygame.display.set_mode(GAME_SIZE)

    # 关卡信息
    frame = 0.05
    level = 1

    # 蛇
    SNAKE_WIDTH, SNAKE_HEIGHT = 12, 12
    snake_list = [[100 + 12 * 4, 100], [100 + 12 * 3, 100], [100 + 12 * 2, 100], [100 + 12 * 1, 100], [100, 100]]
    count_time = 0

    # 主循环
    running = True
    pause = False
    direction = 'right'
    while running:
        # 检测游戏里面的事件
        for event in pygame.event.get():
            # 退出游戏 (如果不加这个将无法通过常规操作关闭游戏)
            if event.type == pygame.QUIT:
                running = False
                break
            # 玩家按了上下左右方向键
            elif event.type == pygame.KEYUP:
                # 玩家按了方向键上
                if event.key == K_UP:
                    if direction in ['left','right']:
                        direction = 'up'
                # 玩家按了方向键下
                elif event.key == K_DOWN:
                    if direction in ['left','right']:
                        direction = 'down'
                # 玩家按了方向键左
                elif event.key == K_LEFT:
                    if direction in ['up','down']:
                        direction = 'left'
                # 玩家按了方向键右
                elif event.key == K_RIGHT:
                    if direction in ['up','down']:
                        direction = 'right'
                # 玩家按了暂停
                elif event.key == K_SPACE:
                    pause = not pause
                # 玩家按了 ESC: 退出游戏
                elif event.key == K_ESCAPE:
                    running = False
                    break

        # 更新数据 - 让蛇移动起来
        if not pause:
            count_time += frame * level
            first = snake_list[0]
            snake_list[1:] = snake_list[:-1]
            if direction == 'up':
                snake_list[0] = [first[0], first[1] - SNAKE_WIDTH]
            elif direction == 'down':
                snake_list[0] = [first[0], first[1] + SNAKE_WIDTH]
            elif direction == 'left':
                snake_list[0] = [first[0] - SNAKE_WIDTH, first[1]]
            elif direction == 'right':
                snake_list[0] = [first[0] + SNAKE_WIDTH, first[1]]

        # 画背景
        draw_background()

        # 画蛇
        draw_snake()
        pygame.display.flip()
        pygame.time.delay(int(frame / level * 1000))
    pygame.quit()
```
