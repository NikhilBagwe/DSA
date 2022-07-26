- Each number can only be used once in an combination.

## BRUTE : Returns duplicate combinations which are not required

- Similar to Combination sum 1, just instead of staying at the same index in Pick case, we move to next element as we have to use every number only once.
- TC = 2^n * k + nlogn(sorting)
```cpp
class Solution {
public:
    void findCombination(int i, int target, vector<int> &ds, vector<int> &arr, vector<vector<int>> &ans){
        if(i == arr.size()){
            if(target == 0){
                ans.push_back(ds);
            }
            return;
        }
        
        // Pick
        if(arr[i] <= target){
            ds.push_back(arr[i]);
            findCombination(i+1, target-arr[i], ds, arr, ans);
            ds.pop_back();
        }
        
        // Not Pick
        findCombination(i+1, target, ds, arr, ans);
    }
    
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<int> ds;
        vector<vector<int>> ans;
        
        sort(candidates.begin(), candidates.end());
        
        findCombination(0, target, ds, candidates, ans);
        
        return ans;
    }
};

/*
[
[1,1,6],
[1,2,5],
[1,7],
[1,2,5],
[1,7],
[2,6]
]
*/
```

## BETTER :

- The idea is that we can start forming combinations from any index.
- Here for every index, we check whether we can call recursion on the remaining indexes by running a for loop.

```cpp
class Solution {
public:
    void findCombination(int ind, int target, vector<int> &arr, vector<vector<int>> &ans, vector<int> &ds){
        // Here we are not checking whether we reached nth index, as we are might get the desired combination at any index.
        if(target == 0){
            ans.push_back(ds);
            return;
        }
        
        for(int i = ind; i < arr.size(); i++){
            // Checks if current element is same as previous element
            if(i > ind && arr[i] == arr[i-1]) continue;
            
            // As the array is sorted, we are not going to get samller element on the right side even if we continue
            if(arr[i] > target) break;
            
            ds.push_back(arr[i]);
            findCombination(i+1 , target-arr[i], arr, ans, ds);
            ds.pop_back();
        }
    }
    
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<int> ds;
        vector<vector<int>> ans;
        
        // We need the combinations in sorted order
        sort(candidates.begin(), candidates.end());
        
        findCombination(0, target, candidates, ans, ds);
        
        return ans;
    }
};
```
