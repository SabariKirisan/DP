## Partition Equal Subset Sum (c++)

Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.

## Example
Input: nums = [1,5,11,5]

Output: true

Explanation: The array can be partitioned as [1, 5, 5] and [11].

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool isSubsetSum(vector<int>& arr, int sum) 
    {
        int n=arr.size();
        vector<vector<bool>> dp(n,vector<bool>(sum+1,false));
        for(int i=0;i<n;i++)
        {
            dp[i][0]=true;
        }
        if(arr[0]<=sum) dp[0][arr[0]]=true;
        for(int i=1;i<n;i++)
        {
            for(int target=1;target<=sum;target++)
            {
                bool nottake=dp[i-1][target];
                bool take=false;
                if(arr[i]<=target) take=dp[i-1][target-arr[i]];
                dp[i][target]=take | nottake;
            }
        }
        return dp[n-1][sum];
    }
    bool canPartition(vector<int>& nums) 
    {
        int n=nums.size();
        int totsum=0;
        for(int i=0;i<n;i++)
        {
            totsum+=nums[i];
        }
        if(totsum%2) return false;
        int target=totsum/2;

        return isSubsetSum(nums,target);        
    }
};
```
## Complexity
- Time complexity : 
  
          O(n * T) where T = total sum of array
     
- Space complexity :

          O(n * T)
