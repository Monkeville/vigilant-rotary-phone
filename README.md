import pygame
import sys

# Initialize Pygame
pygame.init()

# Constants
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
BG_COLOR = (135, 206, 235)  # Sky blue

# Setup the screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption('Monkey Mayhem')

# Load monkey image
monkey_img = pygame.image.load('monkey.png')
monkey_rect = monkey_img.get_rect()
monkey_rect.topleft = (SCREEN_WIDTH // 2, SCREEN_HEIGHT // 2)

# Game loop
clock = pygame.time.Clock()
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
    
    # Get the set of keys pressed
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        monkey_rect.x -= 5
    if keys[pygame.K_RIGHT]:
        monkey_rect.x += 5
    if keys[pygame.K_UP]:
        monkey_rect.y -= 5
    if keys[pygame.K_DOWN]:
        monkey_rect.y += 5

    # Draw everything
    screen.fill(BG_COLOR)
    screen.blit(monkey_img, monkey_rect)
    pygame.display.flip()

    clock.tick(30)
