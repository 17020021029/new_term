# Word Break 
## problem
 Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words. You may assume the dictionary does not contain duplicate words.

For example, given
s = "leetcode",
dict = ["leet", "code"].

Return true because "leetcode" can be segmented as "leet code".

UPDATE (2017/1/4):
The wordDict parameter had been changed to a list of strings (instead of a set of strings). Please reload the code definition to get the latest changes. 
## 问题分析
首先，我对字符串类和vector类都不了解，所以只能迎战头皮瞎做，希望可以逐渐学到一些用法。

看了一个discuss里的程序，用到了s.substr()函数，返回指定位置内的字符串；count函数,没找到相应的用法,试了一下这个算法编译既不能通过。但大体的思路就是遍历字符串的每一位，用一个整型数组记录每一位字符的匹配情况，若匹配，则将临时数组赋值为1
## 代码实现
```C++
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        int n = s.size();
        unordered_set<string>Dict(wordDict.begin(),wordDict.end());
        vector<bool>dp(n,false);
        for(int i = 0; i<n;i++)
            for(int j = 0; j<=i && !dp[i]; j++)
                if(Dict.count(s.substr(j,i-j+1))>0)
                    dp[i] = j== 0 ? true: dp[j-1];
        return dp[n-1];
    }
};
```
## 总结
这道题我就先不A了，因为真的好多都不会用，看别人代码都看不懂，就先留在这，过一段时间再A，要不然老觉得自己都会了
