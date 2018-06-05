## problem
Given a non-empty array of non-negative integers nums, the degree of this array is defined as the maximum frequency of any one of its elements.

Your task is to find the smallest possible length of a (contiguous) subarray of nums, that has the same degree as nums.

Example 1:

Input: [1, 2, 2, 3, 1]
Output: 2
Explanation: 
The input array has a degree of 2 because both elements 1 and 2 appear twice.
Of the subarrays that have the same degree:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
The shortest length is 2. So return 2.

Example 2:

Input: [1,2,2,3,1,4,2]
Output: 6

## 解题思路
数组程度的概念：一个数组任意一个元素的重复次数的最大值</br>
目标：找到与已给数组程度相同的子数组的最小长度</br>
这里可以把给定数组当作矩阵来理解，这样它的顺序就是不可变的，那么此时要找到的最小长度就是从第一个被当作度的元素开始到最后一个的数组个数

## 代码实现
用hash table实现
```C++
class Solution {
public:
    int findShortestSubArray(vector<int>& nums) {
        unordered_map<int, int> hash;//建立hash表用来处理nums
        int maxfreq=0;
        for(int i=0;i<nums.size();i++){
            hash[nums[i]]++;
            maxfreq=max(hash[nums[i]],maxfreq);
        }//找到度
        if(maxfreq==1)  return 1;
    
        vector<int> max;
        for(auto m:hash){
            if(m.second==maxfreq)
                max.push_back(m.first);
        }//将构成度的元素放到容器中
        
        int minlen=nums.size();
        for(int i=0;i<max.size();i++){
            int curr=max[i];
            int minId=-1;
            int maxId=-1;
            int freq=maxfreq;
            for(int j=0;j<nums.size()&&freq>0;j++){
                if(nums[j]==curr){
                    freq--;
                    if(minId==-1)    minId=j;
                    if(freq==0)     maxId=j;
                }
            }//计算个子列长度
            if(maxId-minId+1<minlen)
                minlen=maxId-minId+1;//找到最小长度
        }
        return minlen;
    }
};
```
## 总结
1. unordered_map的使用
2. auto的使用
