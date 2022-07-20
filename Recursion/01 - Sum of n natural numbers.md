## Sum of n natural numbers :

- Logic : ans = n + sum(n-1)
- Eg : If n=5, then if someone gives us the sum of natural no. for n=4 i.e sum(n-1) = sum(5-1) = sum(4) , we can easily caluculate the answer by adding it to 'n' which is '5'

```cpp
#include <bits/stdc++.h>
using namespace std;

int naturalNum(int n){
    if(n == 1) return 1;
    
    int partialAns = naturalNum(n-1);
    
    return n + partialAns;
}

int main()
{
    int n = 6;
    cout<<naturalNum(n);

    return 0;
}
```
