## Minimum Falling Path Sum (c++)

Given an n x n array of integers matrix, return the minimum sum of any falling path through matrix.

A falling path starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position (row, col) will be (row + 1, col - 1), (row + 1, col), or (row + 1, col + 1).

## Example 1
![image](https://github.com/user-attachments/assets/ec0995a7-642c-4e0c-b228-78459140e3aa)

Input: matrix = [[2,1,3],[6,5,4],[7,8,9]]

Output: 13

Explanation: There are two falling paths with a minimum sum as shown.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int minFallingPathSum(vector<vector<int>>& matrix) 
    {
        int n=matrix.size();
        int m=matrix[0].size();
        vector<int>prev (m,0);
        for(int j=0;j<m;j++) prev[j]=matrix[0][j];
        for(int i=1;i<n;i++)
        {
            vector<int>temp (m,0);
            for(int j=0;j<m;j++)
            {
                int u=matrix[i][j]+prev[j];
                int ld=matrix[i][j];
                if(j-1>=0) ld+=prev[j-1];
                else ld=1e9;
                int rd=matrix[i][j];
                if(j+1<m) rd+=prev[j+1];
                else rd=1e9;
                temp[j]=min(u,min(ld,rd));
            }
            prev=temp;
        }
        int mini=1e9;
        for(int j=0;j<m;j++)
        {
            mini=min(mini,prev[j]);
        }
        return mini;
    }
};
```
## Complexity
- Time complexity : 
  
          O(m×n)
     
- Space complexity :

          O(n)
 
