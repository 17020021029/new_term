# Largest Number
## problem
Given a list of non negative integers, arrange them such that they form the largest number.

Example 1:

Input: [10,2]
Output: 210
Example 2:

Input: [3,30,34,5,9]
Output: 9534330
Note: The result may be very large, so you need to return a string instead of an integer.
## 解题思路&过程
将整数转换为字符串型放进容器中，对容器进行排序，使得让元素顺序相加能得到最大的整数，这里自定义了sort排序的规则，*应该是一个全局函数，开始没加static报错，*sort函数的实现还没弄清楚即每相邻两个字符串相加进行比较，若大
，顺序不变，这里用到了字符串的比较大小的规律，可以直接根据字符串的大小比较对应的整数的大小；定义一个vector容器的迭代器，是容器元素顺序相加得到返回值；最后还要
判断前边是否有重复的0，也就是数组元素全为0的情况，只要保留一个0即可,这里用到了erase函数，具体减删除算法,这个根据前边写完的程序给定的报错信息确定的，样例输出：

````
Input [0,0]
Output "00"
Expacted "0"
````
## 编程实现
```C++
class Solution {
public:
        static bool compare(string& a,string& b){
        return (a+b)>(b+a);
    }
    string largestNumber(vector<int>& nums) {
        string res;
        vector<string> tmp;
        for(int i=0;i<nums.size();i++){
            tmp.push_back(to_string(nums[i]));
        }
        sort(tmp.begin(),tmp.end(),compare);
        vector<string>::iterator i;
        for(i=tmp.begin();i!=tmp.end();i++){
            res+=*i;
        }
        while(res[0]=='0'&&res.length()>1)
            res.erase(0,1);
        return res;
    }

};
```
