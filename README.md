# create TASK 1 : Hangman Game

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

# create TASK 2: Stock Portfolio Tracker

stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "MSFT": 300,
    "GOOG": 2800
}

portfolio = {}
total_investment = 0

print("Enter your stock portfolio (type 'done' to finish):")
while True:
    stock = input("Enter stock symbol: ").upper()
    if stock == "DONE":
        break
    if stock not in stock_prices:
        print("Stock not available!")
        continue
    qty = int(input(f"Enter quantity of {stock}: "))
    portfolio[stock] = qty
    total_investment += stock_prices[stock] * qty

print("\nYour Portfolio:")
for stock, qty in portfolio.items():
    print(f"{stock}: {qty} shares")

print("Total Investment Value = $", total_investment)

with open("portfolio.txt", "w") as file:
    file.write("Portfolio Summary:\n")
    for stock, qty in portfolio.items():
        file.write(f"{stock}: {qty} shares\n")
    file.write(f"Total Investment = ${total_investment}\n")

# crate TASK 3: Task Automation

import os
import shutil

source_folder = "source_images"
destination_folder = "moved_images"

if not os.path.exists(destination_folder):
    os.makedirs(destination_folder)

for file in os.listdir(source_folder):
    if file.endswith(".jpg"):
        shutil.move(os.path.join(source_folder, file),
                    os.path.join(destination_folder, file))
        print(f"Moved: {file}")

print("All .jpg files moved successfully!")

# create TASK 4: Basic Chatbot

def chatbot():
    print("Chatbot: Hello! I am your simple chatbot. Type 'bye' to exit.")

    while True:
        user_input = input("You: ").lower()

        if user_input in ["hi", "hello"]:
            print("Chatbot: Hi there!")
        elif user_input in ["how are you"]:
            print("Chatbot: I'm fine, thanks!")
        elif user_input == "bye":
            print("Chatbot: Goodbye! Have a great day.")
            break
        else:
            print("Chatbot: Sorry, I didn't understand that.")

chatbot()
