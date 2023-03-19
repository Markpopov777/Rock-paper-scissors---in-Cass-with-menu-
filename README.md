# Rock-paper-scissors---in-class-with-menu-
Rock paper scissors - in class with menu 


import random
import sys

class Game:
    def __init__(self):
        self.num_games_played = 0
        self.num_wins_player = 0
        self.num_wins_computer = 0

    def makeYourChoice(self):
        print("Press R for Rock")
        print("Press P for Paper")
        print("Press S for Scissors")
        print("Press Q for Quit!")

        userChoice=input("What do you want choice?").lower()

        if userChoice == "r":
            return "Rock"
        if userChoice == "p":
            return "Paper"
        if userChoice == "s":
            return "Scissors"
        if userChoice == "q":
            sys.exit(0)
        else:
            return self.makeYourChoice()

    def computerRandom(self):
        options=["Rock","Paper","Scissors"]
        randomChoice = random.randint(0,2)
        return options[randomChoice]

    def comparison(self, humanChoice, computerChoice):
        if humanChoice == computerChoice:
            return "Draw"
        if humanChoice == "Rock" and computerChoice =="Paper":
            return "Computer wins"
        if humanChoice == "Paper" and computerChoice =="Rock":
            return "Player wins"
        if humanChoice == "Scissors" and computerChoice =="Rock":
            return "Computer wins"
        if humanChoice == "Rock" and computerChoice =="Scissors":
            return "Player wins"
        if humanChoice == "Paper" and computerChoice =="Scissors":
            return "Computer wins"
        if humanChoice == "Scissors" and computerChoice =="Paper":
            return "Player wins"

    def play(self):
        while self.num_games_played < 5:
            humanChoice = self.makeYourChoice()
            computerChoice = self.computerRandom()
            print ("You chose", humanChoice)
            print("The computer chose", computerChoice)
            result = self.comparison(humanChoice, computerChoice)
            if result == "Draw":
                print("It's a draw!")
            elif result == "Player wins":
                print("Congratulations, you win!")
                self.num_wins_player += 1
            else:
                print("Unlucky, you lost!")
                self.num_wins_computer += 1
            self.num_games_played += 1
            print("")
        print("Game over! You won", self.num_wins_player, "game(s) and the computer won", self.num_wins_computer, "game(s).")

game = Game()
game.play()
