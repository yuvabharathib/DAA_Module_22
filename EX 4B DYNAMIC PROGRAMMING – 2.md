# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..


## Algorithm

1. **Input Strings**: Read two strings `X` and `Y`.
2. **Find Lengths**: Store lengths of `X` as `m` and `Y` as `n`.
3. **Initialize Table**: Create a 2D list `lookup` of size `(m+1) x (n+1)` initialized with `0`.
4. **Initialize Variables**: Set `maxLength = 0` and `endingIndex = m`.
5. **Loop Over Strings**: Use nested loops from `i = 1 to m` and `j = 1 to n`.
6. **Character Match**: If `X[i-1] == Y[j-1]`, set `lookup[i][j] = lookup[i-1][j-1] + 1`.
7. **Update Maximum**: If `lookup[i][j] > maxLength`, update `maxLength` and `endingIndex`.
8. **Continue Loop**: If characters don’t match, do nothing (leave `lookup[i][j] = 0`).
9. **Find Substring**: After loops, extract substring from `X[endingIndex - maxLength : endingIndex]`.
10. **Print Result**: Display the longest common substring. 

## Program:
```python
Program to implement the longest common substring problem
Developed by: Yuvabharathi B
Register Number:  212222230181
def LCS(X, Y, m, n):
    maxLength = 0
    endingIndex = m
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
    return X[endingIndex - maxLength: endingIndex]

X = input()
Y = input()
m = len(X)
n = len(Y)
print('The longest common substring is', LCS(X, Y, m, n))
```

## Output:
![image](https://github.com/user-attachments/assets/098cf014-b638-41ed-9488-eacf2cf785a6)


## Result:
Thus the program was executed successfully for finding the longest common substring .
