import pygame
import sys

pygame.init()

# Set up display
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Social Distancing Animation")

# Set up colors
white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)

# Load match image
match_image = pygame.image.load("match.png")  # You need to have a match image file

# Set up match position and speed
match_x, match_y = 100, 300
match_speed = 5

# Set up social distancing message
font = pygame.font.Font(None, 36)
message = font.render("Social Distancing Stops Spread", True, red)

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Clear the screen
    screen.fill(white)

    # Draw match
    screen.blit(match_image, (match_x, match_y))

    # Draw social distancing message
    screen.blit(message, (width // 2 - 200, height - 50))

    # Update the display
    pygame.display.flip()

    # Move match
    match_x += match_speed

    # Check if match goes off-screen
    if match_x > width:
        match_x = -match_image.get_width()

    # Pause for a short time
    pygame.time.delay(50)

# Quit the game
pygame.quit()
sys.exit()
