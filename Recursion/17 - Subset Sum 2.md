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

## BETTER : 
## TC = (2^n) * n = Recursion * Time taken to put ds into ans
## SC = O(2^n * k) = to store every subset of average length k. Auxiliary space is O(n)  if n is the depth of the recursion tree.

- Similar to Combination sum 2.
- (i > ind) => Due to this condition check, only the first element gets picked, then rest of its duplicates are avoided.
- eg: arr = {1 2 2 2 3 4} -> Here only 2 at index 1, will be picked once, and remaining duplicate elements will be skipped.

```cpp
class Solution {
public:
    void findSubsets(int ind, vector<int> ds, vector<vector<int>> &ans, vector<int> &nums){
        ans.push_back(ds);
        
        // This step will generate/print a series of possible list combinations acheived on that recursion level
        for(int i = ind; i < nums.size(); i++){
            // Check to avoid duplicate elements
            if(i > ind && nums[i] == nums[i-1]) continue;
            
            ds.push_back(nums[i]);
            findSubsets(i+1, ds, ans, nums);
            ds.pop_back();
        }
    }
    
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> ds;
        
        // Since we want the duplicates together to avoid them, we sort it.
        sort(nums.begin(), nums.end());
        findSubsets(0, ds, ans, nums);
        
        return ans;
    }
};
```
