import pygame
import time
import random

# Initialize the game
pygame.init()

# Define colors
black = pygame.Color(0, 0, 0)
white = pygame.Color(255, 255, 255)
red = pygame.Color(255, 0, 0)
green = pygame.Color(0, 255, 0)
blue = pygame.Color(0, 0, 255)

# Set the width and height of the display window
display_width = 800
display_height = 600

# Set the size of each snake block and the speed of the snake
block_size = 20
snake_speed = 15

# Initialize the display
dis = pygame.display.set_mode((display_width, display_height))
pygame.display.set_caption('Snake Game')

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 50)
score_font = pygame.font.SysFont(None, 35)


def our_snake(block_size, snake_list):
    for x in snake_list:
        pygame.draw.rect(dis, black, [x[0], x[1], block_size, block_size])


def message(msg, color):
    mesg = font_style.render(msg, True, color)
    dis.blit(mesg, [display_width / 6, display_height / 3])


def game_loop():
    game_over = False
    game_close = False

    # Initial position of the snake
    x1 = display_width / 2
    y1 = display_height / 2

    # Initial movement of the snake
    x1_change = 0
    y1_change = 0

    # Create the snake body
    snake_list = []
    length_of_snake = 1

    # Generate the position of the food
    foodx = round(random.randrange(0, display_width - block_size) / 20.0) * 20.0
    foody = round(random.randrange(0, display_height - block_size) / 20.0) * 20.0

    while not game_over:

        while game_close:
            dis.fill(white)
            message("You lost! Press Q-Quit or C-Play Again", red)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        game_loop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change = -block_size
                    y1_change = 0
                elif event.key == pygame.K_RIGHT:
                    x1_change = block_size
                    y1_change = 0
                elif event.key == pygame.K_UP:
                    y1_change = -block_size
                    x1_change = 0
                elif event.key == pygame.K_DOWN:
                    y1_change = block_size
                    x1_change = 0

        # Check if the snake hits the boundary of the display
        if x1 >= display_width or x1 < 0 or y1 >= display_height or y1 < 0:
            game_close = True

        # Update the position of the snake
        x1 += x1_change
        y1 += y1_change

        dis.fill(white)
        pygame.draw.rect(dis, green, [foodx, foody, block
import pygame
import time
import random

# Initialize the game
pygame.init()

# Define colors
black = pygame.Color(0, 0, 0)
white = pygame.Color(255, 255, 255)
red = pygame.Color(255, 0, 0)
green = pygame.Color(0, 255, 0)
blue = pygame.Color(0, 0, 255)

# Set the width and height of the display window
display_width = 800
display_height = 600

# Set the size of each snake block and the speed of the snake
block_size = 20
snake_speed = 15

# Initialize the display
dis = pygame.display.set_mode((display_width, display_height))
pygame.display.set_caption('Snake Game')

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 50)
score_font = pygame.font.SysFont(None, 35)


def our_snake(block_size, snake_list):
    for x in snake_list:
        pygame.draw.rect(dis, black, [x[0], x[1], block_size, block_size])


def message(msg, color):
    mesg = font_style.render(msg, True, color)
    dis.blit(mesg, [display_width / 6, display_height / 3])


def game_loop():
    game_over = False
    game_close = False

    # Initial position of the snake
    x1 = display_width / 2
    y1 = display_height / 2

    # Initial movement of the snake
    x1_change = 0
    y1_change = 0

    # Create the snake body
    snake_list = []
    length_of_snake = 1

    # Generate the position of the food
    foodx = round(random.randrange(0, display_width - block_size) / 20.0) * 20.0
    foody = round(random.randrange(0, display_height - block_size) / 20.0) * 20.0

    while not game_over:

        while game_close:
            dis.fill(white)
            message("You lost! Press Q-Quit or C-Play Again", red)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        game_loop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change = -block_size
                    y1_change = 0
                elif event.key == pygame.K_RIGHT:
                    x1_change = block_size
                    y1_change = 0
                elif event.key == pygame.K_UP:
                    y1_change = -block_size
                    x1_change = 0
                elif event.key == pygame.K_DOWN:
                    y1_change = block_size
                    x1_change = 0

        # Check if the snake hits the boundary of the display
        if x1 >= display_width or x1 < 0 or y1 >= display_height or y1 < 0:
            game_close = True

        # Update the position of the snake
        x1 += x1_change
        y1 += y1_change

        dis.fill(white)
        pygame.draw.rect(dis, green, [foodx, foody, block
