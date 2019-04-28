##  最后一个单词长度

给定一个仅包含大小写字母和空格 `' '` 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

**说明：**一个单词是指由字母组成，但不包含任何空格的字符串。

**示例:**

```c
输入: "Hello World"
输出: 5
    
    int lengthOfLastWord(char * s){
    	int i=strlen(s);
		int j,end=0,begin=0,len=0;
		for(j=i-1;j>=0;j--)
		{
			if((s[j+1]=='\0'&&s[j]!=' ')||(s[j+1]==' '&&s[j]!=' '))//可能是从最后一个字母开始统计
				end=j+1;
			if((j==0&&s[0]!=' ')||(s[j]!=' '&&s[j-1]==' '))//可能遍历到第一个字母
			{
				begin=j;
				break;
			}
		}
    	len=end-begin;
		return len;
	}
```