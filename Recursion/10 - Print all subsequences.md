## Print all subsequences : 

### TC = O((2 ^ n) * n)  -> (2 ^ n) - for Recursion and 'n' - for printing the subsequences. It is approx as we are not printing all 'n' elements.
### SC = O(n) -> MAximum depth of recursion tree. At max there are n=3 i.e 3 recursion calls waiting in internal stack.

```cpp
void printSubseq(int ind, int n, vector<int> &ds, int arr[]){
    if(ind >= n){
        for(auto num : ds) cout<<num<<" ";
        
        if(ds.size() == 0) cout<<"{}";  // Printing empty subsequence
        
        cout<<endl;
        return;
    }
    
    // Take
    ds.push_back(arr[ind]);
    printSubseq(ind+1, n, ds, arr);
    
    // Not Take
    ds.pop_back();
    printSubseq(ind+1, n, ds, arr);
}

int main()
{
    int arr[] = {3, 1, 2};
    int n = 3;
    vector<int> ds;
    
    printSubseq(0, n, ds, arr);

    return 0;
}

/*
3 1 2 
3 1 
3 2 
3 
1 2 
1 
2 
{}
*/
```
