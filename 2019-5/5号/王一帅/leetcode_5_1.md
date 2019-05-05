## 最长公共前缀

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

**示例 1:**

```
输入: ["flower","flow","flight"]
输出: "fl"
```

**示例 2:**

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```

**说明:**

所有输入只包含小写字母 `a-z` 

```c
char * longestCommonPrefix(char ** strs, int strsSize){
    if(strsSize == 0) 
    {
        char* result = (char*)calloc(1, sizeof(char));
        return result;
    }
    int index = 0, i = 0;
    char flag = strs[0][index];
    while(flag) 
    {
        for(i = 1; i < strsSize; i++) 
        {
            if(strs[i][index] != flag)
                break;
        }
        if(i < strsSize)
            break;
        flag = strs[0][++index];
    }
    strs[0][index] = '\0';
    return strs[0];
}
```

