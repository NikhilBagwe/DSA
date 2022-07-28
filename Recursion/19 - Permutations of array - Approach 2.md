## Permutations of array - Approach 2 :

- Swap every index with itself as well as with remaining indexes on its right.

```cpp
class Solution {
public:
    void findPermutations(int ind, vector<int> &nums, vector<vector<int>> &ans){
        // When pointer becomes equal to size of array, means we have taken decision for every index. Thus nums contain a permutation
        if(ind == nums.size()){
            ans.push_back(nums);
            return;
        }
        
        // Call recursion calls for elements from (ind to n-1)
        for(int i = ind; i < nums.size(); i++){
            swap(nums[i], nums[ind]);
            findPermutations(ind+1, nums, ans);
            swap(nums[i], nums[ind]);
        }
    }
    
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> ds;
        
        findPermutations(0, nums, ans);
        
        return ans;
    }
};
```
