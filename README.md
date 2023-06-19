import pygame
import random

# Initialize Pygame
pygame.init()

# Define colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

# Set the dimensions of the game window
window_width = 800
window_height = 600
window_size = (window_width, window_height)

# Create the game window
window = pygame.display.set_mode(window_size)
pygame.display.set_caption("Snake Game")

# Set the clock for controlling the game's frame rate
clock = pygame.time.Clock()

# Set the initial position and size of the snake
snake_block_size = 20
snake_speed = 15
snake_list = []

# Function to display the snake on the game window
def draw_snake(snake_block_size, snake_list):
    for x in snake_list:
        pygame.draw.rect(window, GREEN, [x[0], x[1], snake_block_size, snake_block_size])

# Main game loop
def game_loop():
    game_over = False
    game_end = False

    # Initial position and direction of the snake
    x1 = window_width / 2
    y1 = window_height / 2
    x1_change = 0
    y1_change = 0

    # Create the initial length of the snake
    snake_length = 1

    # Generate the position of the food
    foodx = round(random.randrange(0, window_width - snake_block_size) / 20.0) * 20.0
    foody = round(random.randrange(0, window_height - snake_block_size) / 20.0) * 20.0

    while not game_over:
        while game_end == True:
            # Display game over message and options
            window.fill(BLACK)
            font_style = pygame.font.SysFont(None, 50)
            message = font_style.render("Game Over!", True, RED)
            window.blit(message, [window_width / 2 - 100, window_height / 2 - 50])
            message = font_style.render("Press Q-Quit or C-Play Again", True, RED)
            window.blit(message, [window_width / 2 - 220, window_height / 2 + 50])
            pygame.display.update()

            # Process user input
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_end = False
                    if event.key == pygame.K_c:
                        game_loop()

        # Capture and process user input events
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change = -snake_block_size
                    y1_change = 0
                elif event.key == pygame.K_RIGHT:
                    x1_change = snake_block_size
                    y1_change = 0
                elif event.key == pygame.K_UP:
                    y1_change = -snake_block_size
                    x1_change = 0
                elif event.key == pygame.K_DOWN:
                    y1_change = snake_block_size
                    x1_change = 0

        # Check if the snake hits the boundaries of the game window
        if x1 >= window_width or x1 < 0 or y1 >= window_height or y1 < 0:
           
