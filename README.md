<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: Viswapriya S      </h3>
<h3>Register Number: 212225230311           </h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance
<hr>
<h2>Sample Input and Output:</h2>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8d5e329a-9aff-41a6-bcf0-46efa10e1b92)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/438b242d-54ba-443e-b040-a936e6ae3b55)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/99a33390-fa11-4ade-a19f-e93bcd7aaec9)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/440797bd-53cb-49c1-b18d-89776864c3e7)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/81575a16-26b2-46f1-a8ac-27c9ed0a0fe5)

## PROGRAM:
```
def print_board(board):
    for i in range(0, 9, 3):
        print(" | ".join(board[i:i+3]))
        if i < 6:
            print("--+---+--")


def check_winner(board):
    wins = [
        (0, 1, 2), (3, 4, 5), (6, 7, 8),
        (0, 3, 6), (1, 4, 7), (2, 5, 8),
        (0, 4, 8), (2, 4, 6)
    ]

    for a, b, c in wins:
        if board[a] == board[b] == board[c] and board[a] != " ":
            return board[a]

    return None


def minimax(board, is_maximizing, alpha, beta):
    winner = check_winner(board)

    if winner == "O":
        return 1
    if winner == "X":
        return -1
    if " " not in board:
        return 0

    if is_maximizing:
        best_score = -float("inf")

        for i in range(9):
            if board[i] == " ":
                board[i] = "O"
                score = minimax(board, False, alpha, beta)
                board[i] = " "

                best_score = max(best_score, score)
                alpha = max(alpha, best_score)

                if beta <= alpha:
                    break

        return best_score

    else:
        best_score = float("inf")

        for i in range(9):
            if board[i] == " ":
                board[i] = "X"
                score = minimax(board, True, alpha, beta)
                board[i] = " "

                best_score = min(best_score, score)
                beta = min(beta, best_score)

                if beta <= alpha:
                    break

        return best_score


def best_move(board):
    best_score = -float("inf")
    move = -1

    for i in range(9):
        if board[i] == " ":
            board[i] = "O"
            score = minimax(
                board, False,
                -float("inf"), float("inf")
            )
            board[i] = " "

            if score > best_score:
                best_score = score
                move = i

    return move


def play_game():
    board = [" "] * 9

    print("TIC-TAC-TOE")
    print("You are X, Computer is O")
    print("Positions are numbered 1 to 9.")

    while True:
        print()
        print_board(board)

        try:
            pos = int(input("Enter your position (1-9): ")) - 1
        except ValueError:
            print("Enter a valid number.")
            continue

        if pos < 0 or pos > 8 or board[pos] != " ":
            print("Invalid move! Try again.")
            continue

        board[pos] = "X"

        if check_winner(board) == "X":
            print_board(board)
            print("You win!")
            break

        if " " not in board:
            print_board(board)
            print("It's a draw!")
            break

        move = best_move(board)
        board[move] = "O"
        print("Computer chooses position:", move + 1)

        if check_winner(board) == "O":
            print_board(board)
            print("Computer wins!")
            break

        if " " not in board:
            print_board(board)
            print("It's a draw!")
            break


play_game()
```

## OUTPUT:

<img width="1530" height="651" alt="WhatsApp Image 2026-10-21 at 9 11 29 AM" src="https://github.com/user-attachments/assets/8a9b1ac3-0110-4244-8024-c7831a715a33" />

<img width="1523" height="697" alt="WhatsApp Image 2026-10-21 at 9 11 40 AM" src="https://github.com/user-attachments/assets/21522b65-b82f-4bef-8281-a898dc779906" />

## RESULT:
We have successfully implemented Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game





