# 216 Combination sum III
## problem
Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

Note:

All numbers will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:

Input: k = 3, n = 7
Output: [[1,2,4]]
Example 2:

Input: k = 3, n = 9
Output: [[1,2,6], [1,3,5], [2,3,4]]
## 解题思路
与上几个combination的思路相同
## 代码实现
```C++
class Solution {
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> res;
        vector<int> temp;
        get_vector(res,temp,k,n,1);
        return res;
    }
    void get_vector(vector<vector<int>>& res,vector<int>& temp,int k,int n,int idex){
        if(n<0||temp.size()>k||idex>10)return;
        if(n==0&&temp.size()==k){
            res.push_back(temp);
        }
        for(int i=idex;i<=9;i++){
            temp.push_back(i);
            get_vector(res,temp,k,n-i,i+1);//若是可以有重复数字，将i+1改为idex+1
            temp.pop_back();
        }
    }
};
```
