# Happy number
## Problem
````
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example: 19 is a happy number

    12 + 92 = 82
    82 + 22 = 68
    62 + 82 = 100
    12 + 02 + 02 = 1

````
## 问题分析
因为这是一个不断递归的过程，等式右边的数是最后要判断是否为1的数，也是下一行要分离处理的数，因此可以写一个函数用来递归操作，计算要判断的值；</br>
在主函数里，判断最终结果是否为1，然后输出结果。

我开始的思路是主函数while循环的条件为n>10，但是测试值为7时总是输出错误，然后意识到，输入的数字若为1位数字，那他本身也要进行平方运算，后来看到，有人判断n==4的情况，意识到要想最终得到循环的数字，那么只能为4或1，那么直接判断4或1即可
## 代码实现
```ruby
int get_eve(int x)
{
    int result=0;
    int t;
    while(x>0){
        t=x%10;
        result+=t*t;
        x=x/10;
    }
    return result;
}
bool isHappy(int n) {
    while(n!=1){
        n=get_eve(n);
        if(n==4)
        {
            return false;
        }
    }
    return true;
}
```
