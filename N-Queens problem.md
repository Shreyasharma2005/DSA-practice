import java.util.\*;



class Solution {

&#x20;   public void solve(int col, char\[]\[] board, int n, int\[] leftRow, int\[] upperDiagonal, int\[] lowerDiagonal, List<List<String>> res) {

&#x20;       if (col == n) {

&#x20;           List<String> temp = new ArrayList<>();

&#x20;           for (int i = 0; i < n; i++) {

&#x20;               temp.add(new String(board\[i]));

&#x20;           }

&#x20;           res.add(temp);

&#x20;           return;

&#x20;       }



&#x20;       for (int row = 0; row < n; row++) {

&#x20;           if (leftRow\[row] == 0 \&\& lowerDiagonal\[row + col] == 0 \&\& upperDiagonal\[n - 1 + col - row] == 0) {



&#x20;               board\[row]\[col] = 'Q';

&#x20;               leftRow\[row] = 1;

&#x20;               lowerDiagonal\[row + col] = 1;

&#x20;               upperDiagonal\[n - 1 + col - row] = 1;



&#x20;               solve(col + 1, board, n, leftRow, upperDiagonal, lowerDiagonal, res);



&#x20;               // backtrack

&#x20;               board\[row]\[col] = '.';

&#x20;               leftRow\[row] = 0;

&#x20;               lowerDiagonal\[row + col] = 0;

&#x20;               upperDiagonal\[n - 1 + col - row] = 0;

&#x20;           }

&#x20;       }

&#x20;   }



&#x20;   public List<List<String>> solveNQueens(int n) {

&#x20;       List<List<String>> res = new ArrayList<>();

&#x20;       char\[]\[] board = new char\[n]\[n];



&#x20;       for (char\[] row : board) {

&#x20;           Arrays.fill(row, '.');

&#x20;       }



&#x20;       int\[] leftRow = new int\[n];

&#x20;       int\[] lowerDiagonal = new int\[2 \* n - 1];

&#x20;       int\[] upperDiagonal = new int\[2 \* n - 1];



&#x20;       solve(0, board, n, leftRow, upperDiagonal, lowerDiagonal, res);

&#x20;       return res;

&#x20;   }

}

