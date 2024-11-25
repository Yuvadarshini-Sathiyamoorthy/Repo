# Ex.No: 11  Mini Project 
### DATE:                                                                            
### REGISTER NUMBER : 212221230126
### AIM: 
To write a python program to simulate the game using the Hangman game in Pygame is to create an interactive game where the player tries to guess a hidden word by suggesting letters within a limited number of guesses.
### Algorithm:
1.Initialize Pygame: Set up the Pygame environment and create a window.

2.Load Assets: Load images, fonts, and words for the game.

3.Set Up Game Variables:
Create a list of words for the game.
Select a random word for the player to guess.
Initialize variables for guessed letters, incorrect guesses, and the number of allowed attempts.

4.Game Loop:
Handle events such as key presses for guessing letters.
Check if the guessed letter is in the word.
Update the display with guessed letters and the hangman state (number of incorrect guesses).
End the game if the word is guessed or the number of attempts is exceeded.

5.Display Result: Show whether the player won or lost.

6.Exit Game: Allow the game to close when the player quits.

### Program:
```
import pygame
import random

# Initialize Pygame
pygame.init()

# Set up display
WIDTH, HEIGHT = 800, 600
win = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Hangman Game")

# Load images
images = [pygame.image.load(f"hangman{i}.png") for i in range(7)]

# Set up fonts
FONT = pygame.font.SysFont('comicsans', 50)
WORD_FONT = pygame.font.SysFont('comicsans', 60)
LETTER_FONT = pygame.font.SysFont('comicsans', 40)

# Game variables
word_list = ['PYTHON', 'HANGMAN', 'PYGAME', 'COMPUTER']
word = random.choice(word_list)
guessed = []
hangman_status = 0

# Colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Main game loop
run = True
while run:
    win.fill(WHITE)
    # Draw the word
    display_word = ""
    for letter in word:
        if letter in guessed:
            display_word += letter + " "
        else:
            display_word += "_ "
    text = WORD_FONT.render(display_word, True, BLACK)
    win.blit(text, (400 - text.get_width() // 2, 200))

    # Draw hangman
    win.blit(images[hangman_status], (150, 100))

    pygame.display.update()

    # Event handling
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        if event.type == pygame.KEYDOWN:
            if event.key >= pygame.K_a and event.key <= pygame.K_z:
                letter = chr(event.key).upper()
                if letter not in guessed:
                    guessed.append(letter)
                    if letter not in word:
                        hangman_status += 1

    # Check for win or loss
    if all(letter in guessed for letter in word):
        print("You won!")
        run = False
    if hangman_status == 6:
        print("You lost!")
        run = False

pygame.quit()

```








### Output:

![image](https://github.com/user-attachments/assets/cf91c40f-7120-45a2-9da2-cce13b626d5c)


### Result:
Thus the simple  game was implemented using  the pygame of Hangman game is sucessfully executed.  
