# hangman
#importing the modules
import random
import time

#taking user's information
def info() :
    username = input("Type ur fullname:")
    print("Hello," +username,"Let's play HANGMAN!")
    time.sleep(1) #wait for 1 second

#defining the words for the game
def get_word() :
    words = ['dragontales','shinchan','oswald','noddy','doraemon','mrbean','ninjahatori','kiterestu']
    return random.choice(words)

#method so the user can play again 
def play_again() :
    print("Do you want to play again??")
    ans = input('yes or noo?')
    if ans == 'yes' :
        play_game()
    else :
        pass
                
#method of game
def play_game() :
    #creates an empty variable 
    guesses = ''

    #determines the number of turns the user gets to guess the word
    chances = 10

    #word is taken from list to guess
    word = get_word()
    print("Your HINT:The word is ", len(word),"characters long. Start guesssing...")
    print(len(word) * '*')

    #wait for 0.5 second
    time.sleep(0.5) 
    #letters = 'abcdefghijklmnopqrstuvwxyz'
    
    #creating a while loop checking if the turns are greater then zero
    while chances > 0 :

        #initializing the counter to zero
        failed = 0  

        #printing the number of chances 
        print("You have " + str(chances) + " chances to guess the word.")
        for char in word :
            #checking if the letter is in the player's guess
            if char in guesses :    
                #printing the letter
                print(char),        
            else :
                #if not found printing * 
                print("*"),
                #incrementing the failed counter with one
                failed += 1         
            
        # if failed counter remains zero
        if failed == 0 :
            #printing you won
            print ("CONGRTULATIONS!YOU'VE WON.")        
            #printing the word guessed
            print ("The word is :" ,word)
            #exiting the statement
            break
        #taking a user input for guessing the word
        guess = input('Please enter one letter or the full word :')
        #set the players' guess to guesses
        guesses += guess
        #if guessed letter is not in word
        if guess not in word :
            #decrementing the chance counter by one
            chances -= 1
            print("EHH! WRONG GUESS.")
            #printing the remaining number of chances left to guesss
            print("You have " + str(chances) + " chances left.")
        #if counter turns equal to zero
        if chances == 0 :
            #printing you lost
            print("Sorry! No more chances left.You've lost.")
            
def main() :
    #calling the method to get info of user
    info()
    #calling the method so user can play the game
    play_game()
    #callling the method if user wants to play again
    play_again()

main()
    
