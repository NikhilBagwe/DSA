## Subset sum 1 : TC = (2 ^ n) + (2^n) log (2^n) = Recursion + Sorting time

- Similar to printing subsequences problem.

```cpp
void findSubsetSum(int i, int sum, vector<int> &ans, vector<int> &nums){
    if(i == nums.size()){
        ans.push_back(sum);
        return;
    }
    
    // Pick
    findSubsetSum(i+1, sum+nums[i], ans, nums);
    
    // Not Pick
    findSubsetSum(i+1, sum, ans, nums);
}

vector<int> subsetSum(vector<int> &num)
{
    vector<int> ans;
    
    findSubsetSum(0, 0, ans, num);
    sort(ans.begin(), ans.end());
    
    return ans;
}
```
