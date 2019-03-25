## 3 。没有重复字符的最长子串  
给定一个字符串，找到最长子字符串的长度而不重复字符。

例1：

输入：“abcabcbb” 
输出：3 
 说明：答案是"abc"，长度为3。   
例2：

输入：“BBBBB” 
输出：1
 说明：牛逼，他的回答是"b"，与1的长度。  
例3：

输入：“pwwkew” 
输出：3
 说明：答案是"wke"，长度为3. 

注意答案必须是子字符串，"pwke"是子序列而不是子字符串。

```c
int lengthOfLongestSubstring(char* s) {
int i, j, k, repeat;
int temp, maxlen = -1;
int len = strlen(s);
if (len == 0) 
    return 0;
for(i = 0; i < len; i++) //循环每个字符
{
    j = i + 1;
    temp = 1;
    repeat = 0;//出现重复字符就置1
    while(j < len && repeat == 0)//从i的下一个字符开始统计s[i]字符的最长不重复字串
    {
        k = i;
        while(k < j)//j和i到j-1的每个字符做比较，不等时字串长+1
        {
            if(s[j] != s[k])    k++;
            else{
                repeat = 1;
                break;
            }
        }
        if(k == j)//当前j所对应字符第一次出现
        {
            j++;
            temp++;
        }          
    }
    maxlen = maxlen > temp?maxlen:temp;
 }
 return maxlen;
}
```
