## problem
Given a string containing only digits, restore it by returning all possible valid IP address combinations.

Example:

Input: "25525511135"
Output: ["255.255.11.135", "255.255.111.35"]
## 解题思路
递归法，若每一部分小于等于255，则插入".",当记录的"."数等于3的时候，不再插入"."</br>
IP地址由32位二进制数组成，为便于使用，常以XXX.XXX.XXX.XXX形式表现，每组XXX代表小于或等于255的10进制数。
所以说IP地址总共有四段，每一段可能有一位，两位或者三位，范围是[0, 255]，题目明确指出输入字符串只含有数字，
所以当某段是三位时，我们要判断其是否越界（>255)，还有一点很重要的是，当只有一位时，0可以成某一段，如果有两位或三位时，
00， 01， 001， 011， 000等都是不合法
## 代码实现
```C++
class Solution {
public:
    vector<string> restoreIpAddresses(string s) {
        vector<string> res;
        restore(s,0,"",res);
        return res;
    }
    void restore(string s,int num,string out,vector<string>& res){
        if(num==4){
            if(s.empty())
                res.push_back(out);
        }   //代表全部的字符已经restore
        else{
          for(int i=1;i<4;i++){
              if(s.size()<i)
                  break;
              int val=atoi(s.substr(0,i).c_str());
              if(val>255||i!=to_string(val).size())
                  continue;
              restore(s.substr(i),num+1,out+s.substr(0,i)+(num==3? "":"."),res);
          }
        }
    }
};
```
