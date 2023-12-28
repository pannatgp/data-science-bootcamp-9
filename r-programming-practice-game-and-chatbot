# R 
## Create a function called 'game' for a rock-paper-scissors game 

game <- function() {

 # Greeting

    print("Hello, welcome to the game")

    flush.console()
    username <- readline("What's your name: ")

    print(paste("Let's play game!", username))

 # Explain the rules

    print("The rules are: Rock beats scisscors. Scissors beats paper. Paper beats rock.")

 # Collect score for user and computer
    user_score <- 0
    robot_score <- 0
    play_again <- 'y'

 # Play game until user not typing y

     while(play_again == 'y')
     {  flush.console()
        input <- as.integer(readline("Say HI! We will be playing ROCK(1) - PAPER(2) - SCISSORS(3)!!! Please type 1,2 or 3: "))
        if (input == 1) {
        i = "ROCK"
        }else if (input == 2){
        i = "PAPER"
        }else if (input == 3){
        i = "SCISSORS"
        }else {
        print("Game Over. Try again. Input 1, 2 or 3")
        flush.console()
        break
        }

    #Sampling data for robot

        hands <- c("ROCK", "PAPER", "SCISSORS")
        robot = sample(hands,1)

    #Show result

        print(paste("You are", i))
        print(paste("The opponent is", robot))

        # Draw
        if(i == robot) {
                print("Draw")
                user_score = user_score + 1
                robot_score = robot_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))

        # User Wins !
        }else if (i == "ROCK" & robot == "SCISSORS"){
                print("ํYou Win!")
                user_score = user_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))
        }else if (i == "PAPER" & robot == "ROCK"){
                print("ํYou Win!")
                user_score = user_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))
        }else if (i == "SCISSORS" & robot == "PAPER"){
                print("You Win!")
                user_score = user_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))

         # User Loses!
        }else if (i == "ROCK" & robot == "PAPER" ){
                print("You lose.")
                robot_score = robot_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))
        }else if (i == "PAPER" & robot == "SCISSORS"){
                print("You lose.")
                robot_score = robot_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))
        }else if (i == "SCISSORS" & robot == "ROCK"){
                print("You lose.")
                robot_score = robot_score + 1
                print(paste("Your score: ", user_score))
                print(paste("The opponent score: ", robot_score))

        # Other wise (user types integer other than 1,2,3)
        }else {
                print( "You broke the rules. Out of order")
                print(paste("Your score: ", user_score))
                print(robot_score("The opponent score: ", robot_score))
        }

        # Ask if user would like to play again
        flush.console()
        play_again <- as.character(readline("Would you like to play again? type: y if yes "))

        if(play_again != 'y')
            {
                print("Game has finished.")
                flush.console()
                break
            }
      }
}

## Create a function called 'chatbot' for a simple order pizza chatbot
chatbot <- function() {

    # Pizza's menu
    menu = data.frame(
        id = c(1:6),
        pizza = c(rep("Dark Cutie Hawaiian",2), rep("Seafood On The Beach",2), rep("Pepperoni Paparazzi",2)),
        size = c("Whole pizza","Piece","Whole pizza","Piece","Whole pizza","Piece"),
        price = c(500, 100, 600, 200, 400, 60)
    )
    bill <- 0

    # Ask a customer what to order
    username <- readline("Your name please..")
    add <- 'y'

    while ( add == 'y' ) {
        pizza <- readline("Hi! What would u like to order?, Sir \n
        Here is the menu.
        We have 3 Kinds.
        1- Dark Cutie Hawaiian
        2- Seafood On The Beach
        3- Pepperoni paparazzi
        Please type 1, 2 or 3: ")

        # Generate menu
        if (pizza == 1) {
            p = "Dark Cutie Hawaiian"
        } else if (pizza == 2){
            p = "Seafood On The Beach"
        } else if (pizza == 3){
            p = "Pepperoni Paparazzi"
        } else {
            print("Try again. Input 1, 2 or 3")
            game()
        }

        # Ask customer which size would you like (a whole pizza/ pieces)
        how <- readline(
        "
            How would you like to order?
            1 - By A whole pizza
                    or
            2 - By A piece
            Please type 1 or 2: ")

        # Generate size of pizza
        if (how == 1) {
            h = "Whole pizza"
        } else if (how == 2){
            h = "Piece"
        }  else {
            print("Try again from the beginning. Input 1 or 2 on this stage. ")
            game()
        }

        # Ask a customer the amount would like to order
        many <- as.integer(readline("Please insert the amount of your order. "))

        # Calculate order
        bill <- menu$price[menu$pizza == p & menu$size == h]*many + bill
        print(bill)
        print(paste("You ( Mr./Mrs./Ms.", username, ")", "order", p , "for", many , h))
        print(paste("Current bill is ", bill, "Baht"))

        # Ask if a customer would like to order more.
        flush.console()
        add <- readline("Would you like to order anything else, Sir?
                        (y/n): ")
        add <- tolower(add)
    }

    # Print order
    if( add != 'y'){
        print(paste("Total bill is ", bill, "Baht"))
        print(paste("Thank you :) Have a good day kaa, sir . Please wait for the button and press next to proceed a payment."))
        print("Dear Wonderful Customer, Please Transfer to Bank Account (Bank A) : 745-1-03912-6")
    }
}
