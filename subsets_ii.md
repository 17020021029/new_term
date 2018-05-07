# Subsets II
## problem
Given a collection of integers that might contain duplicates, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: [1,2,2]
Output:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]

## 代码实现
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> res;
        map<vector<int>,bool> m;
        for(int i=0;i<pow(2,nums.size());i++){
            int t=i;
            vector<int> temp;
            for(int j=nums.size()-1;j>=0;j--){
                if(!t)
                    break;
                if(t%2==1){
                    temp.push_back(nums[j]);
                }
                t>>=1;
            }
                sort(temp.begin(),temp.end());
                if(m.find(temp)==m.end()){
                    m[temp]=true;
                    res.push_back(temp);
                }
        }    
        return res;
    }
};
## 反思
这道题我开始一直在找样例输出的规律，但后来参考代码发现，子集位置不同也能通过，所以这题就只要想办法求不重复的子集就好了
