## Snake-Game-in-Python

>Introdction:

Snake game is one of the most popular arcade games of all time. In this game, the main objective of the player is to catch the maximum number of fruits without hitting the wall or itself.It is one of the best beginner-friendly projects that every novice programmer should take as a challenge. Learning to build a video game is kinda interesting and fun learning. We will be using Pygame to create this snake game. Pygame is an open-source library that is designed for making video games. It has inbuilt graphics and sounds libraries. It is also beginner-friendly, and cross-platform. 

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Dependecies:

- Pygame
- How to download : use code: ``` pip install pygame```, in your terminal
- *Make sure you have pip installed*

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 1: Firstly we are importing the necessary libraries.

- After that, we are defining the width and height of the window in which the game will be played.
- And define the color in RGB format that we are going to use in our game for displaying text.
``` python
# importing libraries
import pygame
import time
import random

snake_speed = 15

# Window size
window_x = 720
window_y = 480

# defining colors
black = pygame.Color(0, 0, 0)
white = pygame.Color(255, 255, 255)
red = pygame.Color(255, 0, 0)
green = pygame.Color(0, 255, 0)
blue = pygame.Color(0, 0, 255)
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 2: After importing libraries we need to initialize Pygame using pygame.init() method. 

- Create a game window using the width and height defined in the previous step.
- Here pygame.time.Clock() will be used further in the main logic of the game to change the speed of the snake.
``` python
# Initialising pygame
pygame.init()

# Initialise game window
pygame.display.set_caption('GeeksforGeeks Snakes')
game_window = pygame.display.set_mode((window_x, window_y))

# FPS (frames per second) controller
fps = pygame.time.Clock()

```
