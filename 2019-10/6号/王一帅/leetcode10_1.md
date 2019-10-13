给定一个字符串，逐个翻转字符串中的每个单词。

示例 1：

输入: "the sky is blue"
输出: "blue is sky the"
示例 2：

输入: "  hello world!  "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
示例 3：

输入: "a good   example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。



```c
void reverse(char* s, int i, int j){
    while(i < j){
        char c = s[i];
        s[i] = s[j];
        s[j] = c;
        i++; j--;
    }
}

char * reverseWords(char * s){
    int i, j, len, flag = 0;
    i = j = 0;  

while(s[j]){
    if(s[j] != ' '){
        if(flag == -1 && i > 0){
            s[i++] = ' ';
        }
        s[i++] = s[j++];
        flag = 1;
    }else{
        j++;
        flag = -1;
    }
}
s[i] = '\0';

reverse(s, 0, i-1);

len = i;
i = 0;
for(j = 0; j <= len; j++){
    if(s[j] == ' ' || s[j] == '\0'){
        reverse(s, i, j-1);
        i = j+1;
    }
}

return s;

}
```

