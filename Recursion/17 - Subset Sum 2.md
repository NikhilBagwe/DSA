[Question link](https://leetcode.com/problems/subsets-ii/)

# Subset Sum 2 :

## Brute force :

- Similar to printing all subsequences.
- Just store all subsequences into a Set so we get only unique subsequences.
- At the end put them back into 'ans' vector.
- Don't pass 'ds' as a reference.

```cpp
class Solution {
public:
    void findSubsets(int i, vector<int> ds, set<vector<int>> &res, vector<int> &nums){
        if(i == nums.size()){
            sort(ds.begin(), ds.end());
            res.insert(ds);
            return;
        }
        
        ds.push_back(nums[i]);
        findSubsets(i+1, ds, res, nums);
        ds.pop_back();
        
        findSubsets(i+1, ds, res, nums);
    }
    
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> ans;
        set<vector<int>> res;
        vector<int> ds;
        
        findSubsets(0, ds, res, nums);
        
        for(auto it = res.begin(); it != res.end(); it++){
            ans.push_back(*it);
        }
        
        return ans;
    }
};
```
