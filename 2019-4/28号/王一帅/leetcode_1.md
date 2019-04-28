## 有效的括号

给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'` 的字符串，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

**示例 1:**

```
输入: "()"
输出: true
```

**示例 2:**

```
输入: "()[]{}"
输出: true
```

**示例 3:**

```
输入: "(]"
输出: false
```

**示例 4:**

```
输入: "([)]"
输出: false
```

**示例 5:**

```c
输入: "{[]}"
输出: true
    

    bool isValid(char * s){
    	int i=1; 
    	char arr[9999]={0}; 
    	while(*s!='\0') 
    	{ 
        	switch(*s) 
        	{ 
            	case '(': arr[i]='('; i++; break; 
            	case '[': arr[i]='['; i++; break; 
            	case '{': arr[i]='{'; i++; break; 
            	case ')': if(arr[--i] == '(') arr[i]=0; else return false; break; 
            	case ']': if(arr[--i] == '[') arr[i]=0; else return false; break; 
            	case '}': if(arr[--i] == '{') arr[i]=0; else return false; break; 
            	default:
                	break;
        	} 
        	s++; 
    	} 
    	if(arr[1]==0) 
        	return true; 
    	else 
        	return false; 
	}
```