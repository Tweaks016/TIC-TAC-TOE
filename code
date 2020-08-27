from IPython.display import clear_output
import random

# DISPLAYING THE BOARD 
def display_board(board):

  clear_output()
  print("      |      |     ")
  print("   {}  |  {}   |  {} ".format(board[7],board[8],board[9]))
  print(" -----+------+------")
  print("      |      |     ")
  print("   {}  |  {}   |  {} ".format(board[4],board[5],board[6]))
  print(" -----+------+------ ")
  print("      |      |     ")
  print("   {}  |  {}   |  {} ".format(board[1],board[2],board[3]))


# Player marker choice
def choose_input():

      marker = ' '
      while marker not in ('X', 'O'):
          marker = input(" Player 1, choose your marker (X or O):").upper()
          player_1_marker = marker

          if marker not in ('X', 'O'):
              print(" Sorry, invalid choice! ")
          if player_1_marker == 'X':
              player_2_marker = 'O'
          else:
              player_2_marker = 'X'
      return (player_1_marker, player_2_marker)   

# to check who goes first
def who_goes_first():
    if random.randint(0,1) == 0:
        return 'Player_2'
    else:
        return 'Player_1'

#
def place_marker(board, marker, position):
    board[position] = marker


# Checks for winner
def winner(board,mark):
    
    mark = [mark[0]] * 3

    if board[:6:-1] == mark or board[6:3:-1] == mark or board[3:0:-1] == mark:
        return True
    if board[:0:-3] == mark or board[8::-3] == mark or board[7::-3] == mark:
        return True
    if board[::-4] == mark or board[7:1:-2] == mark:
        return True
    return False

# Checks and returns a boolean value if
# it finds a blank space
def space_check(board,position):
    if board[position] == ' ':
        return True
    return False

# Checking wheather board is filled or not
def no_space_left(board):
    for i in range(1,10):
        if space_check(board, i):
            return False
    return True 


# Acccepting user input 
def player_choice(board):

    position = 0
    while position not in [1, 2, 3, 4, 5, 6, 7, 8, 9] or space_check(board, position) == False:
        position  = int(input(" Next position (1-9): "))
        if space_check(board, position) == False:
            print (f" Position {position} is already occupied")
        if position not in range(1,10):
            print(" Entered a wrong position! ")
        
    return position

# Asking wheather player wants to play again or not
def play_again():

    user_dec = input(" Do you want to play again (Y/N): ")
    if user_dec in  ('y', 'Y'):
        return True
    return False


# Game starts here
print("--------------------------")
print("\n\n  Welcome to Tic Tac Toe \n\n")
print("--------------------------")
while True:
    board = [' '] * 10
    player1_mark, player2_mark = choose_input()

    Turn = who_goes_first()
    print(Turn + ', will go first')

    Start_the_game = input("\n Are you ready to play ? Enter (Y/N): ").lower()
    if Start_the_game == 'y':
        game_on = True
    else:
        game_on = False
    
    while game_on :

        # For Player 1
        if Turn == 'Player_1':
            display_board(board)
            position = player_choice(board)
            place_marker(board, player1_mark, position)            
            if winner(board, player1_mark):
                display_board(board)
                print(" Congratulation, Player 1 won the game! ")
                game_on = False
            else:
                if no_space_left(board) :
                    display_board(board)
                    print(" The game is draw! ")
                    game_on = False
                else:
                    Turn = 'Player_2'
        else:
            # For Player 2
            display_board(board)
            position = player_choice(board)
            place_marker(board, player2_mark, position)            
            if winner(board, player2_mark):
                display_board(board)
                print(" Congratulation, Player 2 won the game! ")
                game_on = False
            else:
                if no_space_left(board) :
                    display_board(board)
                    print(" The game is draw! ")                    
                    game_on = False
                else:
                    Turn = 'Player_1'
    if not play_again() :
        break
