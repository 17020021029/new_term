# 二刷
首先想到直接三重遍历是一定要超时的，所以想到可以将第一层遍历的值定义为target，然后再找two sum，但是要注意这里要用二分查找法
```C++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> res;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size();i++){
            int target=-nums[i];
            int begin=i+1;
            int end=nums.size()-1;
            while(begin<end){
                int sum=nums[begin]+nums[end];
                if(sum<target)
                    begin++;
                else if(sum>target)
                    end--;
                else {
                    vector<int> temp;
                    temp.push_back(nums[i]);
                    temp.push_back(nums[begin]);
                    temp.push_back(nums[end]);
                    res.push_back(temp);
                    
                    while(begin<end&&nums[begin]==temp[1])
                        begin++;
                    while(begin<end&&nums[end]==temp[2])
                        end--;
                    
                }
                while(i+1<nums.size()&&nums[i+1]==nums[i])
                    i++;
            }
        }
        return res;
    }
};
```
## 反思
1. begin与end的初值的定义
2. 改变i的条件
3. 怎么讲现在的数组加到res
4. 要判断是否又重复元素构成的数组
