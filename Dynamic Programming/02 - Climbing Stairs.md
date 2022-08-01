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
