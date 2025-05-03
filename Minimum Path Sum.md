## Minimum Path Sum (c++)

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

## Example 1
![image](https://github.com/user-attachments/assets/38c87a19-07ac-4f0e-ba38-8534385fa064)

Input: grid = [[1,3,1],[1,5,1],[4,2,1]]

Output: 7

Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) 
    {
        int n=grid.size();
        int m=grid[0].size();
        vector<int> prev(m,0);
        for(int i=0;i<n;i++)
        {
            vector<int> temp(m,0);
            for(int j=0;j<m;j++)
            {
                if(i==0 && j==0) temp[j]=grid[i][j];
                else
                {
                    int up=grid[i][j];
                    if(i>0) up+=prev[j];
                    else up+=1e9;

                    int down=grid[i][j];
                    if(j>0) down+=temp[j-1];
                    else down+=1e9;

                    temp[j]=min(up,down);
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
 
