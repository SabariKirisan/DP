## Partitions with Given Difference (c++)

Given an array arr[], partition it into two subsets(possibly empty) such that each element must belong to only one subset. Let the sum of the elements of these two subsets be sum1 and sum2. Given a difference d, count the number of partitions in which sum1 is greater than or equal to sum2 and the difference between sum1 and sum2 is equal to d. 

## Example
Input: arr[] =  [5, 2, 6, 4], d = 3

Output: 1

Explanation: There is only one possible partition of this array. Partition : {6, 4}, {5, 2}. The subset difference between subset sum is: (6 + 4) - (5 + 2) = 3.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int isSubsetSum(vector<int>& arr, int sum) 
    {
        int n=arr.size();
        vector<vector<int>> dp(n,vector<int>(sum+1,0));
        if(arr[0]==0) dp[0][0]=2;
        else dp[0][0]=1;
        if(arr[0]!=0 && arr[0]<=sum) dp[0][arr[0]]=1;
        for(int i=1;i<n;i++)
        {
            for(int target=0;target<=sum;target++)
            {
                int nottake=dp[i-1][target];
                int take=0;
                if(arr[i]<=target) take=dp[i-1][target-arr[i]];
                dp[i][target]=take + nottake;
            }
        }
        return dp[n-1][sum];
    }
    int countPartitions(vector<int>& arr, int d) 
    {
        int totsum=0;
        for(int i=0;i<arr.size();i++)
        {
            totsum+=arr[i];
        }
        if(totsum-d < 0 || (totsum-d)%2 != 0) return 0;
        return isSubsetSum(arr,(totsum-d)/2);
    }
};
```
## Complexity
- Time complexity : 
  
          O(n * sum)
     
- Space complexity :

          O(n * sum)
