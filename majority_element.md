# Majority Element 
## problem
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.
## 解题思路
此时出现的众数最多只有一个，且中间的数一定是要求的众数
## 编程实现
```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()/2];
    }
};
```

# Majority Element II
## problem
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times. The algorithm should run in linear time and in O(1) space.

写过的错误解法
```
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        int n=nums.size();
        if(n==0)return res;
        sort(nums.begin(),nums.end());
        for(int i=n/3;i<n;i++)
        {
            if(nums[i]==nums[i-n/3])
                res.push_back(nums[i]);
            int t=nums[i];
            while(nums[i]==t){
                i++;
            }
        }
        return res;
    }
};
```
## 解题思路
限制了时间复杂度，不能进行排序。求超过n/3的众数，最多只有两个，所以可以两遍遍历，先找出可能的两个数，再看看是否符合，返回，因为题目没说一定存在众数，所以一定要进行验证。
## 编程实现
感觉没什么问题，但是在[1]处只能输出[]
```
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        int m1=0,m2=0;
        int cm1=0,cm2=0;
        for(int i=0;i<nums.size();i++){
            if(nums[i]==m1) cm1++;
            else if(nums[i]==m2)   cm2++;
            else if(cm1==0){
                m1==nums[i];
                cm1++;
            }
            else if(cm2==0){
                m2==nums[i];
                cm2++;
            }
            else {
                cm1--;
                cm2--;
            }
        }
        cm1=0;   cm2=0;
        for(int i=0;i<nums.size();i++){
            if(m1==nums[i]) cm1++;
            else if(m2==nums[i])    cm2++;
        }
        if(cm1>nums.size()/3)   res.push_back(m1);
        if(cm2>nums.size()/3)   res.push_back(m2);
        return res;
    }
};
```
参考代码
```C++
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        int m = 0, n = 0, cm = 0, cn = 0;
        for (auto &a : nums) {
            if (a == m) ++cm;
            else if (a ==n) ++cn;
            else if (cm == 0) m = a, cm = 1;
            else if (cn == 0) n = a, cn = 1;
            else --cm, --cn;
        }
        cm = cn = 0;
        for (auto &a : nums) {
            if (a == m) ++cm;
            else if (a == n) ++cn;
        }
        if (cm > nums.size() / 3) res.push_back(m);
        if (cn > nums.size() / 3) res.push_back(n);
        return res;
    }
};
```
