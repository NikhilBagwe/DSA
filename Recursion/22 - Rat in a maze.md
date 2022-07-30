## Rat in a maze :

- Maintain a visited array to track which cells are visited.
- For every cell check whether rat can move in four directions - Down, Left, Right, Up - In lexiographical order.

```cpp
class Solution{
    public:
    void solve(int i, int j, vector<vector<int>> &a, int n, vector<string> &ans, string move,
    vector<vector<int>> &vis){
        // When we reach destination
        if(i == n-1 && j == n-1){
            ans.push_back(move);
            return;
        }
        
        // downward -> (i+1, j)
        /* Check for :
        1. If 'i' is not going outside of maze
        2. the cell is not been previously visited
        3. The cell is marked by '1'
        */
        if(i+1<n && !vis[i+1][j] && a[i+1][j]==1){
            // Mark the current cell as visited
            vis[i][j] = 1;
            solve(i+1, j, a, n, ans, move+'D', vis);
            vis[i][j] = 0;
        }
        
        // Left -> (i, j-1)
        if(j-1>=0 && !vis[i][j-1] && a[i][j-1]==1){
            vis[i][j] = 1;
            solve(i, j-1, a, n, ans, move+'L', vis);
            vis[i][j] = 0;
        }
        
        // Right -> (i, j+1)
        if(j+1<n && !vis[i][j+1] && a[i][j+1]==1){
            vis[i][j] = 1;
            solve(i, j+1, a, n, ans, move+'R', vis);
            vis[i][j] = 0;
        }
        
        // Upward -> (i-1, j)
        if(i-1>=0 && !vis[i-1][j] && a[i-1][j]==1){
            vis[i][j] = 1;
            solve(i-1, j, a, n, ans, move+'U', vis);
            vis[i][j] = 0;
        }
    }
    
    vector<string> findPath(vector<vector<int>> &m, int n) {
        vector<string> ans;
        vector<vector<int>> vis(n, vector<int> (n, 0));
        
        // Check if first and last cell are marked '0'. If marked '0', a path can never be formedd
        if(m[0][0]==0 || m[n-1][n-1]==0){
            ans.push_back("-1");
            return ans;
        }
        
        solve(0, 0, m, n, ans, "", vis);
        return ans;
    }
};
```

## Optimized Clean code :

- Here instead of 4 'if' statements we use for loop and direction arrays.

```cpp
class Solution{
    public:
    void solve(int i, int j, vector<vector<int>> &a, int n, vector<string> &ans, string move,
    vector<vector<int>> &vis, int di[], int dj[]){
        if(i == n-1 && j == n-1){
            ans.push_back(move);
            return;
        }
        
        string dir = "DLRU";
        
        for(int ind = 0; ind < 4; ind++){
            int nexti = i + di[ind];
            int nextj = j + dj[ind];
            
            // Do all boundary checks
            if(nexti >= 0 && nextj >= 0 && nexti < n && nextj < n && !vis[nexti][nextj] && a[nexti][nextj]){
                vis[i][j] = 1;
                solve(nexti, nextj, a, n, ans, move + dir[ind], vis, di, dj);
                vis[i][j] = 0;
            }
        }
    }
    
    vector<string> findPath(vector<vector<int>> &m, int n) {
        vector<string> ans;
        vector<vector<int>> vis(n, vector<int> (n, 0));
        
        if(m[0][0]==0 || m[n-1][n-1]==0){
            ans.push_back("-1");
            return ans;
        }
        
        int di[] = {1, 0, 0, -1};
        int dj[] = {0, -1, 1, 0};
        
        solve(0, 0, m, n, ans, "", vis, di, dj);
        return ans;
    }
};
```
