## Unique Paths (c++)

There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.

## Example 1
![image](https://github.com/user-attachments/assets/afab215a-fc1b-43ec-a2c0-d627db4a83ec)

Input: m = 3, n = 7

Output: 28

## Example 2

Input: m = 3, n = 2

Output: 3

Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
- 1. Right -> Down -> Down
- 2. Down -> Down -> Right
- 3. Down -> Right -> Down
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int uniquePaths(int m, int n) 
    {
        vector<int> prev(n,0);
        for(int i=0;i<m;i++)
        {
            vector<int>cur(n,0);
            for(int j=0;j<n;j++)
            {
                if(i==0 && j==0) cur[j]=1;
                else
                {
                    int up=0;
                    int down=0;
                    if(i>0) up=prev[j];
                    if(j>0) down=cur[j-1];
                    cur[j]=up+down;
                }
            }
            prev=cur;
        }
        return prev[n-1];
    }
};
```
## Complexity
- Time complexity : 
  
          O(m×n)
     
- Space complexity :

          O(n)
 
