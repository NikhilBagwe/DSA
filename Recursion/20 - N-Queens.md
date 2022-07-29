## BRUTE :

- Here we are performing a lot of O(n) operations in isSafe() as well as solve() functions taking lot of time.
```cpp
class Solution {
public:
    bool isSafe(int row, int col, vector<string> board, int n){
        int dupRow = row;
        int dupCol = col;
        
        // Check for Upper left diagonal
        while(row >= 0 && col >= 0){
            if(board[row][col] == 'Q') return false;
            // Keep moving upwards. Thus row and col will decrease
            row--;
            col--;
        }
        
        row = dupRow;
        col = dupCol;
        
        // Check for Left direction
        while(col >= 0){
            if(board[row][col] == 'Q') return false;
            // Since we are moving left, row will remain constant, only col will change
            col--;
        }
        
        col = dupCol;
        // Check for Lower left diagonal 
        while(row < n && col >= 0){
            if(board[row][col] == 'Q') return false;
            // Column is going left & row is increasing
            row++;
            col--;
        }
        
        return true;
    }
    
public:
    void solve(int col, vector<string> &board, vector<vector<string>> &ans, int n){
        // If we reach last column, means we have an answer in 'board'
        if(col == n){
            ans.push_back(board);
            return;
        }
        
        // Check for every row of the column, whether Q can be placed
        for(int row = 0; row < n; row++){
            // If it is safe to place Q in that row, than simply insert Q there & move to next column.
            if(isSafe(row, col, board, n)){
                board[row][col] = 'Q';
                solve(col+1, board, ans, n);
                // Backtrack by removing 'Q'
                board[row][col] = '.';
            }
        }
    }
 public:   
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        vector<string> board(n);
        // Creating an empty string of size 'n' filled with '.' at all places
        string s(n, '.');
        
        // Creating a board of n*n size by inserting string at every index of 'board' vector
        for(int i = 0; i < n; i++) board[i] = s;
        
        solve(0, board, ans, n);
        
        return ans;
    }
};
```

## OPTIMAL : TC = O(n! * n)

- Here instead of checking left row, upper and lower diagonal everytime, we are maintaining a hashmap of them.
- Check this article [TakeuForward](https://takeuforward.org/data-structure/n-queen-problem-return-all-distinct-solutions-to-the-n-queens-puzzle/) for optimized approach explanation.

```cpp
class Solution {
public:
    void solve(int col, vector<string> &board, vector<vector<string>> &ans, vector<int> &leftRow, 
               vector<int> &upperDiagonal, 
               vector<int> &lowerDiagonal, int n)
    {
        if(col == n){
            ans.push_back(board);
            return;
        }
        
        for(int row = 0; row < n; row++){
            // This check makes sure that an Queen was never placed in left row, upper & left diagonal
            if(leftRow[row] == 0 && lowerDiagonal[row + col] == 0 && upperDiagonal[n-1 + col - row] == 0){
                board[row][col] = 'Q';
                // On filling a Queen, mark the hashmaps as '1'
                leftRow[row] = 1;
                lowerDiagonal[row + col] = 1; 
                upperDiagonal[n-1 + col - row] = 1;
                
                solve(col+1, board, ans, leftRow, upperDiagonal, lowerDiagonal, n);
                
                // Backtrack
                board[row][col] = '.';
                leftRow[row] = 0;
                lowerDiagonal[row + col] = 0; 
                upperDiagonal[n-1 + col - row] = 0;
            }
        }
    }
 public:   
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        vector<string> board(n);
        string s(n, '.');
        
        for(int i = 0; i < n; i++) board[i] = s;
        
        vector<int> leftRow(n, 0), upperDiagonal(2*n - 1, 0), lowerDiagonal(2*n - 1, 0);
        solve(0, board, ans, leftRow, upperDiagonal, lowerDiagonal, n);
        
        return ans;
    }
};
```
