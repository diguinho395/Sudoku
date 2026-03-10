# Sudoku
def is_valid_sudoku(board):
    def is_valid_unit(unit):
        unit = [i for i in unit if i != 0]
        return len(unit) == len(set(unit))
    
    # Verifica linhas
    for row in board:
        if not is_valid_unit(row):
            return False
    
    # Verifica colunas
    for col in zip(*board):
        if not is_valid_unit(col):
            return False
    
    # Verifica regiões 3x3
    for i in range(0, 9, 3):
        for j in range(0, 9, 3):
            region = [board[x][y] for x in range(i, i+3) for y in range(j, j+3)]
            if not is_valid_unit(region):
                return False
    
    return True
