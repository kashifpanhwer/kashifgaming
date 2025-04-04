import random

def create_board(): numbers = list(range(1, 9)) + [None]  # Numbers 1-8 and an empty space random.shuffle(numbers) return [numbers[i:i+3] for i in range(0, 9, 3)]

def display_board(board): for row in board: print(" ".join(str(cell) if cell else "_" for cell in row))

def find_empty(board): for i, row in enumerate(board): for j, cell in enumerate(row): if cell is None: return i, j

def move_tile(board, direction): i, j = find_empty(board) moves = {'up': (i-1, j), 'down': (i+1, j), 'left': (i, j-1), 'right': (i, j+1)} if direction in moves: new_i, new_j = moves[direction] if 0 <= new_i < 3 and 0 <= new_j < 3: board[i][j], board[new_i][new_j] = board[new_i][new_j], board[i][j] return True return False

def is_solved(board): return board == [[1, 2, 3], [4, 5, 6], [7, 8, None]]

def play_game(): board = create_board() while not is_solved(board): display_board(board) move = input("Move (up, down, left, right): ") if move in {'up', 'down', 'left', 'right'}: if not move_tile(board, move): print("Invalid move!") else: print("Invalid input! Use up, down, left, or right.") print("Congratulations! You solved the puzzle!")

if name == "main": play_game()


