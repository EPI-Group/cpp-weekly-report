7 。反向整数  
给定32位有符号整数，整数的反向数字。

例1：

输入： 123  
 输出： 321  
例2：  

输入： -123  
 输出： -321  
例3：

输入： 120  
 输出： 21  
注意：  
假设我们正在处理的环境中，其只能在32位带符号整数的范围内存储的整数：[-2 31 2 31  - 1] 出于此问题的目的，假设当反向整数溢出时，函数返回0。  

    int reverse(int x) {
     bool negative = false;
     if(x<0){
        negative = true;
        x = -x;
     }
     int nums = 0;
     int tmpNum;
     int tmp;
     int i;
     while(x){
         tmpNum = nums;
         tmp = 0;
         for(i = 0;i<10;i++){
            tmp = tmp+tmpNum;
            if(tmp<tmpNum)
                return 0;
         }
         nums = tmp;
         nums=nums+x%10;
         x = x/10;
     }
     if(negative)
        return -1*nums;
     return nums;
	}