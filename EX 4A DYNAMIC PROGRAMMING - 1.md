# EX 4A DYNAMIC PROGRAMMING - 1
## DATE: 03/05/2025
## AIM: To find longest common subsequence using Dynamic Programming.

## Algorithm

1. Initialize a 2D DP table `dp` of size (m+1) x (n+1) with zeros, where `m` and `n` are the lengths of the input strings `x` and `y`.
2. Fill the DP table by comparing characters of `x` and `y`; if characters match, set `dp[i][j] = dp[i-1][j-1] + 1`, else take the max of `dp[i-1][j]` and `dp[i][j-1]`.
3. Start from `dp[m][n]` and trace back to reconstruct the longest common subsequence.
4. If characters match while tracing back, add them to the result string and move diagonally; else move in the direction of the larger DP value.
5. Return the constructed result string as the LCS.


## Program:
```python
/*
Program to implement the longest common subsequence using Dynamic Programming

Developed by: Nithilan S
Register Number: 212223240108
*/
def lcs(x, y):
    m = len(x)
    n = len(y)
    dp = [[0] * (n+1) for _ in range(m+1)]
    
    for i in range(1, m+1):
        for j in range(1, n+1):
            if x[i-1] == y[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
                
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
                
    res = ""
    i, j = m, n
    
    while i>0 and j>0:
        if x[i-1] == y[j-1]:
            res= x[i-1] + res
            i -= 1
            j -= 1
        
        elif dp[i-1][j] > dp[i][j-1]:
            i -= 1
            
        else:
            j -= 1
            
    return res
    
x = input()
y = input()
res = lcs(x, y)
print(lcs(x, y))
```

## Output:
![image](https://github.com/user-attachments/assets/5313b6dc-149c-4ff7-bd4c-a32eea930068)

## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
