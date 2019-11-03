9 。回文数  
确定整数是否是回文。当它向前读取向后时，整数是回文。

例1：

输入： 121  
输出： true  
例2：  

输入： -121  
输出： false  
说明：从左到右，它显示为-121。从右到左，它变成121-。因此它不是回文      

例3：  
输入： 10  
输出： false  
说明：从右到左读取01。因此它不是回文。  

```c
bool isPalindrome(int x) {
	int left, right, len=1;
	if(x > INT_MAX || x < 0)		
    	return false;
	while(x/len >= 10)			
    	len *= 10;
	while(x){
    	left = x / len;			
    	right = x % 10;			
    	if(left != right)		
        	return false;
    	x = (x % len) / 10;		
    	len /= 100;			
	}
	return true;
}
```