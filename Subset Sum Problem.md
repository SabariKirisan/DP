## Subset Sum Problem (c++)

Given an array of positive integers arr[] and a value sum, determine if there is a subset of arr[] with sum equal to given sum. 

## Example
Input: arr[] = [3, 34, 4, 12, 5, 2], sum = 9

Output: true 

Explanation: Here there exists a subset with target sum = 9, 4+3+2 = 9.

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
        dp[0][arr[0]]=true;
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
};
```
## Complexity
- Time complexity : 
  
          O(n * sum)
     
- Space complexity :

          O(n * sum)
