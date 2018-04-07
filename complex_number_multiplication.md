# Complex Number
## problem
 Given two strings representing two complex numbers.

You need to return a string representing their multiplication. Note i2 = -1 according to the definition.

Example 1:

Input: "1+1i", "1+1i"
Output: "0+2i"
Explanation: (1 + i) * (1 + i) = 1 + i2 + 2 * i = 2i, and you need convert it to the form of 0+2i.

Example 2:

Input: "1+-1i", "1+-1i"
Output: "0+-2i"
Explanation: (1 - i) * (1 - i) = 1 + i2 - 2 * i = -2i, and you need convert it to the form of 0+-2i.

Note:

    The input strings will not have extra blank.
    The input strings will be given in the form of a+bi, where the integer a and b will both belong to the range of [-100, 100]. And the output should be also in this form.

## 解题步骤
### 一
考虑到数字为个位数，好傻哦
```
class Solution {
public:
    string complexNumberMultiply(string a, string b) {
        int* as=new int[2],* bs=new int[2];
        as=get_num(a,as);
        bs=get_num(b,bs);
        int ar,br;
        ar=as[0]*bs[0]-as[1]*bs[1];
        br=bs[0]*as[1]+as[0]*bs[1];
        return to_string(ar)+"+"+to_string(br)+"i";
    }
    int* get_num(string tmp,int* &s)
    {
        int len=tmp.length();
        if(len==4)
        {
            s[0]=(int)(tmp[0]-'0');
            s[1]=(int)(tmp[2]-'0');
        }
        if(len==5&&tmp[2]=='-')
        {
            s[0]=(int)(tmp[0]-'0');
            s[1]=-1*(int)(tmp[3]-'0');
        }
        if(len==5&&tmp[0]=='-')
        {
            s[0]=-1*(int)(tmp[1]-'0');
            s[1]=(int)(tmp[3]-'0');
        }
        if(len==6)
        {
            s[0]=-1*(int)(tmp[1]-'0');
            s[1]=-1*(int)(tmp[4]-'0');
        }
        return s;
    }
};
```
### 二
用到stoi(),substr(),找到"+"后，直接计算实部和虚部，计算两个字符串的实部和虚部，计算所得字符串的实部和虚部，返回的时候转为字符串，to_string()
```C++
class Solution {
public:
    string complexNumberMultiply(string a, string b) {
        int ra,ia,rb,ib;
        for(int i=0;i<a.length();i++)
        {
            if(a[i]=='+')
            {
                ra=stoi(a.substr(0,i));
                ia=stoi(a.substr(i+1,a.length()-i-2));
                break;
            }
        }
        for(int i=0;i<b.length();i++)
        {
            if(b[i]=='+')
            {
                rb=stoi(b.substr(0,i));
                ib=stoi(b.substr(i+1,b.length()-i-2));
                break;
            }
        } 
        int rt=ra*rb-ia*ib;
        int it=ra*ib+rb*ia;
        return to_string(rt)+"+"+to_string(it)+"i";
    }
};
```
