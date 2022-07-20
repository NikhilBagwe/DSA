## Power of a number :

- ans = x * power(x, n-1)

```cpp
#include <bits/stdc++.h>
using namespace std;

int power(int x, int n){
    if(n == 1) return x;

    int partialAns = power(x, n-1);
    
    return x * partialAns;
}

int main()
{
    int x=5, n=3;
    
    cout<<power(x, n);

    return 0;
}
```
