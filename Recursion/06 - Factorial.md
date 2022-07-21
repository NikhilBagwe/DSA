## Parametrized way :

```cpp
void factorial(int n, int sum){
    if(n < 1){
        cout<<sum;
        return;
    }
    
    factorial(n-1, sum*n);
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    factorial(n, 1);

    return 0;
}
```

## Functional way :

```cpp
int factorial(int n){
    if(n == 0) return 1;
    
    return n * factorial(n-1);
}

int main()
{
    int n;
    cout<<"Enter number : ";
    cin>>n;
    
    cout<<factorial(n);

    return 0;
}
```
