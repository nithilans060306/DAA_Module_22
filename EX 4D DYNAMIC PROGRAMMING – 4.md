# EX 4D DYNAMIC PROGRAMMING – 4
## DATE: 03/05/2025
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.

## Algorithm

1. Create a 2D DP table of size (a+1) x (b+1), where `a` and `b` are lengths of the input strings `str1` and `str2`.
2. Initialize the first row and first column with index values representing conversions from/to an empty string.
3. Traverse through both strings; if characters match, copy the value from the diagonal cell `dp[i-1][j-1]`.
4. If characters differ, set `dp[i][j]` to 1 plus the minimum of insert (`dp[i][j-1]`), delete (`dp[i-1][j]`), or replace (`dp[i-1][j-1]`) operations.
5. Return `dp[a][b]`, which holds the minimum number of operations to convert `str1` to `str2`.

## Program:
```python
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method

.
Developed by: Nithilan S
Register Number: 212223240108
*/
def edit_distance(str1, str2, a, b):
    ################ Add your code here #############
    dp = [[0 for _ in range(b+1)] for _ in range(a+1)]
    
    for i in range(a+1):
        for j in range(b+1):
            if i == 0:
                dp[i][j] = j
            elif j == 0:
                dp[i][j] = i
            
            elif str1[i-1] == str2[j-1]:
                dp[i][j] = dp[i-1][j-1]
                
            else:
                dp[i][j] = 1 + min(dp[i][j - 1], dp[i - 1][j], dp[i - 1][j - 1])
    return dp[a][b]
    
if __name__ == '__main__':
    str1 = input()
    str2 = input()
    print('No. of Operations required :',edit_distance(str1, str2, len(str1), len(str2)))
```

## Output:
![image](https://github.com/user-attachments/assets/808cd9f6-42d5-42cf-8001-9977eaa3ba08)


## Result:
Thus the program was executed successfully for finding edit distance between two strings.
