# Combination Sum IV
## Problem
 Given an integer array with all positive numbers and no duplicates, find the number of possible combinations that add up to a positive integer target.

Example:

nums = [1, 2, 3]
target = 4

The possible combination ways are:
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)

Note that different sequences are counted as different combinations.

Therefore the output is 7.

Follow up:
What if negative numbers are allowed in the given array?
How does it change the problem?
What limitation we need to add to the question to allow negative numbers? 

## 代码实现
最开始当然是想用递归，但是写过了之后发现超时了，如下
```C++
class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        int res=0;
        get_res(nums,target,res,0);
        return res;
    }
    void get_res(vector<int>& nums,int target,int& res,int tmp)
    { 
        int t;
        for(int i=0;i<nums.size();i++){
            t=tmp+nums[i];
            if(tmp<target){
                get_res(nums,target,res,t);
            }
            else if(tmp==target){
                res++;
                break;
            }
            else break;
        }
    }
};
```
[参考代码](https://blog.csdn.net/JANESTAR/article/details/52163357)
但是还是不是很懂这种做法
  ```C++
  class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        if(target==0)
            return 1;
        vector<int> dp(target+1,0);
        dp[0]=1;
        for(int i=1;i<=target;i++){
            for(int j=0;j<nums.size();j++){
                if(i>=nums[j])
                    dp[i]+=dp[i-nums[j]];
            }
        }
        return dp[target];
    }
};
  ```

