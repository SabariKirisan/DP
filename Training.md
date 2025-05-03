## Training (c++)

Geek is going for a training program for n days. He can perform any of these activities: Running, Fighting, and Learning Practice. Each activity has some point on each day. As Geek wants to improve all his skills, he can't do the same activity on two consecutive days. Given a 2D array arr[][] of size n where arr[i][0], arr[i][1], and arr[i][2] represent the merit points for Running, Fighting, and Learning on the i-th day, determine the maximum total merit points Geek can achieve .

## Example

Input: arr[]= [[1, 2, 5], [3, 1, 1], [3, 3, 3]]

Output: 11

Explanation: Geek will learn a new move and earn 5 point then on second day he will do running and earn 3 point and on third day he will do fighting and earn 3 points so, maximum merit point will be 11.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int maximumPoints(vector<vector<int>>& arr) 
    {
        int n=arr.size();
        vector<int>prev(4,0);
        
        prev[0]=max(arr[0][1],arr[0][2]);
        prev[1]=max(arr[0][0],arr[0][2]);
        prev[2]=max(arr[0][0],arr[0][1]);
        prev[3]=max(arr[0][0],max(arr[0][1],arr[0][2]));
        
        for(int day=1;day<n;day++)
        {
            vector<int> temp(4,0);
            for(int last=0;last<4;last++)
            {
                for(int task=0;task<3;task++)
                {
                    if(task!=last)
                    {
                        int point=arr[day][task]+prev[task];
                        temp[last]=max(temp[last],point);
                    }
                }
            }
            prev=temp;
        }
        return prev[3];
    }
};
```
## Complexity
- Time complexity : 
  
          O(N x 4 x 3)
     
- Space complexity :

          O(4)
