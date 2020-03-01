比较两个版本号*version1*和*version2*。
如果返回， 则返回，否则返回。`*version1* > *version2*``1;``*version1* < *version2*``-1;``0`

您可以假定版本字符串为非空，并且仅包含数字和`.`字符。

该`.`字符不代表小数点，用于分隔数字序列。

例如，`2.5`不是“两个半”或“到第三版的一半”，它是第二个第一级修订的第五个第二级修订。

您可以将版本号的每个级别的默认修订号假定为`0`。例如，版本号`3.4`的修订号为`3`，`4`其第一级和第二级修订号为。它的第三级和第四级修订号都是`0`。

 

**范例1：**

```
输入： version1 =“ 0.1”，version2=“ 1.1”
 输出： -1
```

**范例2：**

```
输入：version1 =“ 1.0.1”，version2=“ 1”
 输出： 1
```

**范例3：**

```
输入： version1 =“ 7.5.2.4”，version2=“ 7.5.3”
 输出： -1
```

**范例4：**

```
输入： version1 =“ 1.01”，version2=“ 1.001”
 输出： 0
 说明：忽略前导零，“ 01”和“ 001”代表相同的数字“ 1”
```

**范例5：**

```
输入： version1 =“ 1.0”，version2=“ 1.0.0”
 输出： 0
 说明：第一个版本号没有第三级修订号，这意味着其第三级修订号默认为“ 0”
```

```c
int compareVersion(char* version1, char* version2) {
	int lenversion1 = strlen(version1);
	int lenversion2 = strlen(version2);
	int i = 0;
	int j = 0;
	int num1 = 0;
	int num2 = 0;

while (i < lenversion1 || j < lenversion2)
{
	while (i < lenversion1&&version1[i] != '.')
	{
		num1 = 10 * num1 + version1[i]-'0';
		i++;
	}

	while (j < lenversion2 && version2[j] != '.')
	{
		num2 = 10 * num2 + version2[j]-'0';
		j++;
	}

	if (num1>num2)return 1;
	else if (num1 < num2)return -1;
	i++;
	j++;
	num1 = 0;
	num2 = 0;
}
return 0;

}
```

