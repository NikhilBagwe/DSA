## Fibonacci series : TC = O(2 ^ n) i.e exponential , SC = O(n)

- n = fibo(n-1) + fibo(n-2)

```cpp
#include <bits/stdc++.h>
using namespace std;

int fibo(int n){
    if(n == 1) return 1;
    if(n == 2) return 1;
    
    int partialAns1 = fibo(n-1);
    int partialAns2 = fibo(n-2);
    
    return partialAns1 + partialAns2;
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    cout<<fibo(n);

    return 0;
}
```

## Concise code :

```cpp
int fibo(int n){
    // If n is '1 or 0' , just return n.
    if(n <= 1) return n;
    
    return fibo(n-1) + fibo(n-2);
}

int main()
{
    int n = 4;
    cout<<fibo(n);

    return 0;
}
```
