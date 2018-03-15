# Product of Array Except Self
## problem 
 Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Solve it without division and in O(n).

For example, given [1,2,3,4], return [24,12,8,6].

Follow up:
Could you solve it with constant space complexity? (Note: The output array does not count as extra space for the purpose of space complexity analysis.)
## 问题分析
要求返回一个数组，每个数组的元素代表出此项原来的元素外其他元素的乘积</br>
题目应该是主要考查时间复杂度的减小
## 编程实现
超时，这个就是题目否定的做法
```
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int a=nums.size();
        vector<int> res(a,1);
        for(int i=0;i<a;i++)
        {
            for(int j=0;j<a;j++)
            {
                if(j!=i)
                res[i]*=nums[j];
            }
        }
        return res;
    }
};
```
AC代码：我们想，对于某一个数字，如果我们知道其前面所有数字的乘积，同时也知道后面所有的数乘积，那么二者相乘就是我们要的结果，所以我们只要分别创建出这两个数组即可，分别从数组的两个方向遍历就可以分别创建出乘积累积数组
```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> fwd(n, 1), bwd(n, 1), res(n);
        for (int i = 0; i < n - 1; ++i) {
            fwd[i + 1] = fwd[i] * nums[i];
        }
        for (int i = n - 1; i > 0; --i) {
            bwd[i - 1] = bwd[i] * nums[i];
        }
        for (int i = 0; i < n; ++i) {
            res[i] = fwd[i] * bwd[i];
        }
        return res;
    }
};
```
