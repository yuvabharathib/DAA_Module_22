# EX 4C DYNAMIC PROGRAMMING – 3
## DATE:
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.





## Algorithm

1. **Input String**: Read string `seq`.
2. **Find Length**: Get length `n` of the string.
3. **Reverse String**: Create `s2` as the reverse of `seq`.
4. **Initialize DP Table**: Create 2D list `dp[1001][1001]`, filled with `-1`.
5. **Define Function `lps(s1, s2, n1, n2)`**:
6. **Base Case**: If either string is empty (`n1 == 0` or `n2 == 0`), return 0.
7. **Memoization Check**: If `dp[n1][n2]` already computed, return it.
8. **Character Match**: If `s1[n1-1] == s2[n2-1]`, set `dp[n1][n2] = 1 + lps(...)`.
9. **Character Mismatch**: Else, take max of skipping a character from either string.
10. **Print Result**: Call `lps()` with original and reversed string to get LPS length.  

## Program:
```Python
Program to implement to find the length of the longest palindromic subsequence in it
Developed by: Yuvabharathi B
Register Number:  212222230181
dp = [[-1 for i in range(1001)]for j in range(1001)]
def lps(s1, s2, n1, n2):
    if (n1 == 0 or n2 == 0):
        return 0
    if (dp[n1][n2] != -1):
        return dp[n1][n2]
    if (s1[n1 - 1] == s2[n2 - 1]):
        dp[n1][n2] = 1 + lps(s1, s2, n1 - 1, n2 - 1)
        return dp[n1][n2]
    else:
        dp[n1][n2] = max(lps(s1, s2, n1 - 1, n2), lps(s1, s2, n1, n2 - 1))
        return dp[n1][n2]
seq = input()
n = len(seq)
s2 = seq
s2 = s2[::-1]
print(f"The length of the LPS is",lps(s2, seq, n, n))
```

## Output:
![image](https://github.com/user-attachments/assets/18efa1a4-30a1-4c68-9408-eacc351c8da1)


## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
