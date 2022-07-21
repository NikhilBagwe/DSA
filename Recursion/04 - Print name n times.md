## Print name n times :

```cpp
void printName(string name, int n){
    if(n == 0) return;
    
    cout<<name<<endl;
    
    printName(name, n-1);
}

int main()
{
    int n = 5;
    string name = "Nikhil";
    
    printName(name, n);  // Recursive call

    cout<<"Program Ends";
    return 0;
}
```
