# 739. Daily Temperatures
## Problem
 Given a list of daily temperatures, produce a list that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.

For example, given the list temperatures = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0].

Note: The length of temperatures will be in the range [1, 30000]. Each temperature will be an integer in the range [30, 100]. 
## 问题分析
题意：每一天与比它温度高的一天的天数差，找到第一个就不用再往下遍历；首先想到的就是二重遍历，这个时间复杂度应该挺大的，但是run了一下，样例输入的前几个都是对大，最后两个不对，一直没找到原因
```
class Solution {
public:
   
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        vector<int> res;
        for(int i=0;i<temperatures.size();i++)
        {
            int gap=0;
            for(int j=i;j<temperatures.size();j++)
            {
                if(temperatures[i]>=temperatures[j])
                    gap++;
                else break;
            }
            res.push_back(gap);
            }
        return res;
    }
};
```
看discussion的代码，发现大家基本都会用到stack（容器适配器），但是还不会stack的用法及原理等,所以我想之后再做这道题.
先贴一下代码
```C++
vector<int> dailyTemperatures(vector<int>& temperatures) {
        vector<int> v(temperatures.size(),0);
        stack<pair<int,int>> s;
        for(int i=0;i<temperatures.size();i++)
        {
            while((s.empty()==false)&&((s.top()).first<temperatures[i]))
            {
                v[(s.top()).second] = (i-(s.top()).second);
                s.pop();
            }
            s.push(make_pair(temperatures[i],i));
        }
        return v;
    }
```
