## Memoization : 
- TC = O(n) -> As only once the recursion goes to the depth of the tree which of size 'n' and due to memoiztion rest are constant calls.
- SC = O(n) + O(n) = Recursion Stack space + DP array

```cpp
int fibo(int n, vector<int> &dp){
    if(n <= 1) return n;
    
    if(dp[n] != -1) return dp[n];  // Step 3
    
    return dp[n] = fibo(n-1, dp) + fibo(n-2, dp);  // Step 2
}

int main()
{
    int n ;
    cin>>n;
    vector<int> dp(n+1, -1);  // Step 1
    
    cout<<fibo(n, dp);

    return 0;
}
```

## Tabulation : Eliminates Recursion 

- TC = O(n)
- SC = O(n) -> Recursion stack space is eliminated, only DP array space is considered

```cpp
int main()
{
    int n;
    cin>>n;
    vector<int> dp(n+1, -1);  // Step 1
    
    dp[0] = 0;  // Step 2
    dp[1] = 1;
    
    for(int i = 2; i <= n; i++){  // Step 3
        dp[i] = dp[i-1] + dp[i-2];
    }
    
    cout<<dp[n];

    return 0;
}
```

## Space Optimization : Eliminate DP array

- TC = O(n)
- SC = O(1)
- Here we simply use 2 variables 'prev' and 'prev2' to keep track of previous two numbers and accordingly calculate the current number.

```cpp
int main()
{
    int n;
    cin>>n;
    
    int prev2 = 0;
    int prev = 1;
    
    for(int i = 2; i <= n; i++){  
        int cur = prev + prev2;
        // For the next iteration, the 'cur' will become the new 'prev' & 'prev' will become 'prev2'
        prev2 = prev;
        prev = cur;
    }
    
    cout<<prev;

    return 0;
}
```
