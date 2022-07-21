## Sum of n natural numbers :

- Logic : ans = n + sum(n-1)
- Eg : If n=5, then if someone gives us the sum of natural no. for n=4 i.e sum(n-1) = sum(5-1) = sum(4) , we can easily caluculate the answer by adding it to 'n' which is '5'

## Functional way : Here the function returns the answer

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

## Parameterized way : We pass parameters that keep track of ans

```cpp
void sumOfNaturalNum(int n, int sum){
    if(n < 1){
        cout<<sum;
        return;
    }
    
    sumOfNaturalNum(n-1, sum+n);
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    sumOfNaturalNum(n, 0);

    return 0;
}
```
