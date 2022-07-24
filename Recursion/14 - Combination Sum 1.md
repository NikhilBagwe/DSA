## Combination Sum 1 : Pick number unlimited times

```cpp
class Solution {
public:
    void findCombination(int i, int target, vector<int> &ds, vector<int> &arr, vector<vector<int>> &ans){
        // Check if you have reached the nth index
        if(i == arr.size()){
            // Target became 0
            if(target == 0){
                ans.push_back(ds);
            }
            return;
        }
        
        // Pick - Stay at the same index
        // Make Pick call only when 'element at current index' is <= 'target'. If element is greater, move to next index
        if(arr[i] <= target){
            ds.push_back(arr[i]);
            findCombination(i, target-arr[i], ds, arr, ans);
            ds.pop_back();
        }
        
        // Not Pick - Move to next index
        findCombination(i+1, target, ds, arr, ans);
    }
        
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> ans;
        vector<int> ds;
        
        findCombination(0, target, ds, candidates, ans);
        return ans;
    }
};
```
