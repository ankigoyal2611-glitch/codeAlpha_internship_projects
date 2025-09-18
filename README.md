#TASK 1 : Hangman Game


import random

def hangman():
    words = ["apple", "banana", "orange", "mango", "grapes"]
    word = random.choice(words)
    guessed = "_" * len(word)
    guessed_list = list(guessed)
    attempts = 6
    used_letters = []
    
    print("Welcome to Hangman Game!")

    while attempts > 0 and "_" in guessed_list:
        print("\nWord:", " ".join(guessed_list))
        print("Attempts left:", attempts)
        guess = input("Enter a letter: ").lower()

        if guess in used_letters:
            print("You already guessed that letter!")
            continue
        used_letters.append(guess)

        if guess in word:
            for i in range(len(word)):
                if word[i] == guess:
                    guessed_list[i] = guess
            print("Good guess!")
        else:
            attempts -= 1
            print("Wrong guess!")

    if "_" not in guessed_list:
        print("\nCongratulations! You guessed the word:", word)
    else:
        print("\nGame Over! The word was:", word)

hangman()
