## Recursion :

- When a function calls itself, until a certain condition is met is called recursion.
- If no base condition is mentioned, the function will keep calling itself until the system runs out of memory throwing StackOverflow error (Segmentation fault).

## Functional way :

- Here the function returns us the final ans.
- Eg : In Sum of n natural no. we use the logic where n + f(n-1). If n=5, the we ask recursion to find f(4) for us and we simply add it to our 'n' which is 5.

## Parameterized way :

- Here we pass extra parameters to keep track of our final answer.
