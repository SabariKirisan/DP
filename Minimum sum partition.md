## Minimum sum partition (c++)

Given an array arr[]  containing non-negative integers, the task is to divide it into two sets set1 and set2 such that the absolute difference between their sums is minimum and find the minimum difference.

## Example
Input: arr[] = [1, 6, 11, 5]

Output: 1

Explanation: 
- Subset1 = {1, 5, 6}, sum of Subset1 = 12 
- Subset2 = {11}, sum of Subset2 = 11 
- Hence, minimum difference is 1. 

## PROGRAM:(Main.cpp)
```
class Solution {

  public:
    int minDifference(vector<int>& arr) 
    {
        int n=arr.size();
        int totsum=0;
        for(int i=0;i<n;i++)
        {
            totsum+=arr[i];
        }
        int sum=totsum;

        vector<vector<bool>> dp(n,vector<bool>(sum+1,false));
        for(int i=0;i<n;i++)
        {
            dp[i][0]=true;
        }
        if (arr[0] <= sum) 
        {
            dp[0][arr[0]] = true;
        }
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
        
        int mini=1e9;
        for(int s1=0;s1<=totsum/2;s1++)
        {
            if(dp[n-1][s1]==true)
            {
                mini=min(mini,abs((totsum-s1)-s1));
            }
        }
        return mini;
        
    }
};
```
## Complexity
- Time complexity : 
  
          O(n * sum)
     
- Space complexity :

          O(n * sum)
