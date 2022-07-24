## Count no. of subsequences whose elements add up to given sum :

### TC = O(2 ^ n)

```cpp
int printAll(int i, int sum, int arr[], int n, int val){
    // Optional condition to reduce time complexity
    // if(sum > val) return 0;
    
    if(i == n){
        // Condition satisfied - return 1
        if(val == sum) return 1;
        
        // Condition not satisfied - return 0
        else return 0;
    }
    
    // Pick
    sum += arr[i];
    int l = printAll(i+1, sum, arr, n, val);
    sum -= arr[i];
    
    // Not Pick
    int r = printAll(i+1, sum, arr, n, val);
    
    return l+r;
}

int main()
{
    int arr[] = {1, 2, 1};
    int n = 3;
    int val = 2; // Required sum to be acheive after adding elements of subsequence
    
    cout<<printAll(0, 0, arr, n, val);

    return 0;
}

/*
2
*/
```
