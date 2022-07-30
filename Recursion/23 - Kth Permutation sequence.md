## Kth Permutation sequence :

## BRUTE :

### Using recursion we can find out all possible permutations and then on sorting, return the kth one.

## OPTIMAL :
```cpp
class Solution {
public:
    string getPermutation(int n, int k) {
        int fact = 1;
        vector<int> numbers;
        
        // Creating the required array of size 'n'. Eg: n=4, arr=[1, 2, 3, 4] and calculating factorial
        for(int i = 1; i < n; i++){
            fact = fact * i;
            numbers.push_back(i);
        }
        numbers.push_back(n);
        
        string ans = "";
        k = k-1;    // Since we are using 0 based indexing
        
        while(true){
            // add the number upon calculation
            ans = ans + to_string(numbers[k / fact]);
            // erase the added number from array
            numbers.erase(numbers.begin() + k/fact);
            
            // Keep the loop running until array becomes empty
            if(numbers.size() == 0) break;
            
            // Calculate next value of k and new factorial
            k = k % fact;
            fact = fact / numbers.size();
        }
        
        return ans;
    }
};
```
