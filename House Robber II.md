## House Robber II (c++)

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

## Example
Input: nums = [2,3,2]

Output: 3

Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.

## PROGRAM:(Main.cpp)
```
class Solution 
{
public:
    int rob1(int start,int end,vector<int>& nums) 
    {
        int n=nums.size();
        if(n==0) return 0;

        int prev=nums[start];
        int prev2=0;
        for(int i=start+1;i<=end;i++)
        {
            int take=nums[i];
            if(i>start+1) take+=prev2;
            int not_take=0+prev;

            int cur_i=max(take,not_take);

            prev2=prev;
            prev=cur_i;
        }
        return prev;
    }
public:
    int rob(vector<int>& nums) 
    {
        int n=nums.size();
        if(n==1) return nums[0];
        return max(rob1(0,n-2,nums),rob1(1,n-1,nums));  
    }
};
```
## Complexity
- Time complexity : 
  
          O(N)
     
- Space complexity :

          O(1)
