# Optimal Division 
## problem
Given a list of positive integers, the adjacent integers will perform the float division. For example, [2,3,4] -> 2 / 3 / 4.

However, you can add any number of parenthesis at any position to change the priority of operations. You should find out how to add parenthesis to get the maximum result, and return the corresponding expression in string format. Your expression should NOT contain redundant parenthesis.

Example:

Input: [1000,100,10,2]
Output: "1000/(100/10/2)"
Explanation:
1000/(100/10/2) = 1000/((100/10)/2) = 200
However, the bold parenthesis in "1000/((100/10)/2)" are redundant, 
since they don't influence the operation priority. So you should return "1000/(100/10/2)". 

Other cases:
1000/(100/10)/2 = 50
1000/(100/(10/2)) = 50
1000/100/10/2 = 0.5
1000/100/(10/2) = 2

Note:

    The length of the input array is [1, 10].
    Elements in the given array will be in range [2, 1000].
    There is only one optimal division for each test case.

## 问题分析
根据题目，可以看出，不管怎样，只有把括号加在第一位之后的几位上才能得到最大的值</br>
除了第一位，其它都能转换成乘法，且第二位只能做除数，要获得最大值，就要找到最大的被除数，拿一定是除第二位所有数的乘积最大，那么就是上述解法
## 解题思路
返回值定义为string型，那么可以调用to_string()函数，将nums转换为字符型
## 编程实现
```C++
class Solution {
public:
    string optimalDivision(vector<int>& nums) {
        string res;
        int len=nums.size();
        if(len==1)  return to_string(nums[0]);
        if(len==2){
            return to_string(nums[0])+"/"+to_string(nums[1]);
        }
        else {
            for(int i=2;i<len;i++)
            {
                res+="/";
                res+=to_string(nums[i]);
            }
            return to_string(nums[0])+"/"+"("+to_string(nums[1])+res+")";
        }
    }
};
```
## 总结
注意因为nums的长度，可以分情况设计算法，避免出错,但是在discuss里边看到一个很简洁的算法,而且时间复杂度耶更小些
```C++
class Solution {
public:
    string optimalDivision(vector<int>& nums) {
        int n = nums.size();
        string expr;
        for (int i = 0; i < n; i++) {
            if (i > 0) {
                expr += "/";
            }
            if (i == 1 && n > 2) {
                expr += "(";
            }
            expr += to_string(nums[i]);
            if (i == n - 1 && n > 2) {
                expr += ")";
            }
        }
        return expr;
    }
};
```
