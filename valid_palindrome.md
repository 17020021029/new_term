# Valid Palindrome
## problem
 Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

Note:
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome. 
## 解题思路
这道题本身是一道easy题，因为今天沉溺与类和对象，很晚才开始写leetcode，所以找了一道easy题

这个思路是之前看到过的，我觉得很巧妙是在于调用了两种函数，使整个代码看起来一场简单

## 代码实现
```c
bool isPalindrome(char* s) {
    int len = strlen(s);
    if(!len) return true;
    char *p1 = s, *p2 = s + len - 1;
    while(p1 < p2){
        if(!isalnum(*p1)){p1++;continue;} //isalnum,判断是否为字符型
        if(!isalnum(*p2)){p2--;continue;}
        if(tolower(*p1++) != tolower(*p2--)) return false; //tolower，将字母字符转换成小写
    }
    return true;
}
```
## 总结
两个函数的调用
