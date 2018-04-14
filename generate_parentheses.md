# generate parentheses
括号匹配的问题
## problem
 Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
## 问题分析
这题寒假就一直困扰我，根本不知道要怎么做才行，连别人的代码都看不懂，不过现在emmmm，可以看懂别人的代码了；主要是思路弄明白了</br>
向string里添加“（”或“）”，条件是，总的数目不多与2*n，插入）要判断是否大于（的数目
## 解题思路
先要开一个string类型容器来存储返回值，写一个helper函数，递归处理每一个string
## 代码实现
```C++
class Solution {
public:
    vector<string> res;
    void helper(int i,int j,int n,string s)//i用于记录 (, j用于记录 )
    {
        if(j<0) return;//当全部的组合都用完时，直接返回
        if(i==n){
            if(j==0)
                res.push_back(s);//当全部(都加完，且可用的）为0时，将字符串加到vector中
            return;
        }
        helper(i+1,j+1,n,s+"(");//加上一个（后，可用的)加一
        helper(i+1,j-1,n,s+")");//加上一个)后，可用的）减一
    }
    vector<string> generateParenthesis(int n) {
        string s="";
        helper(0,0,2*n,s);
        return res;
    }
};
```
