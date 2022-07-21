## Power of a number : TC = O(n) , SC = O(n)

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

## Optimized soln : TC = O(logn) , SC = O(logn)

- For higher values of n, the below soln will prove to be useful as it reduces the no. of calculations significantly.
- For ODD number : eg. we have to find for 3^7. Thus, in first call it will be 7/2=3, then 3/2=1, then 1/2=0. So we will be calculating upto 3^6 here. Thus we once again multiply the ans by 'x'.
```cpp
#include <bits/stdc++.h>
using namespace std;

long long power(int x, int n){
    if(n == 0) return 1;
    
    long long temp = power(x, n/2);
    
    // For odd no. we have to multiply the ans again by 'x' once
    if(n%2 == 1) return temp*temp*x;
    // For even no.
    return temp*temp;
}

int main()
{
    int x, n;
    cout<<"Enter number : ";
    cin>>x;
    cout<<"Enter power : ";
    cin>>n;
    
    cout<<"Answer : "<<power(x,n);

    return 0;
}
```
