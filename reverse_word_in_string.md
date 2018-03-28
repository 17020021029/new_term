
## Problem
 Given an input string, reverse the string word by word.

For example,
Given s = "the sky is blue",
return "blue is sky the". 
## 问题分析
我开始是想建立足够大的二维数组，遍历存储各个单词，然后重新组合放进一个string，但是感觉太麻烦，也不是最有效的办法（因为这样好蠢）
但是因为今天满课 ，又有一些事情，所以直接参考了他人的代码。
## 代码实现
```C++
class Solution {

    void reverseword(string &s, int i, int j){
        while(i<j){
          char t=s[i];
          s[i++]=s[j];
          s[j--]=t;
        } 
    }
    
    void reverseWords(string &s) {
        
        int i=0, j=0;
        int l=0;
        int len=s.length();
        int wordcount=0;
        
        while(true){
            while(i<len && s[i] == ' ') i++; 
            if(i==len) break;
            if(wordcount) s[j++]=' ';
            l=j;
            while(i<len && s[i] != ' ') 
            {s[j]=s[i]; j++; i++;} 
            reverseword(s,l,j-1);                
            wordcount++;
            
        }
        
        s.resize(j);                         
        reverseword(s,0,j-1);               
    }
};
```
## 总结
有时间要自己再A一次
