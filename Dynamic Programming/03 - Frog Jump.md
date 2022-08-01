## Recursion :

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
