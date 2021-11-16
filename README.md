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
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 5: Now create a game over function that will represent the score after the snake is hit by a wall or itself. 

- In the first line, we are creating a font object to display scores.
- Then we are creating text surfaces to render scores.
- After that, we are setting the position of the text in the middle of the playable area.
- Display the scores using blit and updating the score by updating the surface using flip().
- We are using sleep(2) to wait for 2 seconds before closing the window using quit().
```python
# game over function
def game_over():

	# creating font object my_font
	my_font = pygame.font.SysFont('times new roman', 50)
	
	# creating a text surface on which text
	# will be drawn
	game_over_surface = my_font.render('Your Score is : ' + str(score), True, red)
	
	# create a rectangular object for the text
	# surface object
	game_over_rect = game_over_surface.get_rect()
	
	# setting position of the text
	game_over_rect.midtop = (window_x/2, window_y/4)
	
	# blit wil draw the text on screen
	game_window.blit(game_over_surface, game_over_rect)
	pygame.display.flip()
	
	# after 2 seconds we will quit the
	# program
	time.sleep(2)
	
	# deactivating pygame library
	pygame.quit()
	
	# quit the program
	quit()
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 6: Now we will be creating our main function that will do the following things:

- We will be validating the keys that will be responsible for the movement of the snake, then we will be creating a special condition that the snake should not be allowed to move in the opposite direction instantaneously.
- After that, if snake and fruit collide we will be incrementing the score by 10 and new fruit will be spanned.
- After that, we are checking that is the snake hit with a wall or not. If a snake hits a wall we will call game over function.
- If the snake hits itself, the game over function will be called.
- And in the end, we will be displaying the scores using the show_score function created earlier.






