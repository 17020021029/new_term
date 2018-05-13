## problem 
Given an array of strings, group anagrams together.

Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
Note:

All inputs will be in lowercase.
The order of your output does not matter.
## 解题思路
题意是把容器中相同字母的字符串放在不同的一维数组中（包含在二维数组中），顺序是任意的；</br>
运用map的特性，查看是否与前边的字符串相同，若相同，加到前边的容器中，若不相同，重新写入一个容器
## 代码实现
```C++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> res;
        map<string,int> test;
        for(int i=0;i<strs.size();i++){
            string temp=strs[i];
            sort(temp.begin(),temp.end());
            if(test.count(temp)==0){
                test[temp]=res.size();
                vector<string> v;
                v.push_back(strs[i]);
                res.push_back(v);
            }
            else{
                res[test[temp]].push_back(strs[i]);
            }
        }
       return res; 
    }
};
```
