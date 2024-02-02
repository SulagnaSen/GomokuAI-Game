# GomokuAI-Game
This AI in Gomoku uses minimax with alpha-beta pruning for strategic decisions, maximizing winning chances while hindering the opponent. It evaluates states using winning patterns and positions, employing correlation matrices and utility functions for potential patterns, and mathematically optimizing the algorithm for recursive exploration

IMPLEMENTATION
The Submission class is initialized with parameters such as board_size, win_size, and an optional parameter max_depth for the minimax algorithm. The main entry point for the agent is the __call__ method. It calls the minimax function to determine the best move for the current state. The minimax method explores potential moves recursively, considering the current player's and opponent's turns. Alpha-beta pruning is employed to optimize the search and avoid unnecessary exploration of branches.The evaluate_best_move method scrutinizes the current state to identify the agent's best move. It prioritizes creating winning patterns and blocking opponent victories based on the correlation matrix—a representation of potential winning configurations on the game board. The evaluation function incorporates the following strategies:
1.
Correlation Matrix Analysis: The code examines the correlation matrix to identify winning patterns where the agent can win on its next move and block opponent wins. The correlation matrix (state.corr) captures potential winning configurations. Let's denote the correlation matrix as C of size N×M, where N is the board's height and M is its width. Each cell in this matrix represents the correlation of each position with the potential winning patterns for both players.
For each player (P1 (max-player) and P2 (min-player)):
•
Cij,P1 represents the correlation of position (i,j) with potential winning patterns for P1.
•
Cij,P2 represents the correlation of position (i,j) with potential winning patterns for P2.
2.
Utility Functions used for Decision-Making:
2.1
minimal_path_to_game_over_state: Calculates the minimal path to a game-over state by considering the remaining empty cells, the opponent's potential wins, and the current turn.
2.2
evaluate_best_move: We query the correlation matrix to identify potential winning moves for both players.
•
P1 requires just one more move to win: Cij,P1 = state.win_size − 1
•
P2 requires just one more move to win: Cij,P2 = state.win_size – 1
•
Find (i,j) that disrupt the opponent players’ winning sequence:j = argmaxj (state.boardempty,row,j) and i = argmaxi (state.boardempty,row,i)
•
Calculate best move for agent based on strategic considerations: best_move = player_sign *  action
2.3
find_best_empty_board_cells: Identifies optimal empty cells on the board using winning patterns (0 for upward, 1 for downward, 2 for diagonal, and 3 for anti-diagonal). The code determines row and column positions by finding the maximum values in specific slices of the game board. Introducing randomness through move order scrambling enhances the agent's decision-making adaptability.
PERFORMANCE
This AI showed a mixed performance, achieving a 67% win rate, hence showing a strategic decision-making against Minimax. The scores in some repetitions indicate better strategic moves by our AI as there were negative scores. Our implementation was successfully able to address the balancing of minimax depth and refining move evaluation logic through parameter tuning, optimizing the exploration-exploitation balance for effective decision-making to get desired results.
