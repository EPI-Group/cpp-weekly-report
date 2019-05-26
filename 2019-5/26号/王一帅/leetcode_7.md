给定两个以字符串形式表示的非负整数 `num1` 和 `num2`，返回 `num1` 和 `num2` 的乘积，它们的乘积也表示为字符串形式。

**示例 1:**

```
输入: num1 = "2", num2 = "3"
输出: "6"
```

**示例 2:**

```
输入: num1 = "123", num2 = "456"
输出: "56088"
```

**说明：**

1. `num1` 和 `num2` 的长度小于110。
2. `num1` 和 `num2` 只包含数字 `0-9`。
3. `num1` 和 `num2` 均不以零开头，除非是数字 0 本身。
4. 不能使用任何标准库的大数类型（比如 BigInteger）**或**直接将输入转换为整数来处理。



```c
char * multiply(char * num1, char * num2){
    int* sum = (int*)calloc(220, sizeof(int));
    if(num1 == NULL || num2 == NULL || num1[0] == '0' || num2[0] == '0') {
        char* result = (char*)calloc(2, sizeof(char));
        result[0] = '0';
        return result;
    }
    int l1 = strlen(num1);
    int l2 = strlen(num2);
    int i = 0, j = 0, t = 0, index = 0;
    for(i = 0; i < l1; i++) {
        for(j = 0; j < l2; j++) {
            sum[i + j] += (num1[i] - '0') * (num2[j] - '0');
        }
    }
    for(i = l1 + l2 - 2; i >= 0; i--) {
        sum[i] += t;
        if(sum[i] >= 10) {
            t = sum[i] / 10;
            sum[i] = sum[i] % 10;
        }
        else
            t = 0;
    }
    int len = 2 + (t ? l1 + l2 - 1 : l1 + l2 - 2);
    char* result = (char*)malloc(len * sizeof(char));
    if(t)
        result[index++] = '0' + t;
    for(i = 0; i <= l1 + l2 - 2; i++)
        result[index++] = sum[i] + '0';
    result[index] = 0;
    free(sum);
    return result;
}
```

