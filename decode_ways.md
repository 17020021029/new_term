# Decode Ways
## problem 
 A message containing letters from A-Z is being encoded to numbers using the following mapping:
````
'A' -> 1
'B' -> 2
...
'Z' -> 26
````
Given an encoded message containing digits, determine the total number of ways to decode it.

For example,
Given encoded message "12", it could be decoded as "AB" (1 2) or "L" (12).

The number of ways decoding "12" is 2.
##  问题分析
给定一个字符串，根据规则，每个字母代表一个数字，看用数字代表的字符能转换成多少个字母表示的字符串。开始不太明白，后来看到网上的解法，都是采用了菲勃列契数，这个在之前的程序里用到过

## 代码实现
```C++
class Solution {
public:
    int numDecodings(string s) {
        if (s.empty() || (s.size() > 1 && s[0] == '0')) return 0;//若第一位为0，因为没有代表的字母，所以不能排序，直接返回0
        vector<int> dp(s.size() + 1, 0);
        dp[0] = 1;
        for (int i = 1; i < dp.size(); ++i) {
            dp[i] = (s[i - 1] == '0') ? 0 : dp[i - 1];
            if (i > 1 && (s[i - 2] == '1' || (s[i - 2] == '2' && s[i - 1] <= '6'))) {
                dp[i] += dp[i - 2];
            }
        }
        return dp.back();
    }
};
```

