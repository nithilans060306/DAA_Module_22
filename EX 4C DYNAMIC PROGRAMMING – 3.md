# EX 4C DYNAMIC PROGRAMMING – 3
## DATE: 03/05/2025
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.

## Algorithm

1. Reverse the original string and store it as a second string to compare with the original.
2. Create a 2D DP table of size (n+1) x (n+1) initialized with -1 to store intermediate LCS results.
3. Define a recursive function `lps()` with memoization that returns 0 if either string is empty.
4. If characters match at the current indices, add 1 to the result and recurse on the remaining substrings.
5. If characters do not match, take the maximum value between excluding the current character from either string, and store the result in the DP table.

## Program:
```
/*
Program to implement to find the length of the longest palindromic subsequence in it

.
Developed by: Nithilan S
Register Number: 212223240108
*/
def lps(str1, str2, m, n, dp):
    if m == 0 or n == 0:
        return 0
    
    if dp[m][n] != -1:
        return dp[m][n]
        
    if str1[m-1] == str2[n-1]:
        dp[m][n] = 1 + lps(str1, str2, m-1, n-1, dp)
        
    else:
        dp[m][n] = max(lps(str1, str2, m-1, n, dp), lps(str1, str2, m, n-1, dp))
        
    return dp[m][n]
    
str1 = input()
revStr = str1[::-1]
n = len(str1)
dp = [[-1 for _ in range(n+1)] for _ in range(n+1)]
print("The length of the LPS is", lps(str1, revStr, n, n, dp))
```

## Output:
![image](https://github.com/user-attachments/assets/b457c367-605b-406e-9d13-ca42bed50c18)

## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
