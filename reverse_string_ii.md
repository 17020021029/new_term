## problem
Given a string and an integer k, you need to reverse the first k characters for every 2k characters counting from the start of the string. If there are less than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and left the other as original.

Example:

Input: s = "abcdefg", k = 2
Output: "bacdfeg"

Restrictions:

    The string consists of lower English letters only.
    Length of the given string and k will in the range [1, 10000]


## 编程实现
RE
```C
class Solution {
public:
    string reverseStr(string s, int k) {
        int len=s.size();
        for(int i=0;i<len;)
        {
            int num=len;
            if(num<=k)
            {
                int begin=i;
                int end=len-1;
                while(begin<=end)
                {
                    swap(s[begin],s[end]);
                    begin++;end--;
                }
            }
            else{
                int begin=i;
                int end=i+k-1;
                while(begin<=end)
                {
                    swap(s[begin],s[end]);
                    begin++;end--;
                }
            }
           num-=2*k; 
            i=i+2*k;
        }
        return s;
    }
};
```
