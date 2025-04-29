# EX 4D DYNAMIC PROGRAMMING – 4
## DATE:
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.





## Algorithm

1. **Input String**: Read the string `s`.
2. **Initialize Table**: Create a 2D table `dp` of size `len(s) x len(s)`, all set to `False`.
3. **Single Letters**: Mark all `dp[i][i] = True` (every single character is a palindrome).
4. **Initialize Variables**: Set `max_length = 1` and `start = 0` to track the longest palindrome.
5. **Loop Over Lengths**: For all substring lengths `l` from 2 to `len(s)`:
6. **Loop Over Start Index**: For each starting index `i`, calculate `end = i + l`.
7. **Two-Character Case**: If length `l == 2` and `s[i] == s[end-1]`, mark `dp[i][end-1] = True`, update `start` and `max_length`.
8. **More Than Two Characters**: If `s[i] == s[end-1]` and `dp[i+1][end-2]` is `True`, mark `dp[i][end-1] = True`, update `start` and `max_length`.
9. **Continue Checking**: Repeat the above steps for all possible lengths and positions.
10. **Return Result**: Return the substring from `start` to `start + max_length`.

## Program:
```python
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method
Developed by: Yuvabharathi B
Register Number:  212222230181
class Solution(object):
    def longestPalindrome(self, s):
    ###########  Add your code here #############
        dp = [[False for i in range(len(s))] for i in range(len(s))]
        for i in range(len(s)):
            dp[i][i] = True
        max_length = 1
        start = 0
        for l in range(2,len(s)+1):
             for i in range(len(s)-l+1):
                end = i+l
                if l==2:
                    if s[i] == s[end-1]:
                        dp[i][end-1]=True
                        max_length = l
                        start = i
                else:
                    if s[i] == s[end-1] and dp[i+1][end-2]:
                        dp[i][end-1]=True
                        max_length = l
                        start = i
        return s[start:start+max_length]

ob1 = Solution()
str1=input()
print(ob1.longestPalindrome(str1))
```

## Output:
![image](https://github.com/user-attachments/assets/ca53d9a9-423d-433c-ac71-e8598e907c09)


## Result:
Thus the program was executed successfully for finding edit distance between two strings.
