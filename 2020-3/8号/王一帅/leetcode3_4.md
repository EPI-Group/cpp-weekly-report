给你一个长度为 n 的整数数组 nums，其中 n > 1，返回输出数组 output ，其中 output[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积。

 

示例:

输入: [1,2,3,4]
输出: [24,12,8,6]


提示：题目数据保证数组之中任意元素的全部前缀元素和后缀（甚至是整个数组）的乘积都在 32 位整数范围内。

说明: 请不要使用除法，且在 O(n) 时间复杂度内完成此题。

进阶：
你可以在常数空间复杂度内完成这个题目吗？（ 出于对空间复杂度分析的目的，输出数组不被视为额外空间。）



 * ```c
 /**

	- Note: The returned array must be malloced, assume caller calls free().
	  */
	  int* productExceptSelf(const int a[], int length, int* return_length) {
	  int* mul_a = (int*) malloc(length * sizeof(int));
	  int i = 0, mul = 1, ai;
	  while (1) {
	  	mul_a[i] = mul;
	  	ai = a[i];
	  	if (i == length - 1) {
	  		break;
	  	}
	  	mul *= ai;
	  	i++;
	  }
	  mul = ai;
	  while (1) {
	  	i--;
	  	mul_a[i] *= mul;
	  	if (i == 0) {
	  		break;
	  	}
	  	mul *= a[i];
  }
   *return_length = length;
   return mul_a;
   }
 ```
 
 