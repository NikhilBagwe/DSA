## Functional method : TC = O(n/2) - since only half of the recurssive calls are made

```cpp
bool checkPalindrome(int i, string &s){
    // (i > n/2) -> At this point we have already reached the middle of string, hence return true.
    if(i >= s.size() / 2) return true;  
  
    // Use formula 'size-i-1' and check for equal elements.
    if(s[i] != s[s.size()-i-1]) return false;
    
    return checkPalindrome(i+1, s);
}

int main()
{
    string word = "MADAM";
    
    cout<<checkPalindrome(0, word);
    
    return 0;
}
```
