## Count Ways To Reach The N-th Stairs - Similar to Fibonacci Series
## Recursion : Count Pattern

```cpp
class Solution {
public:
    int func(int n){
        if(n <= 1) return 1;
        
        // Do all possible stuffs on the index i.e we can jump either '1' or '2' so subtract them accordingly.
        int l = func(n-1);
        int r = func(n-2);
        
        // We are counting all the ways, hence sum up all answers
        return l + r;
    }
    
    int climbStairs(int n) {
        int ans = func(n);
        return ans;
    }
};
```

## Memoization :

```cpp
class Solution {
public:
    int func(int n, vector<int> &dp){
        if(n <= 1) return 1;
        
        if(dp[n] != -1) return dp[n];
        
        return dp[n] = func(n-1, dp) + func(n-2, dp);
    }
    
    int climbStairs(int n) {
        vector<int> dp(n+1, -1);
        int ans = func(n, dp);
        
        return ans;
    }
};
```

## Tabulation :

```cpp
class Solution {
public:
    
    int climbStairs(int n) {
        vector<int> dp(n+1, -1);
        
        dp[0] = 1;
        dp[1] = 1;
        
        for(int i = 2; i <= n; i++){
            dp[i] = dp[i-1] + dp[i-2];
        } 
        
        return dp[n];
    }
};
```

## Space optimization : Similar to Fibonacci
