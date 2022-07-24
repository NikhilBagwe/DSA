## Print only one subsequence satisfying the condition :

- Here we have to print only 1 subsequence matching the condition and avoid any further recursion calls.

```cpp
bool printAll(int i, int sum, vector<int> &ds, int arr[], int n, int val){
    if(i == n){
        // Condition satisfied - return true
        if(val == sum){
            for(auto num : ds) cout<<num<<" ";
            cout<<endl;
            return true;
        }
        
        // Condition not satisfied - return false
        else return false;
    }
    
    // Pick
    ds.push_back(arr[i]);
    sum += arr[i];
    
    // If this function call returns a true, means we have the no need to make further recursion call so return true
    // as we got our 1 answer printed.
    if(printAll(i+1, sum, ds, arr, n, val) == true) return true;
    
    ds.pop_back();
    sum -= arr[i];
    
    // Not Pick
    if(printAll(i+1, sum, ds, arr, n, val) == true) return true;
    
    return false;
}

int main()
{
    int arr[] = {1, 2, 1};
    int n = 3;
    int val = 2;
    vector<int> ds;
    
    printAll(0, 0, ds, arr, n, val);

    return 0;
}
```
