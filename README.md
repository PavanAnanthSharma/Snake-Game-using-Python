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
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 3: Initialize snake position and its size.

- After initializing snake position, initialize the fruit position randomly anywhere in the defined height and width.
- By setting direction to RIGHT we ensure that, whenever a user runs the program/game, the snake must move right to the screen.
``` python
# defining snake default position
snake_position = [100, 50]

# defining first 4 blocks of snake
# body
snake_body = [ [100, 50],
				[90, 50],
				[80, 50],
				[70, 50]
			]
# fruit position
fruit_position = [random.randrange(1, (window_x//10)) * 10,
				random.randrange(1, (window_y//10)) * 10]
fruit_spawn = True

# setting default snake direction
# towards right
direction = 'RIGHT'
change_to = direction
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 4: Create a function to display the score of the player. 

- In this function, firstly we’re creating a font object i.e. the font color will go here.
- Then we are using render to create a background surface that we are going to change whenever our score updates.
- Create a rectangular object for the text surface object (where text will be refreshed)
- Then, we are displaying our score using blit. blit takes two argument screen.blit(background,(x,y))
``` python
# initial score
score = 0

# displaying Score function
def show_score(choice, color, font, size):

	# creating font object score_font
	score_font = pygame.font.SysFont(font, size)
	
	# create the display surface object
	# score_surface
	score_surface = score_font.render('Score : ' + str(score), True, color)
	
	# create a rectangular object for the
	# text surface object
	score_rect = score_surface.get_rect()
	
	# displaying text
	game_window.blit(score_surface, score_rect)
```

