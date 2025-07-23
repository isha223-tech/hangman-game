# hangman-game
This is my first git repository.
<br>
author - Isha saini


import random

# List of words
words = ["apple", "banana", "orange", "grapes", "mango"]

# Randomly choose one word
word = random.choice(words)
word_letters = list(word)  # convert word into list
guessed_letters = []       # to store correct guesses
tries = 6                  # number of chances

print("Welcome to Hangman!")
print("_ " * len(word))    # show blank spaces

while tries > 0:
    guess = input("Guess a letter: ").lower()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter only one letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    if guess in word_letters:
        print("Good job!")
        guessed_letters.append(guess)
    else:
        print("Wrong guess!")
        tries -= 1
        print(f"Tries left: {tries}")

    # Show current progress
    display = ""
    for letter in word_letters:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    print(display)

    # Check if all letters guessed
    if set(guessed_letters) >= set(word_letters):
        print("Congratulations! You won 🎉")
        break
else:
    print("Game Over! The word was:", word)











