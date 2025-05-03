## Triangle (c++)

Given a triangle array, return the minimum path sum from top to bottom.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index i on the current row, you may move to either index i or index i + 1 on the next row.

## Example 1
Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]


Output: 11

Explanation: The triangle looks like:
-    2
-   3 4
-  6 5 7
- 4 1 8 3

The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) 
    {
        int n=triangle.size();
        vector<int> prev(n,0),temp(n,0);
        for(int j=0;j<n;j++)
        {
            prev[j]=triangle[n-1][j];
        }
        for(int i=n-2;i>=0;i--)
        {
            for(int j=i;j>=0;j--)
            {
                int d=triangle[i][j]+prev[j];
                int dg=triangle[i][j]+prev[j+1];
                temp[j]=min(d,dg);
            }
            prev=temp;
        }
        return prev[0];
    }
};
```
## Complexity
- Time complexity : 
  
          O(m×n)
     
- Space complexity :

          O(n)
 
