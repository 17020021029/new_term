# 二刷
之前一直用的是c，现在改成c++,因为用了vector，所以感觉比c要好写,就是注意这道题不能用重复元素，所以要加判断条件或直接从i+1开始
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;
        for(int i=0;i<nums.size();i++){
            for(int j=i;j<nums.size();j++)
            {
                if(nums[i]+nums[j]==target&&i!=j)
                {
                    res.push_back(i);
                    res.push_back(j);
                }
            }
        }
        return res;
    }
};
```
