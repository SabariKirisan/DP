## Unique Paths II (c++)

You are given an m x n integer array grid. There is a robot initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

An obstacle and space are marked as 1 or 0 respectively in grid. A path that the robot takes cannot include any square that is an obstacle.

Return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The testcases are generated so that the answer will be less than or equal to 2 * 109.

## Example 1
![image](https://github.com/user-attachments/assets/580bb4be-7066-4d33-925b-55a458a88ed2)

Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]

Output: 2

Explanation: There is one obstacle in the middle of the 3x3 grid above.
- There are two ways to reach the bottom-right corner:
- 1. Right -> Right -> Down -> Down
- 2. Down -> Down -> Right -> Right
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) 
    {
        int n=obstacleGrid.size();
        int m=obstacleGrid[0].size();
        vector<int>prev (m,0);
        for(int i=0;i<n;i++)
        {
            vector<int> temp(m,0);
            for(int j=0;j<m;j++)
            {
                if(obstacleGrid[i][j]==1) temp[j]=0;
                else if(i==0 && j==0) temp[j]=1;
                else
                {
                    int up=0;
                    int down=0;
                    if(i>0) up=prev[j];
                    if(j>0) down=temp[j-1];
                    temp[j]=up+down;
                }
            }
            prev=temp;
        }
        return prev[m-1];   
    }
};
```
## Complexity
- Time complexity : 
  
          O(m×n)
     
- Space complexity :

          O(n)
 
