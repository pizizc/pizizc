import pygame
import random

# 初始化游戏
pygame.init()

# 创建游戏窗口
window_width = 500
window_height = 500
game_window = pygame.display.set_mode((window_width, window_height))

# 设置游戏标题
pygame.display.set_caption("跳跃的青蛙")

# 设置游戏背景颜色
background_color = (255, 255, 255)

# 设置青蛙初始位置
frog_x = window_width / 2
frog_y = window_height / 2

# 设置青蛙跳跃高度和速度
jump_height = 20
jump_speed = 5

# 游戏主循环
running = True
while running:
    # 处理事件
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # 更新青蛙位置
    frog_y += jump_speed

    # 检查青蛙是否碰到了边界
    if frog_y > window_height:
        frog_y = 0

    # 绘制背景
    game_window.fill(background_color)

    # 绘制青蛙
    frog_image = pygame.image.load("frog.png")
    frog_image = pygame.transform.scale(frog_image, (100, 100))
    game_window.blit(frog_image, (frog_x, frog_y))

    # 绘制分数
    score_image = pygame.image.load("score.png")
    score_image = pygame.transform.scale(score_image, (30, 30))
    game_window.blit(score_image, (window_width / 2 - score_image.get_width() / 2, window_height / 2 - score_image.get_height() / 2))

    # 更新屏幕
    pygame.display.flip()

    # 控制速度
    clock.tick(60)
