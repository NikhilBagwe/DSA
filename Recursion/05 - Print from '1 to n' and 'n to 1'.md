## Print from '1 to n' :

```cpp
void printNum(int i, int n){
    // Eg: n=5 and 'i' becomes 6 i.e (6>5) and thus the program terminates.
    if(i > n) return;
    
    cout<<i<<endl;
    
    printNum(i+1, n);
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    printNum(1, n);

    cout<<"Program Ends";
    return 0;
}

/*
Output :

Enter number : 5
1
2
3
4
5
Program Ends

*/
```

## Print from 'n to 1' :

```cpp
void printNum(int n){
    if(n == 0) return;
    
    cout<<n<<endl;
    
    printNum(n-1);
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    printNum(n);

    cout<<"Program Ends";
    return 0;
}

/*
Output :

Enter number : 5
5
4
3
2
1
Program Ends

*/
```
