# 字符串冒泡排序
## Problem
N个字符串，输出扫描K(<N)边后的中间结果序列
## 代码实现
```ruby
#include<iostream>
#include<string>
using namespace std;
int main()
{
        string str[100],temp;
        int N,K;
        cin>>N>>K;
        for(int i=0;i<N;i++)
        {
                cin>>str[i];
        }
        for(int i=0;i<K;i++)  //原题要求k次遍历（1<K<N<100)
           for(int j=0;j<N-1-i;j++)
                {
                        if(str[j]>str[j+1])
                        {
                           temp=str[j];
                           str[j]=str[j+1];
                           str[j+1]=temp;
                        }
                }
        for(int  k=0;k<N;k++)
        {
                cout<<str[k]<<endl;
        }
return 0;
}
```
