## Permutations of array - Approach 1 :

### TC = O(n! * n) = Recursion * for loop
### SC = O(n) + O(n) = ds + freq array

```cpp
class Solution {
public:
    void findPermutations(vector<int> &ds, int freq[], vector<int> &nums, vector<vector<int>> &ans){
        // When size of 'ds' and 'nums' become equal, means we gernerated a permutation
        if(ds.size() == nums.size()){
            ans.push_back(ds);
            return;
        }
        
        // Check which index element can be picked by comparing with freq. array
        for(int i = 0; i < nums.size(); i++){
            // If index is not picked
            if(!freq[i]){
                // Pick
                freq[i] = 1;
                ds.push_back(nums[i]);
                findPermutations(ds, freq, nums, ans);
                
                // After coming back from recursion, remove the element from 'ds' for further recurssive calls.
                freq[i] = 0;
                ds.pop_back();
            }
        }
    }
    
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> ds;
        
        int freq[nums.size()];
        for(int i = 0; i < nums.size(); i++) freq[i] = 0;
        
        findPermutations(ds, freq, nums, ans);
        
        return ans;
    }
};
```
