## Frog Jump (c++)

Given an integer array height[] where height[i] represents the height of the i-th stair, a frog starts from the first stair and wants to reach the top. From any stair i, the frog has two options: it can either jump to the (i+1)th stair or the (i+2)th stair. The cost of a jump is the absolute difference in height between the two stairs. Determine the minimum total cost required for the frog to reach the top.

## Example
Input: heights[] = [20, 30, 40, 20] 

Output: 20

Explanation:  Minimum cost is incurred when the frog jumps from stair 0 to 1 then 1 to 3:
- jump from stair 0 to 1: cost = |30 - 20| = 10
- jump from stair 1 to 3: cost = |20-30|  = 10
- Total Cost = 10 + 10 = 20

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int minCost(vector<int>& height) 
    {
        int n=height.size();
        if (n == 1) return 0;
        int prev=0;
        int prev2=0;
        for(int i=1;i<n;i++)
        {
            int jumpTwo = INT_MAX;
            int jumpOne= prev + abs(height[i]-height[i-1]);
            if(i>1) 
            {
                jumpTwo = prev2 + abs(height[i]-height[i-2]);
            }
            int cur_i=min(jumpOne, jumpTwo);
            prev2=prev;
            prev=cur_i;
        }
        return prev;
    }
};
```
## Complexity
- Time complexity : 
  
          O(N)
     
- Space complexity :

          O(1)
