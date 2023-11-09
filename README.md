# DIGIBHEM
New repository 
import pygame
import random

# Initialize Pygame
pygame.init()

# Constants
SCREEN_WIDTH, SCREEN_HEIGHT = 800, 600
SNAKE_SIZE = 20
FPS = 10
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Set up the game window
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption('Snake Game')

# Game variables
snake = [(SCREEN_WIDTH // 2, SCREEN_HEIGHT // 2)]
snake_direction = "RIGHT"
food_position = (random.randint(0, SCREEN_WIDTH // SNAKE_SIZE - 1) * SNAKE_SIZE,
                 random.randint(0, SCREEN_HEIGHT // SNAKE_SIZE - 1) * SNAKE_SIZE)
score = 0

# Game loop
running = True
clock = pygame.time.Clock()

while running:
    screen.fill(BLACK)
    
  for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP and snake_direction != "DOWN":
                snake_direction = "UP"
            elif event.key == pygame.K_DOWN and snake_direction != "UP":
                snake_direction = "DOWN"
            elif event.key == pygame.K_LEFT and snake_direction != "RIGHT":
                snake_direction = "LEFT"
            elif event.key == pygame.K_RIGHT and snake_direction != "LEFT":
                snake_direction = "RIGHT"

    # Update snake position
    # Implement collision detection and game mechanics

    # Draw snake and food
  for segment in snake:
        pygame.draw.rect(screen, WHITE, (segment[0], segment[1], SNAKE_SIZE, SNAKE_SIZE))
    pygame.draw.rect(screen, RED, (food_position[0], food_position[1], SNAKE_SIZE, SNAKE_SIZE))

    # Update display
  pygame.display.update()

  clock.tick(FPS)

pygame.quit()
