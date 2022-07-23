## Method 1 :

- Passing 2 pointers keeping track of elements to be swapped.
- Array is passed as reference.
```cpp
#include <bits/stdc++.h>
using namespace std;

void reverseArr(int l, int r, int arr[]){
    if(l >= r) return;
    
    swap(arr[l], arr[r]);
    reverseArr(l+1, r-1, arr);
}

int main()
{
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    
    cout<<"Before reversing : ";
    for(int i=0; i<n; i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
    
    reverseArr(0, n-1, arr);
    
    cout<<"After reversing : ";
    for(int i=0; i<n; i++){
        cout<<arr[i]<<" ";
    }
    return 0;
}
```

## Method 2 : Functional

- Instead of passing two pointers, here we just pass 'i' and 2 constant parameters i.e 'arr' and size of array 'n'.
- We use the formula 'n-i-1' to calulate the other element which is to be swapped.

```cpp
void reverseArr(int i, int arr[], int n){
    if(i >= n/2) return;
    
    swap(arr[i], arr[n-i-1]);
    reverseArr(i+1, arr, n);
}

int main()
{
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    
    reverseArr(0, arr, n);
    
    cout<<"After reversing : ";
    for(int i=0; i<n; i++) cout<<arr[i]<<" ";
    
    return 0;
}
```
