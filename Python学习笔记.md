# <center>Python学习笔记</center>

### <center>第一章 Python语言概述</center>

#### 1.1 Python语言简介

1. 特点：自由软件、设计哲学“明确、简单、优雅”、具有丰富的资源库等

2. IDE：IDLE、Pycharm、Spyder、Jupyter、Python Tutor
3. 选择Python 3版本
4. 使用：

   + 交互式：>>>后输入

   + 文件式：file->new file->save（保存）->run->run mode

#### 1.2 标识符和变量

​	1.标识符由字母、数字、下划线组成（Python 3可以有中文），不能以数字开头

​	2.关键字不能做标识符；关键字也区分大小写，如True是关键字，而true不是。py是大小写敏感的

​	3.字符串也可以做常量，如“hello”

​	4.变量不需要先定义或者声明，属于动态类型语言，可对变量多次赋值且赋值的数据类型可以不一样，可用type()查看数据类型

​	5.特别的，如果对一个有函数功能的函数名赋值，赋值之后函数功能消失

​		如sum([1,2,3])=6;

​			sum=5后，求和功能消失，再用的话会报错

​			解决：del (sum)  		（del是删除函数）

​		因此，不要用python的内置函数作为变量

​	6. id()函数显示变量地址

```python
a=1
b=1
id(a)
id(b)
```

​		会发现a,b内存地址一样，因为python中对变量进行赋值是建立变量和值之间的指向关系

​		再输入```id(1)```，发现和上面的```id(a)``` ```id(b)```一样

```python
而
a=1000
b=1000
id(1000)
id(a)
id(b)
```

​		```id(a)``` ```id(b)``` ```id(1000)```不一样

​		原因是python解释器会把小整数(-5~256)存放在小整数对象池中，不需要对这些对象再次进行内存分配

​		对于大整数和其他类型变量，会随机分配内存空间

#### 1.3 输入函数与输出函数

1.输入函数input()

​	内置函数，从键盘中读入__字符串__,若想输入其他类型——强制类型转换，如int(input())

```python
>>>st=input()
hello   #输入的
>>>st
'hello'

>>>a=input()
123
>>>a
'123'
>>>type(a)
<class 'str'>

>>>a=int(input())
123
>>>a
123
>>>type(a)
<class 'int'>
```

输入多个整数

```python
>>>a,b= input().split()
12 34
>>>a
'12'
>>>b
'34'
```

输入前有提示语

```python
>>>n=int(input(“请输入一个整型值：”))
```

2.输出函数print()

```python
>>>print("hello")
>>>print(a)
>>>print(a,b)  //两个值

>>>for i in range(5):
    print(i)
#输出
0
1
2
3
4
>>>for i in range(5):
    print(i,end=' ')
#输出
1 2 3 4 5 
```



### 第二章 用Python语言编写程序

#### 2.1 数字类型

1. 整数

+ 与数学中整数概念一致，不像c那样有范围

* 可正可负
* 默认情况下采用十进制

| 进制     | 前导符 | 示例 | 十进制 |
| -------- | ------ | ---- | ------ |
| 二进制   | 0b/0B  | 0b10 | 2      |
| 八进制   | 0o/0O  | 0o10 | 8      |
| 十六进制 | 0x/0X  | 0x10 | 16     |

2. 浮点数

+ 与数学中实数概念一致
+ 取值范围和精度有限制
+ 小数：1.23 3.14 -1.22

​		科学计数法：1.23e9   1.21e-5

+ 运算存在不确定尾数，有误差。保留小数：round(0.1+0.1,2)保留两位

3. 复数

+ 与数学中复数概念一致  a=complex(1,2)
+ 虚部用j表示  a             (1+2j)

4. 运算符

+ 加+，减-，乘*，浮点数除/,整数除//，求余%,求幂**

​	(3/2=1.5,3//2=1,-3//2=-2(和c不一样) __向左取整__)

​	(3%2=1   ,3.2%1.5=0.2000000000000000000000018)

​	(2**3=8)

+ 使用方法：import math->math.函数名

  | 函数或常数  | 功能                                     |
  | ----------- | ---------------------------------------- |
  | e           | 自然常数                                 |
  | pi          | 圆周率                                   |
  | log(x,base) | 返回以base为底的对数，缺省为e            |
  | pow(x,y)    | 返回x的y次方                             |
  | sqrt(x)     | 返回x的平方根                            |
  | fabs(x)     | 返回x的绝对值                            |
  | round(x,n)  | 返回浮点数x的四舍五入值，n代表保留的位数 |
  | divmod(x,y) | 返回x和y的商和余数                       |



#### 2.2 字符串

1. Python没有单字符类型，所有字符都被当做字符串，字符串是以引号括起来的任意文本

2. 单引号‘abc’   双引号“hello”   三引号“’hello 

​																	world”‘（可以表示多行文本）

3. 转义字符

| \    | 反斜杠符号                                   |
| ---- | -------------------------------------------- |
| \\'  | 单引号                                       |
| \\"  | 双引号                                       |
| \a   | 响铃                                         |
| \b   | 退格                                         |
| \n   | 换行                                         |
| \v   | 纵向制表符                                   |
| \t   | 横向制表符                                   |
| \r   | 回车                                         |
| \f   | 换页                                         |
| \ooo | 最多三位八进制，如\12表示换行                |
| \xyy | 十六进制数，yy代表的字符，例如：\x0a代表换行 |

4. 字符串运算符

| 运算符 | 功能       | 示例                                                        |
| ------ | ---------- | ----------------------------------------------------------- |
| +      | 连接字符串 | >>>'hello'+'world'------>'helloworld'（只能在字符串间进行） |
| *      | 复制字符串 | >>>'ab'*3------->'ababab'                                   |

5. 字符串切片

+ 字符串是一个有序序列，正向递增/负向递减

0 1 2 3 4 5 6 7							-8 -7 -6 -5 -4 -3 -2 -1 

+ 索引：在[]中给出序号
+ 切片：在[]中给出切片序号范围

如

```python
s="abcdefgh"
s[0]='a'
s[-1]='h'
s[1:5]='bcde'
```

6. 布尔值

+ True 、False

7. 关系运算

| 运算符 | 表达式 | 含义       | 实例             | 结果  |
| ------ | ------ | ---------- | ---------------- | ----- |
| ==     | x==y   | x等于y     | "ABCD"=="ABCDEF" | False |
| !=     | x!=y   | x不等于y   | "ABCD"！="abcd"  | True  |
| >      | x>y    | x大于y     | "ABC">"ABD"      | False |
| >=     | x>=y   | x大于等于y | 123>=23          | True  |
| <      | x<y    | x小于y     | "ABC"<"DEF"      | True  |
| <=     | x<=y   | x小于等于y | "123"<="23"      | True  |

另外，关系运算连在一起：

+ 1<3<5等价于1<3 and 3<5
+ 3<5>2 True
+ 1>6<8 False
+ 'Hello'>'world'  ascii('H')=72<ascii('w')=119   False
+ 字符串和数字不能比较

8. 逻辑运算

```and运算```   ```or运算```   ```not运算```

例：3>5 and a>3 #注意，此时a未定义。  输出False

​		3>5 or a>3 NameError. name 'a' is not defined 短入原则

​		not 3----->False

​		not 0----->True

9. 优先级和结合性

\*\*从右向左：  例如2\*\*3**2=512



#### 2.3 内置转换函数

1. 类型转换

```bool()```   ```float()```   ```complex()``` ```str()```   ```int()```  ```list()```

* bool('str')    True
* float(3)  3.0
* complex(1,2)  (1+2j)
* str(123)      '123'
* list('abcd')     ['a','b','c','d']
* int(x[,base=10])
* + int()   #不传入参数时，结果0
  + int("02")    2（去掉0）
  + int("    35   ")   35 (去掉空格，但3、5不能分开)
  + int("35",8)=29  （八进制）

2. ord函数和chr函数

ord('a')  #ASCII码值 ->97

ord('中') #汉字‘中’的Unicode码 ->20013

chr(97) #参数类型为整数  ->‘a’

3. bin函数，oct函数，hex函数

bin函数——二进制、oct函数——八进制、hex——十六进制



#### 2.4 基本语句

##### 2.4.1 赋值语句

1. 基本形式：变量=值

2. 序列赋值 x,y=4,8   ------>x等于4,y等于8

​						x,y="ab"------>x='a',y='b'

​		变量交换：a,b=b,a

3. i,j=[1,2,3]报错

​		i,*j=[1,2,3]  ------>i=1,j=[2,3]

4. 支持多变量赋值 a=b=c=5

​		结果a=5,b=5,c=5

##### 2.4.2 if语句

```Chinese
if 逻辑表达式:
	语句块1
else:
	语句块2
```

例：判断奇偶数

```python
x = int(input())
if x%2==0:
    print("这是个偶数")
else:
    print("这是个奇数")
```

##### 2.4.3 for语句

```
for variable in 列表:
	语句块 
```

例如：

```python
for i in [1,2,3,4]:
    print(i)
```

range函数

```python
range(start,stop,step)
start:默认从0开始
stop:到stop结束，但是不包括stop
step:步长，默认为1
```

```python
list(range(10))
[0,1,2,3,4,5,6,7,8,9]
list(range(1,10))
[1,2,3,4,5,6,7,8,9]
list(range(1,10,4))
[1,5,9]
list(range(0,-10,-1))
[0,-1,-2,-3,-4,-5,-6,-7,-8,-9]
```

```python
求1+2+...+n的和
n=int(input())
result=sum(list(range(1,n+1)))
print(result)
```

```python
求n!
n=int(input())
f=1
l=list(range(1,n+1))
for i in l:
    f=f*i
```

##### 2.4.4 列表推导式

1.列表

​	python中最常用的数据类型之一：

+ 由零个或多个元素组成，元素之间用逗号隔开，整个列表被方括号包裹
+ 元素类型可以相同也可以不同
+ 通过序号可以引用列表中的元素
+ 支持加法、乘法、比较、索引、切片等

```
[1,2,3]+['c','java','python']->[1,2,3,'c','java','python']
[1]*10 ->[1,1,1,1,1,1,1,1,1,1]
[1,2,3]<[2,3,4] True
```

2.列表推导式

+ 简明扼要的方法创建列表
+ 将循环和条件判断相结合

+ 基本格式 ：n1=[2*number for number in [1,2,3,4,5]]

​							n1=[2,4,6,8,10]

```python
n1=[number for number in range(1,8)]
n1=[1,2,3,4,5,6,7]
n1=[number for number in range(1,8) if number%2 == 1]
n1=[1,3,5,7]
```

```python
求1+1/2+1/3....1/20
a=sum([1/i for i in range(1,21)])
print(a)
```

```python
求1-1/2+1/3-1/4+...前n项和
n=int(input())
a=sum([1/i if i%2==1 else -1/i for i in range(1,n+1)])
```

```python
6+66+666......（生成：'6'*i for i in range (1,n+1)）
n=int(input())
[int('6'*i) for i in range(1,n+1)]
sum([int('6'*i) for i in range(1,n+1)])

```

#### 2.5 格式化输出

```python
华氏-摄氏温度转换表
lower,upper=input().split()
lower,upper=int(lower),int(upper)
for i in range(lower,upper+1,2):
    print(i,"{:.1f}".format(5*(i-32)/9))
```

format()函数

1. 基本格式：str.format()

```python
x=3.14159
y=2*x*3
print("{0:.2f} {1:.2f}".format(x,y))
```

```python
1-2/3+3/5-4/7.....
一、
n=int(input())
result=0
for i in range(1,n+1):
    if i%2==1:
        result = result + i/(2*i-1)
    else:
        result = result - i/(2*i-1)
print("{:.3f}".format(result))
二、
n=int(input())
alist=[i/(2*i-i) if i%2==1 else -i/(2*i-i) for i in range(1,n+1)]
result=sum(alist)
print("{:.3f}".format(result))
```



### 第三章 使用字符串、列表和元组

#### 3.1 序列的访问及运算符

##### 3.1.1 序列类型容器

1. 容器：序列容器---字符串、列表

​			非序列容器

2. 加法、乘法：不会改变容器本身
3. 某一元素是否在容器中？

```python
s1='123'
'12' in s1---->True
'4' in s1---->False
'4' not in s1---->True
t1=[1,2,3]
1 in t1---->True
[1,2] in t1---->False??????????
[1,2] in [[1,2],3]---->True
```

##### 3.1.2 取单个元素

1.用方括号[]取得列表中单一元素

```python
>>>[1,2,3,4,5][4]
5
>>>"this is a string"[6]
s
如果越界：
>>>t1=[1,2,3]
>>>t1[3]
Error!!!

>>>t1[-1]
3
```

2.修改列表的某元素（字符串不可以）

```python
>>>t1=[1,2,3]
>>>t1[0]
1
>>>t1[0]=4
>>>t1
[4,2,3]
```

##### 3.1.3 字符串和列表切片

[2:6]是在2,6号前面各切一刀

```python
'26C'[0:-1]---->'26'
'8c'[:-1]---->'8'
```

```python
切一段
'zhejiang'[:3]---->'zhe'
'zhejiang'[3:8]------>'jiang'(虽然8号不存在，但是切片的时候可以这么做)
'zhejiang'[3:]------>'jiang'(冒号后面不写，取到结尾)
```

##### 3.1.4 序列的函数

1. len() 求序列的长度——有多少个元素

最后一个元素t1[-1]或t1[len(t1)-1]

2. min()、max()——获取列表中最大、最小的元素



#### 3.2 使用字符串

##### 3.2.1 字符串再认识

字符串内有单/双引号

+ 字符串里有单引号---->外面用双引号
+ 使用转义字符\\'  \\"   
+ 三引号'''---->多行表达一个字符串

```python
一、>>>s='''this
is
a
 string
'''
>>>s
'this\nis\na\n string'
>>>print(s)
this
is
a
 string
    
```

```python
#另一种多行表达的方法：结尾加\(但是前后是紧紧连接的)
>>>s = 'this\
is\
a\
 string.\
 '
>>>s
'thisisa string.'
>>>print(s)
'thisisa string.'
```

r：字符串原样输出，\不被当成转义字符的前缀

```python
>>>s=r'this\nis\na\ntest/'
>>>s
'this\\nis\\na\\ntest/'（\\就是\）
>>>print(s)
this\nis\na\ntest/
```



##### 3.2.2 字符串函数

\* 字符串本身不变

1. lower()将字母变成小写

```python
>>>s='John Smith'
>>>s
'John Smith'
>>>s1=s.lower()
>>>s1
'john smith'
>>>s
'John Smith'（原字符串不变）
```

2.  find()在字符串中找子字符串的位置

```python
>>>s.find('hn')
2
>>>s.find('aa')
-1（代表没找到）

>>>'hello world'.find('l')
2（找的是第一次出现的位置）
>>>'hello world'.find('l',3)
3（从3开始找）
>>>'hello world'.find('l',4)
9
```

3. count()找字符（串）出现次数

```python
>>>'hello world'.count('l')
3
>>>'hello world'.count('lo')
1
```

4. strip()去掉两端空格

```python
>>>s = '   hello world   '
>>>s.strip()
'hello world'（两边空格都去掉）
>>>s.rstrip()
'   hello world'(去掉右边空格)
>>>s.lstrip()
'hello world   '（去掉左边空格）
```

5. replace()替换

```python
>>>s=' hello world '
>>>s.replace(' ','-')
'-hello-world-'
>>>s.replace(' ','--')
'--hello--world--'
>>>s.replace(' ','')
'helloworld'
```



##### 3.2.3 字符串和数字之间的转换

1.str()函数

```python
>>>str(123)
'123'
```

2.有一定格式

```python
>>>'I am %d years old and weight %d kg' % (18,50)
I am 18 years old and weight 50 kg
>>>'it is %.1fC'%30.5123
'it is 30.5'
>>>'it is %.1fC'%30.565
'it is 30.6'（四舍五入）
>>>'I am %10d years old' % 18
'I am         18 years old'
```



#### 3.3 列表的使用

##### 3.3.1 基本的列表操作

1. 运算

```python
>>>a=6
>>>b=8
>>>t=[a+2,b-a]
>>>t
[8,2]
```

2. list()函数

```python
>>>t=list('this is a string')
>>>t
['t', 'h', 'i', 's', ' ', 'i', 's', ' ', 'a', ' ', 's', 't', 'r', 'i', 'n', 'g']
```

3. 广义表

```python
t=[[1,2,3],[4,5,6],[7,8,9]]
>>>len(t)
3
>>>t[0]
[1,2,3]
>>>t[0][0]
1
```

4. 两个列表变量

```python
>>> t1=[1,2,3]
>>> t2=t1
>>> t2
[1, 2, 3]
>>> t2[0]=0
>>> t2
[0, 2, 3]
>>> t1
[0, 2, 3]
可以看出，列表变量中，t2=t1是管理权的授予
```

```python
若要创造t2一个新的列表(和t1无关)，可以
t2=t1[:](做切片)

```

5. del()删除列表元素



##### 3.3.2 列表的函数

1. append()   往列表后增加一个元素

​		extend()  往后面拼列表

```python
t1.append(5)
t1.extend([7,8,9])

t2.append([4,5])---->直接将列表作为一个元素插入到最后
```

2. insert()插入

​		remove()删除值为多少的元素

```python
t1.insert(1,9)----->在原来1号位前面加9
t2.insert(100,-1)------>100超过列表元素个数的时候，会做append的动作
```

3. pop()删除最后一个，同时返回最后一个

​		pop(2)删除2号位置元素并将它返回，相当于弹出

4. reverse()颠倒字符串中所有元素
5. index()查找某一元素在列表中第一次出现的位置



##### 3.3.3 列表和字符串之间的操作

1. split()函数——分隔

```python
>>> s='this is a test'
>>> s.split()
['this', 'is', 'a', 'test']

>>> s='12:35'
>>> s.split(':')  //用于决定用什么来分割
['12', '35']

>>> s='12::35'
>>> s.split('::')
['12', '35']
>>> s.split(':')
['12', '', '35']  //中间会自动加一个空格
```

2.join()

```python
>>> s='this is a test'
>>> t=s.split()
>>> t
['this', 'is', 'a', 'test']
>>> ' '.join(t)
'this is a test'
```



#### 3.4 元组的使用

1. 元组：自变量用圆括号；不可修改
2. 会对列表本身进行修改的函数，元组不能用
3. 有被逗号分割的量，天生会被认为是元组

#### 3.5 Python随机模块

1. sort()函数——>排序（改变原列表）

```python
>>> t=[1,2,5,7,8,6,10]
>>> t.sort()
>>> t
[1, 2, 5, 6, 7, 8, 10]
>>>
```

2. import random->random.shuffle()——>随机排列

```python
>>> import random
>>> random.shuffle(t)
>>> t
[2, 8, 1, 6, 5, 10, 7]
>>> random.shuffle(t)
>>> t
[8, 2, 7, 1, 10, 5, 6]
```

3. random.choice()——>找出一个

````python
>>> random.choice(t)
1
>>> random.choice(t)
6
````

4. random.random()——>返回0-1的浮点数

​		random.randint(1,100)——>返回1-100的整数

​		random.seed()——>种子，给出一个确定的seed值，就会生成固定的随机数



### 第四章 条件、循环和其他语句

#### 4.1 条件语句

1. if-else语句

```python
if 条件表达式:
    表达式1
    ...
else:
    表达式2
    ...
```

+ 注意缩进
+ 嵌套的if-else

2. elif——级联的if语句

```python
if x>0:
    y=1
elif x==0:
    y=0
else:
    y=2*x+100
```



#### 4.2 while循环

```python
while True:(无穷循环)
```

```python
#求平均值，以输入-1结束
s=0
cnt=0
while True:
    if x!=-1:
    	x=int(input())
    	s+=x
    	cnt+=1
    else:
        break   #使用break离开循环
if cnt>0:
    print(s/cnt)
else:
    print(0)
```



#### 4.3 for循环

```python
#判断素数
方法一：
x= int(input())
isprime = True
for i in range(2,x):
    if x%k==0:
        isprime = False
        break
if isprime:
    print('is prime')
else:
    prinf('is not prime')

方法二：    
x= int(input())
for i in range(2,x):
    if x%k==0:
        break
else:
    print('isprime')   ##for循环的else，for正常结束else执行，否则不执行
```

```python
#嵌套for循环,求m，n间素数的和
m,n=map(int,input().split)
s=0
cnt=0
for x in range(m,n+1):
    for k in range (2,x):
        if x%k==0:
            break
    else:
        cnt+=1
        s+=x
print(cnt,s)
```



#### 4.4 range函数

1. range(5)——>0,1,2,3,4
2. range(2,10)——> 2,3,4,5,6,7,8,9
3. range(2,20,2)——>2,4,6,8,10,12,14,16,18



#### 4.5 异常

1.try、except（如有异常，进入except而不是终止）

```python
x=int(input())
t=[1,2,3,4,5]
try:
    print(t[x])
except:
    print('x is not a valid index') 
```

```python
try:
    语句块1
except 异常类型1:
    语句块2
except 异常类型2:
    语句块3
    ...
except 异常类型N:
    语句块N+1
except:
    语句块N+2
else:
    语句块N+3(try里没有异常，try完运行else，类似于循环)
finally:
    语句块N+4(无论有没有异常，都要运行finally)
```

![image-20230116122702291](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230116122702291.png)





### 第五章 集合与字典

#### 5.1 集合

1. 集合用大括号{}，元素不重复，是无序的容器（顺序不能由程序员指定）

```python
>>> s={1,2,3,3,4}
>>> s
{1, 2, 3, 4}
>>> s={1,2,5,3,4}
>>> s
{1, 2, 3, 4, 5}
```

2. 增加元素s.add()

```python
>>> s.add(0)
>>> s
{0, 1, 2, 3, 4, 5}
>>> s.add(3)
>>> s
{0, 1, 2, 3, 4, 5}  #如果加的数据已经存在，那再加相当于没做
```

3. 集合创建set()——把列表转换成集合

```python
>>> t=[1,3,2,5,4]
>>> s1=set(t)
>>> s1
{1, 2, 3, 4, 5}
```

4. 空列表[],空元组(),空字符串''.......{}字典，空集合set()

```python
>>> type({})
<class 'dict'>
>>> type(set())
<class 'set'>
```

5. 其它函数:add(),remove()——添加和删除

​		min(),max(),len(),sum()

​		但不能像列表那样通过下标访问集合元素

​		可以遍历集合中所有的元素

​		in、not in也可以使用

​		还可以用==判断两个集合是否相等，>、<判断大小（真子集关系）

6.    ```|```并集，```&```交集（若交集为空，则显示set()），```^```对称差集——两个集合作并集，去掉交集的成分

​		```-```差集（s1-s2:s1里有而s2没有的） 



#### 5.2 字典

1. 基本操作

```python
>>>d={'one':1,'two':2}
>>>d['one']——方括号
1
>>>d['two']
2
>>>d['three']
异常
```

```python
>>>d['three']=3
>>>d['three']
3
```

2. 字典的基本运算

+ 删除 del

```python
>>>del d['two']
>>>d
{'one':1,'three':3}
```

+ 遍历 for——遍历字典中的key，再去获取对应的值

```python
>>>for name in d:
    	print(d[name])
1
3
>>>for name in d:
    	print(name)
one
three
```

+ 修改

```python
>>>d['one']=11
>>>d
{'one':11,'three':3}
```

+ len()——获得字典条目
+ min()/max()——获取最小/大的key（比较的是名字字符串），因此没有sum()

+ 另一种访问方式

```python
>>>d.get('one')
11
```

对于d中没有的元素

```python
>>>d['ok']
异常
>>>d.get('ok')
（无结果）
>>>d.get('ok',0)
0
```

d.get('ok',0)的妙用

```python
x=int(input())
if x != -1:
    d[x]=d.get(x,0)+1
```

此时若d[x]存在，则取出来直接加；若不存在，则会返回0，起到建立d[x]的作用



#### 5.3 集合与字典的应用☆

例：处理学生成绩

```python
#输入
stuid = {} #建立字典
stuscore = {}
course = set() #表示成绩的空集合
while True:
    line = input()
    if line == 'END':
        break
    s = line.split(',')
    if len(s) == 2:
        stuid[s[0]] = s[1]  #s中第一个元素和第二个元素对应，即学号和姓名对应
    elif len(S) == 3:
        #s[0] = ['3190101234','微积分',95]
        d = stuscore.get(s[0],{})
        d[s[1]] = int(s[2])
        course.add(s[1])

d = stuscore[id]
for k in score#course:
    if k in d:......
```



### 第六章 函数

#### 6.1 函数定义与调用

1. 内置函数不用定义，直接调用
2. 定义：

```python
def 函数名(参数表)：
	函数体
```

```python
定义函数y=x^2+1
def f(x):
    value = x**2+1
    return value
```

```python
调用f(x)
n=int(input())
y=f(x)
print(y)
```

3. 求斐波那契数列前n项

```python
def fibs(n):
    result=[1,1]
    for i in range(n-2):
        result.append(result[-2]+result[-1])
    return result  #函数定义
```

4. 函数要先定义再调用
5. lambda表达式：定义一个匿名函数

```python
g = lambda x,y,z:x+y+z
#把lambda定义的匿名函数赋给函数g
print(g(1,4,5))
```



#### 6.2 函数参数

1. 位置参数：传入参数的值按顺序依次赋给形参
2. 关键字参数：调用参数时可以指定对应形式参数的名字，如```def dis(x1,y1,x2,y2)``` 、```dis(x1=1,y2=5,y1=3,x2=4)```

+ 位置参数和关键字参数混合——先写位置参数，再写关键字参数，否则会出错

3. 默认值参数：当调用方没有提供对应形式参数的值时，可以指定默认形式参数值（定义时）。如果提供了实参，调用时会代替默认值

```python
def init(arg,result=[]):
    result.append(arg)
    print(result)
init('a')
init('b')
init(1,[1])

['a']
['a', 'b']  #默认值参数不再重新创建
[1, 1]
```

4. 数量可变参数

+ 当函数参数数目不确定时，*将一组可变数量的位置参数集合成参数值的元组

```python
def countnum(a,*b):
    print(b)
    print(len(b)+1)
countnum(3,7,9)
countnum(5,8,1,6,89)

结果：
(7,9)
3
(8,1,6,89)
5
```

+ **收集参数到字典中

```python
def countnum(a,**d):	#计算参数个数
    print(d)
    print(len(d)+1)
countnum(3,x1=9,x2=1,x3=6,x4=89)

结果：
{'x1':9,'x2':1,'x3':6,'x4':89}
5
```

5. print()函数的完整表示

```python
print(*object,sep=" ",end="\n",file=sys.stdout)
object:输出参数，可变数量
sep=" ":输出分隔符
end="\n":输出函数结束换行
file=sys.stdout:输出到屏幕缺省
```

6. 实参拆包，调用时参数前加*

```python
>>> l=[2,7,5]
>>> print(l)
[2, 7, 5]
>>> print(*l)
2 7 5
```

7. 可变对象和不可变对象当参数时

+ 当实参是不可变对象时，形参值改变不会影响实参
+ 当实参是可变对象时，形参值改变可能会影响实参

```python
def change(a,b):
    a=3
    b=b+a
x,y=7,9
change(x,y)
print(x,y)

结果：7,9  #把实参拷贝到形参中，形参改变不影响原来的实参

def change1(a):
    a[0]=3
    a[1]=11+a[0]
l=[7,9]
change1(l)
print(l)

结果： [3,14]  #拷贝的是实参的地址，形参和实参都是指向这个地址，所以形参改变实参也改变
```



#### 6.3 函数的返回值

1. 函数用return语句返回值，如没有用return语句返回，这时函数返回的值为None；如果return后面没有表达式，返回值也是None；None是Python中一个特殊的值，虽然它不表示任何数据，但仍然具有重要的作用

```python
判断m到n间素数的个数和它们的和
def isprime(i):
    for k in range(2,i):
        if i%k==0:
            return False
	return True

m,n=input().split()
m,n=int(m),int(n)
p=[i for i in range(m,n+1) if isprime(i)]
print(len(p),sum(p))
```

2. 返回值是函数

```python
def test(par):
    return par
def test1():
    return 1000
def test2():
    return 2000
def f(x):
    return {
        'a':test,
        'b':test1,
    }.get(x,test2)
    
print(f('a')(100))
print(f(4)(100))

输出：
100
2000
```

3. 集合add函数的返回值是None

按列表原次序输出非重复元素

```python
l=[2,3,5,8,3,6,8,6,5]
seen=set()
l1=[i for i in l if i not in seen and not seen.add(i)]
print(l1)
输出：[2,3,5,8,6]
```



#### 6.4 命名空间和作用域

1. 变量可被访问的范围称为变量的作用域，也称为变量命名空间或变量名字空间。Python程序用命名空间区分不同空间的相同名字
2. python解释器启动时建立一个全局命名空间，全局变量就放在这个空间，还建立内置命名空间，记录所有标准常量名、标准函数名等。在全局命名空间中定义的变量是全局变量
3. 每一个函数定义自己的命名空间，函数内部定义的变量是局部变量。如果在一个函数中定义一个变量x，在另外一个函数中也定义x变量，因为是在不同的命名空间，所以两者指代的是不同的变量。可以用多种方式获取其他命名空间的变量
4. Python语言规定赋值即定义

+ 全局变量：定义在函数外，作用域是整个程序
+ 局部变量：定义在函数内，作用域是函数内部。形参也是局部变量

5. 在函数中使用全局变量——global关键字

```python
def scope():
    global var1
    var1=1
    print(var1,var2)
var1=10
var2=20
scope()
print(var1,var2)

结果：
1 20
1 20
```



#### 6.5 递归调用

1. 斐波那契数列

```python
def fib(n):
    if n==0 or n==1:
        return 1
    else:
        return fib(n-1)+fib(n-2)
```

改进：已计算的值放到字典中

````python
pre={0:1,1:1}
def fib(n):
    if n in pre:
        return pre[n]
    else:
        newvalue=fib(n-1)+fib(n-2)
        pre[n]=newvalue
        return newvalue
print(fib(100))    
````

2. 求嵌套列表的数值和

```python
def flatten(items):
    lst=[]
    for x in items:
        if isinstance(x,(list,tuple)):
            for element in flatten(x):
                lst.append(element)
        else:
            if type(x)!=str:
                lst.append(x)
    return lst

items=[11,2,[3,7],(68,-1),"123",9]
l=[i for i in flatten(items)]
print(sum(l))
```



#### 6.6 内置函数

1. sorted函数：对字符串，列表，元组，字典等对象进行排序操作（sort应用在list上）

list的sort是对已经存在的列表进行操作，而sorted返回的是一个新的list

```python
语法格式：
sorted(iterable[,key[,reverse]])
iterable——序列：如字符串，元组等
key——函数，缺省为空
reverse——排序规则
reverse=True 降序，=False 升序（默认）
```

```python
>>>students=[('江兴',89,15),('方鹏',85,14),('陈科',80,14)]
>>>print(sorted(students,key=lambda s:s[2]))  #将第3行/第2号行按从小到大排列
```

2. map函数：根据提供的函数对指定序列做映射，返回值是新列表或迭代器

```python
map(function,iterable,...)
function是对参数序列的每一个元素调用function函数，iterable是序列
```

举例

```python
>>>print(list(map(lambda x:x**2,[1,2,3,4,5])))
[1,4,9,16,25]
>>>print(list(map(lambda x,y:x+y,[1,3,5,7,9],[2,4,6,8,10])))
[3,7,11,15,19]
```

3. zip函数：将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表或迭代器

如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同

```python
格式：zip([iterable,...])
```

```python
>>> a=[1,2,3]
>>> b=[4,5,6]
>>> c=[4,5,6,7,8]
>>>
>>> print(list(zip(a,b)))
[(1, 4), (2, 5), (3, 6)]
>>> print(list(zip(a,c)))  #与最短的对象相同
[(1, 4), (2, 5), (3, 6)]
```

字典键值互换

````python
>>>d={'blue':500,'red':100,'white':300}
>>>d1=dict(zip(d.values(),d.keys()))
>>>print(d1)
{500:'blue',100:'red',300:'white'}
````

4. eval和exec函数

Python是一种动态语言，操作合法性检查都在动态运行中检查，运算的代码需要到运行时才能动态确定；程序结构也可以动态变化，容许动态加载新模块等。这两个函数就体现了这个特点

+ eval计算表达式，返回表达式的值
+ exec可运行python程序，返回程序运行结果

```python
>>> x,y=3,7
>>> eval('x+3*y-4')    
20

>>> exec('print("hello world")')    #eval/exec函数内部都是字符串，要加引号
hello world
```

5. all和any函数

+ all、any以迭代的对象作为参数
+ all参数都为True时才返回True，any参数只要有一个为True就返回True

```python
判断素数
>>>n=47
>>>all[1 if n%k!=0 else 0 for k in range(2,n)]
True
```

```python
空列表和0都表示False
>>>any[[],0,False]
False
```



#### 6.7 程序结构

1. ”import 模块名“是执行文件名为模块名的程序
2. ”from 模块名 import *“引入模块中的所有函数，调用时不用再加模块名
3. “from 模块名 import 函数名”引入模块中的单个函数，调用时不用再加模块名



### 第七章 文件

#### 7.1 文件读写操作

1. 计算机文件：二进制文件（图形文件、文字处理程序等）、文本文件
2. 打开文件

```py
textFile=open("7-1.txt","rt") #以文本形式打开，返回文件对象
textFile=open("7-1.txt","rb") #以二进制形式打开
```

open()

+ fileobj=open(filename,mode)
+ 返回文件对象，filename-文件名，mode-文件类型和操作（t-文本文件（可省略）、b-二进制文件）

| 文件打开模式 | 含义                               |
| ------------ | ---------------------------------- |
| "r"          | 只读模式（默认）                   |
| "w"          | 覆盖写                             |
| "a"          | 追加                               |
| "x"          | 创建写（不存在则创建；存在则出错） |
| "+"          | 与r/w/a/x一起使用，增加读写功能    |
| "t"          | 文本                               |
| "b"          | 二进制                             |

3. 文件读写函数

| 名称               | 含义                                                         |
| ------------------ | ------------------------------------------------------------ |
| open()             | 打开文件                                                     |
| read(size)         | 从文件读取size长度的字符串，如果未给定/负则读取所有内容      |
| readline()         | 读取整行，返回字符串                                         |
| readlines()        | 读取整行，返回列表                                           |
| write(s)           | 把字符串s的内容写入文件                                      |
| writelines(s)      | 向文件写入一个元素为字符串的列表，如果需要换行则要自己加入每行的换行符 |
| seek(off,whence=0) | 设置文件当前位置                                             |
| tell()             | 返回文件读写的当前位置                                       |
| close()            | 关闭文件                                                     |

4. 复制文件

```python
source=open("cj.txt","r")
back=open("cjback.txt","w")
s=source.read()
back.write(s)
source.close()
back.close()
```

5. 多行文件读写

```python
for line in f.readlines():
    print(line)

```

6. 输入输出重定向

+ sys.stdin 标准输入
+ sys.stdout 标准输出
+ sys.stderr 标准错误输出

```py
import sys
#从文件输入改变为键盘输入
s=sys.stdin.readlines()
```

#### 7.2 用Pandas模块读写常见格式文件

#### 7.3 数据可视化——plotly模块（4.0版）



### 第八章 类和对象

#### 8.1 类和对象的概念

1. 面向对象程序设计（OOP）：使用对象进行程序设计，实现代码复用和设计复用，使得软件开发更高效方便。

工业界大部分都是面向对象程序设计语言，而C语言是面向过程的程序设计语言，Python是OOP语言

2. 类：类是一种对象的模板和数据类型，它定义了对象的属性（数据），并提供用于初始化对象的初始化程序和操作这些属性的方法（函数）。

```python
class Students:     #Students类
    uname='浙江大学'
    def __init__(self,ino,iname):
        self.no=ino
        self.name=iname
    def getinfo(self):
        print('学校：',Students.uname,',学号：',self.no,',姓名：',self.name)
```

3. 对象：对象是**类**的一个**实例**，使用构造方法来创建一个对象，使用圆点运算符（.）通过引用方法和变量来访问对象的成员。

```python
s1=Students('317000001','zjuzhuang')   #创建一个Students对象s1
s='浙江大学'  #创建一个字符串对象s，等价于s=str('浙江大学')
```

4. 三大特性：封装、继承、多态

#### 8.2 类和对象的创建

1. 定义类 

```py
class 名字:
    #初始化
    #定义方法
```

例如，

```python
class Students:     #Students类
    def __init__(self,ino,iname):   #构造方法，用于创建对象
        self.no=ino    #定义成员变量
        self.name=iname
    def getinfo(self):    #获取对象方法
        print('学校：',Students.uname,',学号：',self.no,',姓名：',self.name)
        
s1=Students('wang','3170000020')   #创建s1对象
s1.getinfo()
```

self作为前缀，在方法里面不作为参数使用，这里与函数不同

2. 创建对象 ：`对象名.成员名`

```py
s1=Students('wang','3170000020')
s1.getinfo()   #使用方法
s1.name     #引用变量
```

3. isinstance测试一个对象是否为某个类的实例

```python
>>>isinstance(s1,Students)
True
>>>isinstance(s1,str)
False
```

4. 访问对象：`对象名.成员名`

```py
>>>s1=Students('wang','3170000020')    #创建s1对象
>>>s1.name                       #name是对象的数据
'wang'

>>>s2=Students('zhang','113')   #创建s2对象
>>>s2.getinfo                   #getinfo()是方法
zhang 113
```

5. 类中的变量必须有初始值，可以初始化成0
6. 变量值的修改：

+ 直接通过对象进行修改（直接赋值）
+ 通过方法进行修改（符合封装）

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230809150406183.png" alt="image-20230809150406183" style="zoom: 73%;" />

#### 8.3 使用对象编写程序

#### 8.4 封装

#### 8.5 继承和多态



### 第九章 Web应用程序开发和网络爬虫

#### 9.1 Web应用程序开发概述

#### 9.2 Web应用框架Flask和文件模板

#### 9.3 云端部署Web应用程序

#### 9.4 网络爬虫

