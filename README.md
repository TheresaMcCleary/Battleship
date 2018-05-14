# Battleship
#Battleship game
from random import randint

board = []

# Create a 5 x 5 board filled with O

for x in range(5):
  board.append(["O"] * 5)

def print_board(board):
  for row in board:
    # print the board with only O, no quote marks or commas
    print " ".join(row)

print_board(board)


# function that generates a random number from 0 to 4 for the row
def random_row(board):
  return randint(0, len(board) - 1)

def random_col(board):
  return randint(0, len(board[0]) - 1)


# this is where the battle ship is located
ship_row = random_row(board)
ship_col = random_col(board)
#print ship_row
#print ship_col

# Everything from here on should go in your for loop!

# Player only has 4 chances to guess
number_of_turns = 2
for turn in range(number_of_turns):
 
# Be sure to indent four spaces!
    guess_row = int(raw_input("Guess Row: "))
    guess_col = int(raw_input("Guess Col: "))

    if guess_row == ship_row and guess_col == ship_col:
      print "Congratulations! You sunk my battleship!"
      break
    else:
      if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
        print "Oops, that's not even in the ocean."
      elif(board[guess_row][guess_col] == "X"):
        print "You guessed that one already."
      else:
        print "You missed my battleship!"
        board[guess_row][guess_col] = "X"
        
      if turn == number_of_turns - 1:
        print "Game Over"
        print "The Battle Ship was at row ", ship_row, "and column ", ship_col
        
  # Print (turn + 1) here!
    print_board(board)
    print "Turn", turn + 1
   
