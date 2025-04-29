# EX 4A DYNAMIC PROGRAMMING - 1
## DATE:
## AIM:
To find longest common subsequence using Dynamic Programming.


## Algorithm

1. **Input Strings**: Read two strings `u` and `v`.
2. **Initialize Table**: Create a 2D table `c` of size `(len(u)+1) x (len(v)+1)` and fill it with `-1`.
3. **Set Base Cases**: Set all values in the last row and column of `c` to `0` (LCS with an empty string is 0).
4. **Fill Table (Bottom-Up)**: Iterate from the end of the strings to the start.
5. **Check Match**: If characters `u[i] == v[j]`, set `c[i][j] = 1 + c[i+1][j+1]`.
6. **Check Mismatch**: If not equal, set `c[i][j] = max(c[i+1][j], c[i][j+1])`.
7. **Return Table**: After filling, return the table `c` containing LCS lengths.
8. **Initialize Pointers**: Set `i = 0` and `j = 0` to begin reconstruction.
9. **Trace LCS**: If `u[i] == v[j]`, print the character and move both pointers.
10. **Navigate Table**: If not equal, move in the direction of the larger LCS value in table `c`.

## Program:
```python
Program to implement the longest common subsequence using Dynamic Programming

Developed by: Yuvabharathi B
Register Number: 212222230181
def lcs(u, v):
    """Return c where c[i][j] contains length of LCS of u[i:] and v[j:]."""
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
 
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v) - 1, -1, -1):
            if u[i] == v[j]:
                c[i][j] = 1 + c[i + 1][j + 1]
            else:
                c[i][j] = max(c[i + 1][j], c[i][j + 1])
    return c
 
def print_lcs(u, v, c):
    """Print one LCS of u and v using table c."""
    i = j = 0
    while not (i == len(u) or j == len(v)):
        if u[i] == v[j]:
            print(u[i], end='')
            i += 1
            j += 1
        elif c[i][j + 1] > c[i + 1][j]:
            j += 1
        else:
            i += 1
 
u = input()
v = input()
c = lcs(u, v)
print_lcs(u, v, c)
```

## Output:
![image](https://github.com/user-attachments/assets/28b869f8-d4b9-4063-9e76-1c74931e84f0)



## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
