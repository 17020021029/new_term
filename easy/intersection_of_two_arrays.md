## problem 
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

Note:
Each element in the result must be unique.
The result can be in any order.

## 代码实现
```C++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        sort(nums1.begin(),nums1.end());sort(nums2.begin(),nums2.end());
        set<int> S;
        for(int i=0,j=0;i<nums1.size()&&j<nums2.size();){
            if(nums1[i]==nums2[j]){S.insert(nums1[i]);i++;j++;}
            else if(nums1[i]<nums2[j]) i++;
            else j++;
        }
        vector<int> iv;
        set<int>::iterator it;
        for(it=S.begin();it!=S.end();it++) iv.push_back(*it);
        return iv;
    }
};
```
