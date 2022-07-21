## Backtracking :

- In backtracking, we make sure to execute the print line in last function call first.
- It is done by mentioning the print line after function call.

## Print '1 to n' :

```cpp
void printNumBacktrack(int n){
    if(n < 1) return;
    
    printNumBacktrack(n-1);
    
    cout<<n<<endl;
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    printNumBacktrack(n);

    return 0;
}

/*
Enter number : 5
1
2
3
4
5
*/
```

## Print 'n to 1' :

```cpp
void printNumBacktrack(int n, int num){
    if(n == 0) return;
    
    printNumBacktrack(n-1, num);
    
    cout<<num-n+1<<endl;
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    printNumBacktrack(n, n);

    return 0;
}

/*
Enter number : 5
5
4
3
2
1
*/
```
