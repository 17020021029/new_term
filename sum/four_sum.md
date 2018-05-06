# 二刷
## 解题思路
和3sum相同，不过注意要加一层循环
## 代码实现
```C++
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>> res;        
        if(nums.size()<4)
            return res;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size()-3;i++){
            for(int j=i+1;j<nums.size()-2;j++){
                int begin=j+1;
                int end=nums.size()-1;
                while(begin<end){
                    int sum=nums[begin]+nums[end]+nums[i]+nums[j];
                    if(sum<target)  begin++;
                    else if(sum>target) end--;
                    else{
                        vector<int> tmp;
                        tmp.push_back(nums[i]);
                        tmp.push_back(nums[j]);
                        tmp.push_back(nums[begin]);
                        tmp.push_back(nums[end]);
                        res.push_back(tmp);
                        while(begin<end&&nums[begin]==tmp[2])begin++;
                        while(begin<end&&nums[end]==tmp[3])end--;
                    }
                }
            while(nums[j+1]==nums[j]&&j<nums.size()-2)j++;           
            }
        while(nums[i+1]==nums[i]&&i<nums.size()-3)i++;
        }
        return res;
    }
};
```
## 总结
1. 注意两层循环的起始位置
2. 根据第一条，改变i j值时，条件也要注意
3. 这题需要判断元素个数
