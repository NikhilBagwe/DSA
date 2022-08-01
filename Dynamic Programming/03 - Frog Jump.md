## Recursion :

- Here we find all the ways the frog can reach the nth staircase and then return the way in which the frog's least energy is consumed.
- Frog can jump either 1 or 2 stairs at a time.
- So we will check for both jumps and return the minimum energy required path.

```cpp
#include <bits/stdc++.h>

int func(int i, vector<int> &heights){
    // If you are standing on 0th stair, the energy required to go from 0 to 0 stair is 0
    if(i == 0) return 0;
    
    int jumpOne = func(i-1, heights) + abs(heights[i] - heights[i-1]);
    
    int jumpTwo = INT_MAX;
    
    // To avoid going to '-1' stair
    if(i > 1){
        jumpTwo = func(i-2, heights) + abs(heights[i] - heights[i-2]);
    }
    
    return min(jumpOne, jumpTwo);
}

int frogJump(int n, vector<int> &heights)
{
    int ans = func(n-1, heights);
    return ans;
}
```

## Memoization :

- Only 3 changes made in recursion solution to make it memoization.

```cpp
int func(int i, vector<int> &heights, vector<int> &dp){
    if(i == 0) return 0;
    
    if(dp[i] != -1) return dp[i];  // Change 2
    
    int jumpOne = func(i-1, heights, dp) + abs(heights[i] - heights[i-1]);
    
    int jumpTwo = INT_MAX;
    if(i > 1){
        jumpTwo = func(i-2, heights, dp) + abs(heights[i] - heights[i-2]);
    }
    
    return dp[i] = min(jumpOne, jumpTwo);  // Change 3
}

int frogJump(int n, vector<int> &heights)
{
    vector<int> dp(n+1, -1);  // Change 1
    int ans = func(n-1, heights, dp);
    return ans;
}
```
