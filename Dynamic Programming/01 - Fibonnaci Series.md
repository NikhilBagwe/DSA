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
