## Print all subsequences that add upto the given value :

- eg: arr = {1, 2, 1} , value =2 . Thus subsequences are {1, 1} and {2}.
- Simply carry a sum variable to keep track of the addition of elements stored in ds and check if they are equal to required value i.e in our case '2'.
- Make sure to write 'return' outside of inner if statement or else o/p won't be printed.

```cpp
void printAll(int i, int sum, vector<int> &ds, int arr[], int n, int val)
{
    if(i == n){
        if(val == sum){
            for(auto num : ds) cout<<num<<" ";
            cout<<endl;
        }
        
        return;
    }
    
    // Pick
    ds.push_back(arr[i]);
    sum += arr[i];
    
    printAll(i+1, sum, ds, arr, n, val);
    
    ds.pop_back();
    sum -= arr[i];
    
    // Not Pick
    printAll(i+1, sum, ds, arr, n, val);
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

/*
1 1 
2 
*/
```
