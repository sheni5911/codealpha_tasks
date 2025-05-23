# codealpha_tasks
import random

def hangman():
    words = ["python", "programming", "hangman", "challenge", "openai"]
    word = random.choice(words)
    guessed_letters = []
    tries = 6

    print("Welcome to Hangman!")
    print("_ " * len(word))

    while tries > 0:
        guess = input("Guess a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print("Good guess!")
        else:
            print("Wrong guess.")
            tries -= 1

        display_word = ""
        for letter in word:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "

        print("\n" + display_word.strip())
        print(f"Tries left: {tries}")

        if "_" not in display_word:
            print("Congratulations, you won!")
            break
    else:
        print(f"Sorry, you lost. The word was '{word}'.")

# Run the game
hangman()
