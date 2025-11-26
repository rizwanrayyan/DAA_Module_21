# EX 3A Knight Tour & Count Path
## DATE:29-10-2025
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight


## Algorithm

1. Initialize an empty chessboard of size `(d1, d2)` with all cells set to 0.
2. Start the knight's tour at position `(x, y)` and mark it with move number 1.
3. Repeat for each remaining move (total `d1*d2 - 1` moves):
4. Find all valid knight moves from the current position to unvisited cells.
5. From those, choose the one with the fewest onward moves (Warnsdorff’s Rule).
6. Mark the selected position with the current move number.
7. End when no more valid moves are found or the board is fully visited.
8. Print the final board (unless GUI mode is enabled).

## Program:
```
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.
Developed by: RIZWAN T
Register Number:  212222040134
```
```py
KNIGHT_MOVES = [(2, 1), (1, 2), (-1, 2), (-2, 1), (-2, -1), (-1, -2), (1, -2), (2, -1)]
class KnightTour:
    def __init__(self, board_size):
        self.board_size = board_size  # tuple
        self.board = []
        for i in range(board_size[0]):
            temp = []
            for j in range(board_size[1]):
                temp.append(0)
            self.board.append(temp) # empty cell
        self.move = 1

    def print_board(self):
        print('board:')
        for i in range(self.board_size[0]):
            print(self.board[i])

    def warnsdroff(self, start_pos, GUI=False):
        #Add your code here
        x,y=start_pos
        self.board[x][y]=self.move
        self.move+=1
        for i in range(self.board_size[0]*self.board_size[1]-1):
            next_pos=self.find_next_pos((x,y))
            if next_pos is None:
                break
            x,y=next_pos
            self.board[x][y]=self.move
            self.move+=1
        if not GUI:
            self.print_board()
            # self.board_printed=True
            
            
        

    def find_next_pos(self, current_pos):
        empty_neighbours = self.find_neighbours(current_pos)
        if len(empty_neighbours) == 0:
            return
        least_neighbour = 8
        least_neighbour_pos = ()
        for neighbour in empty_neighbours:
            neighbours_of_neighbour = self.find_neighbours(pos=neighbour)
            if len(neighbours_of_neighbour) <= least_neighbour:
                least_neighbour = len(neighbours_of_neighbour)
                least_neighbour_pos = neighbour
        return least_neighbour_pos

    def find_neighbours(self, pos):
        neighbours = []
        for dx, dy in KNIGHT_MOVES:
            x = pos[0] + dx
            y = pos[1] + dy
            if 0 <= x < self.board_size[0] and 0 <= y < self.board_size[1] and self.board[x][y] == 0:
                neighbours.append((x, y))
        return neighbours

d1=int(input())
d2=int(input())
x=int(input())
y=int(input())
a = KnightTour((d1,d2))
```
## Output:

![image](https://github.com/user-attachments/assets/9fb46aee-8184-42ce-aa15-bba31d171125)


## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
