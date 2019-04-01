#####给定字符串*s*由大写/小写字母和空格字符组成`' '`，返回字符串中最后一个单词的长度。

##### 如果最后一个单词不存在，则返回0。

**注意：**单词定义为字符序列仅由非空格字符组成。

**例**：输入：“Hello World”  输出：5

实现代码：

```c
int lengthOfLastWord(char* s) {
    if (NULL == s || 0 == strlen(s)) return 0;
    
    unsigned int length_of_s = strlen(s);
    unsigned int length_of_LW = 0;
    int flag = 0;  
    for (int i = length_of_s-1; i >= 0 && 2 != flag; --i) {
        if (0 == flag && ' ' == s[i]) continue;
        if (1 == flag && ' ' == s[i]) {
            flag = 2;
            continue;
        }
        if (0 == flag) flag = 1;
        ++length_of_LW;
    }
    return length_of_LW;
}
```

