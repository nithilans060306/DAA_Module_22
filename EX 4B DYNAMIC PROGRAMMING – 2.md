# EX 4B DYNAMIC PROGRAMMING – 2
## DATE: 03/05/2025
## AIM: 
To find the longest string (or strings) that is a substring (or are substrings) of two strings..

## Algorithm

1. Initialize a 2D DP table of size (m+1) x (n+1) with all values set to 0, where `m` and `n` are lengths of input strings `u` and `v`.
2. Iterate over each character of both strings; if characters match, update `dp[i][j] = dp[i-1][j-1] + 1`.
3. Track the maximum value in the DP table and store the ending index of the substring in the first string.
4. If characters do not match, set `dp[i][j] = 0` to reset the substring count.
5. After filling the table, extract and return the substring from `u` using the recorded end index and maximum length.


## Program:
```python
/*
Program to implement the longest common substring problem

.
Developed by: Nithilan S
Register Number: 212223240108
*/
def lcs(u, v):
    m, n = len(u), len(v)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    maxL = 0
    endI = 0

    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if u[i - 1] == v[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
                if dp[i][j] > maxL:
                    maxL = dp[i][j]
                    endI = i
            else:
                dp[i][j] = 0

    return u[endI - maxL:endI]

u = input()
v = input()

result = lcs(u, v)
print("The longest common substring is", result)

```

## Output:



## Result:
Thus the program was executed successfully for finding the longest common substring .
