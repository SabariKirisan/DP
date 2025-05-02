## Climbing Stairs (c++)

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Example
Input: n = 3

Output: 3

Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int climbStairs(int n) 
    {
        int prev=1;
        int prev2=1;

        for(int i=2;i<=n;i++)
        {
            int cur_i=prev+prev2;
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
