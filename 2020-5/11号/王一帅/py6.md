```python
# 密钥格式化

S = input("please input the string: ") #存储密钥字符串
K = int(input("please the k: "))       #存储数字K
S_change = []
S_turn = []
count = 0

#去除'-'
for i in range(len(S)):
    if S[i] != '-':
        S_change += S[i]

S_change.reverse()                     #反转list便于插入'-'

#根据所给参数，添加'-'
for j in range(len(S_change)):
    S_turn += S_change[j]
    count += 1
    if count == K and j != len(S_change)-1:
        S_turn += '-'
        count = 0

S_turn.reverse()                       #把list反转回来

print(''.join(S_turn).upper())         #输出格式化后的密钥
```

```python
# 旋转函数
print("please input the member of array: ")
A = [int(n) for n in input().split()] #存储数组A
answer = []

# 求BK数组
def Bk(x):
    temp = []
    for i in range(int(len(A))):
        a = -(x % int(len(A)))
        temp.append(A[a])
        x -= 1
    return temp

#旋转函数
def f(y):
    temp = 0
    for n in range(int(len(A))):
        temp += n*Bk(y)[n]
    return temp

#把旋转函数各个值输入到answer list里
for j in range(int(len(A))):
    answer.append(f(j))

print("The biggest number is ", max(answer)) #输出所求值
```

```python
#密码宝盒

#定义两个字典用于存储每个进制中所含有的全部基本数字，切记不能忘记包含'0'
dict_1 = {'0':'0','1':'1','2':'2','3':'3','4':'4','5':'5','6':'6','7':'7','8':'8','9':'9',
      '10':'A','11':'B','12':'C','13':'D','14':'E','15':'F'}
dict_2 = {'0':'0','1':'1','2':'2','3':'3','4':'4','5':'5','6':'6','7':'7','8':'8','9':'9',
           'A':'10','B':'11','C':'12','D':'13','E':'14','F':'15'}

#该函数用于进行进制转换
def turn(n,x):
    a = []
    b = []
    while True:
        n1 = n // x
        n2 = n % x
        b.append(n2)
        if n1 == 0:
            break
        n = n1
    b.reverse()
    for i in range(len(b)):
        a.append(str(b[i]))
    return a

#进行操作，输入对应参数
T = int(input("please input the T(T<=500) which is the number of test data: "))
while T:
    C = int(input("please input the C , it decides the formats of password: "))
    n = input("please input the N , the password should be an integer multiple of it: ")      
    M = list(input("input the number(input all of them at one time): "))
    
    #吧list中的' '去掉，以免在下面与字典进行匹配时出现问题
    while ' ' in M :       
        M.remove(' ')
    for i in range(len(M)):
        M[i] = dict_2[M[i]]
    
    i = 1
    N = int(n)
    while len(str(n)) <= 500:                #密码位数不应超过500位，用输入的十进制整数进行限制
        cv = 1
        n = turn(N*i,C)       
        for char in n:       
            if char not in M :               #比较测试数字进行c进制后是否与初始数组相匹配
                cv = 0
        if cv == 1:
            for i in range(len(n)):     
                n[i] = dict_1[n[i]]
            end = ''.join(n)
            print(end)
            break
        i += 1
    if len(str(n)) > 500:      
        print("So sorry !")
    
    T -= 1                                   #一次测试数据运行完，循环减一
```

```python
#基因编码

n = list(input("please input the string(0-1): "))#输入

#定义函数按照ABC编码规则进行编码
def f (n):
    A,B = 1,1
    j = len(n)
    for i in n:
        if i == '0':
            B = 0
        if i == '1':
            A = 0
    if A == 1:
        return 'A'
    if B == 1:
        return 'B'
    return 'C' + f(n[:j//2]) + f(n[-j//2:])

print("After ABC coding: ",f(n))
```

```python
#法雷数列

from fractions import Fraction          #从fractions库中引入Fraction类

def judge(x, y):                        #该函数用于求分子与分母的最大公因数
    while y:                            #进而判断分子与分母是否可以约分
        temp = x % y                    #若返回为1， 则证明分子与分母之间不可约分
        x = y
        y = temp
    return x

n = int(input("please input the n: "))  #输入n值，确定法雷数列的n级
fl = ['0/1']                            #该字典d用于存储法雷数列
a = []
b = []

for i in range(n+1):
    a.append(i)

for i in a[2:]:
    for j in range(i):
        if j == 0:                      #分母不能是0
            continue
        if judge(i,j) == 1:
            b.append(Fraction(j,i))

b=sorted(b)                             #排序

for k in b:
    fl.append(str(k))
fl.append('1/1')

print("Farley series: ",fl)             #输出法雷数列
```

```python
#折叠加密

import copy

t = input("Encrypt(0) or decrypt(1) ?: ")                         #输入判断是加密还是解密
n = [list(input("please input the n(len(n) == pow(2,k): "))]      #存储需要折叠的数组
#加这个[]是为了避免temp不能调用方法reverse()
reg = list(input("please input the reg(len(reg) == k): "))        #存储数组reg

def left(n):
    n1 = copy.deepcopy(n)
    n2 = []
    lh = int(len(n[0])/2)
    lb = int(len(n))
    i = 0
    while i < lb:
        temp = n[i][0:lh]
        temp.reverse()
        n2.insert(0, temp)
        del n1[i][0:lh]
        i += 1
    return n2 + n1

def right(n):
    n1 = copy.deepcopy(n)
    n2 = []
    lh = int(len(n[0])/2)
    lb = int(len(n))
    i = 0
    while i < lb:
        temp = n[i][lh:]
        temp.reverse()
        n2.insert(0, temp)
        del n1[i][lh:]
        i += 1
    return n2 + n1

for i in reg:
    if i == '0':
        n = left(n)
    else:
        n = right(n)

if t == '0':
    for i in range(len(n)):
        print(''.join(n[i]),'\n')
else:
    n = n[::-1]
    for i in range(len(n)):
        print(''.join(n[i]),'\n')
```

