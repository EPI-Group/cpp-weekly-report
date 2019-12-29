累加数是一个字符串，组成它的数字可以形成累加序列。

一个有效的累加序列必须至少包含 3 个数。除了最开始的两个数以外，字符串中的其他数都等于它之前两个数相加的和。

给定一个只包含数字 '0'-'9' 的字符串，编写一个算法来判断给定输入是否是累加数。

说明: 累加序列里的数不会以 0 开头，所以不会出现 1, 2, 03 或者 1, 02, 3 的情况。

示例 1:

输入: "112358"
输出: true 
解释: 累加序列为: 1, 1, 2, 3, 5, 8 。1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, 3 + 5 = 8
示例 2:

输入: "199100199"
输出: true 
解释: 累加序列为: 1, 99, 100, 199。1 + 99 = 100, 99 + 100 = 199



```c
void _isAdditiveNumber(char* num, int pos, long pre2, long pre1, int bitNums, int dep, bool* res){

​    if(*res || num[pos] == '\0'){

​        if(dep >= 3){

​            *res = true;

​        }

​        return ;

​    }

​    

​    int i, j;

​    char buf[32];

​    if(pre1 == -1 || pre2 == -1){//第一个数 第二个数 无需满足pre1 + pre2 = cur

​        for(i = 0; num[pos+i] != '\0'; i++){

​            buf[i] = num[pos+i];

​            buf[i+1] = '\0';

​            if(i > 0 && buf[0] == '0'){

​                break;

​            }

​            if(pre2 == -1){//第一个数

​                _isAdditiveNumber(num, pos+i+1, atol(buf), pre1, i + 1 > bitNums ? i + 1 : bitNums, dep+1, res);

​            }else{//第二个数

​                _isAdditiveNumber(num, pos+i+1, pre2, atol(buf), i + 1 > bitNums ? i + 1 : bitNums, dep+1, res);

​            }

​        }

​    }else{

​        for(i = 0; num[pos+i] != '\0'; i++){//第三个数 需要满足pre1 + pre2 = cur

​            buf[i] = num[pos+i];

​            if(i + 1 < bitNums){

​                continue;

​            }

​            if(i + 1 > bitNums + 1 || i > 0 && buf[0] == '0'){

​                break;

​            }

​            buf[i+1] = '\0';

​            long cur = atol(buf);

​            if(cur == pre1 + pre2){

​                pre2 = pre1;

​                pre1 = cur;

​                _isAdditiveNumber(num, pos+i+1, pre2, pre1, i + 1 > bitNums ? i + 1 : bitNums, dep+1, res);

​            }

​        }

​    }

}



bool isAdditiveNumber(char * num){

​    bool res = false;

​    _isAdditiveNumber(num, 0, -1, -1, 0, 0, &res);

​    return res;

}
```

