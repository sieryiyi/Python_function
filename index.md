### 二分查找

#### import bisect

```
bisect.bisect_left([1,2,6,8],7)  # 找出7的合适插入位置或找出7在列表中的哪一个
bisect.bisect_right([1,2,6,8],7)  # 找出位置后+1

```

### 装饰器

#### @functools.lru_cache

写为lru_cache(None)会快很多！！！！！


如果 typed=True，则不同参数类型的调用将分别缓存，例如 f(3) 和 f(3.0)

参数maxsize为最多缓存的次数，如果为None，则无限制，设置为2n时，性能最佳

开拓额外空间，记录函数过往出现过的自变量取值x而算出的函数结果f(x)，当再次遇到相同自变量输入，直接调用算过的结果

### 小根堆

#### import heapq

Python是小根堆，想转大根堆就把元素集体×(-1)

```
heapq.heapify([1,5,3,6])
heapq.heappop()
heapq.heappush([1,5,2,3],7)
heapq.heapreplace([1,5,6,7],4) # 删除最小元素，并添加新的
heapq.heappushpop([1,4,5,6],3) # 比较要添加元素x与最小的堆元素大小，如果大，删除最小堆元素并把x加进去，否则堆不变

```

### 字典API

s.get(key,default)   # 查找关键词key，如果不存在，返回默认值default

能极大 ———— 程度节省时间，对比判断存不存在，再赋值默认值来说

### 正则表达式（用来处理字符串）

import re

https://blog.csdn.net/zhiguigu/article/details/119992775?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165647420416782184623744%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165647420416782184623744&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~top_positive~default-1-119992775-null-null.nonecase&utm_term=python%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F&spm=1018.2226.3001.4450

正则表达式是用在findall()方法当中，大多数字符串检索都可以通过这个方式完成

re.findall(正则表达式，目标字符串)

找不到匹配字符串会返回[]，找到则返回[正则表达式]

#### 1、正则表达式 [ ]

  用来指定一个字符集

  ```
  s = "a123456b"
  rule = "a[0-9][1-6][1-6][1-6][1-6][1-6]b"	
  l = re.findall(rule,s)
  print(l)

  s = "abcabcaccaac"
  rule = "a[a,b,c]c"  # rule = "a[a-z0-9][a-z0-9][a-z0-9][a-z0-9]c"	
  l = re.findall(rule, s)
  print(l)

  ```

#### 2、表达式^和$

  ^ 通常用来匹配行首

  $ 通常用来匹配行尾，不匹配则返回[]


#### 3、表达式反斜杠\

这其中，一切改用大写的，都表示匹配非这些的！！！比如\D表示匹配非数字！！！！

  \d：匹配任何十进制数等价于[0-9]

  re.findall("c\d\d\da", "abc123abc")

  \可以转义成普通字符
  ```
  re.findall("\^abc", "^abc^abc")
  ```
  \s：匹配任何空白字符

  ```
  re.findall("\s\s", "a     c")

  ['  ', '  ']

  ```
  \w：匹配任何字母数字和下划线，等价于[a-z，A-Z，0-9_]，例如：

  re.findall("\w\w\w", "abc12_") 


#### 4、表达式{n}

  {n}可以避免重复写
  ```
  re.findall("\w{2}", "abc12_")
  ['ab', 'c1', '2_']
  ```

#### 5、表达式*

  ```
  *表示匹配零次或多次（尽可能的多去匹配）

  re.findall("010-\d*", "010-123456789")
  ```

#### 6、表达式+

  表示匹配一次或多次（尽可能的多去匹配） ###至少匹配一次
  
#### 7、表达式？（非贪婪模式）

  匹配一次或者0次

  贪婪模式：尽可能多的匹配，如\d*
  
  非贪婪模式：尽可能少，如\d?
  
  
  
#### （1）re.search()

扫描字符串，找到匹配的位置，会返回一个match对象：

a=<re.Match object; span=(0, 3), match='abc'>

a.group() #返回匹配后的

a.start() # 返回匹配的开始位置

a.end() #返回匹配结束位置

a.span() # 返回一个元组，（开始，结束）

#### （2）re.sub(正则表达式，新字符串，原字符串)

s = "abcabcacc" # 原字符串

l = re.sub("abc","ddd",s) 

会将所有abc换成ddd

```
re.sub('(\d+)', '*\g<1>*', n)
```
解析：\d+一定要带括号！！！！！！！！！这样才能用后面的

\g<1>代表前面匹配字段中的第一个分组，可以简写为\1，\g<0>代表前面匹配到的所有字符串

总结，前面匹配的里面，用括号区分

后面的\g的<>里跟的，就可以用前面括号的标号分别替换！！！！！-----------------------------注意



#### （3）re.subn(正则表达式，新字符串，原字符串)

返回替换后的与替换次数

#### （4） re.split()分割字符串

```
s = "abcabcacc"
l = re.split("b",s)
print(l)

['a', 'ca', 'cacc']

```

### 阶乘

math.factorial(3)

### 字符串

a='123'

a.isalpha()

a.isdigit()

a.islower()

a.isupper()

a.index('1') # 返回索引值

a.replace('1','2') # 把1换成2

' '.join(map(str,a))  # 此方法也能输出空格形式，善用map!!!!!!!!!!!!!!!!!!!


### 存在多组输入的情况，Try语句

while 1:
try:

except:
  break
  
### 计算表达式的值eval() 

注意！！当遇到需要将包含运算符的字符串拆分成数字和运算符时：可以用' + 'replace'+'，以保证需要拆分的东西之间有空格，在split拆分即可


### 手动计算表达式的值时候：逆波兰表达式

https://blog.csdn.net/sgbfblog/article/details/8001651

中缀表达式转后缀表达式（逆波兰表达式）：遇到数字，直接输出，遇到操作符，如果优先级大于栈顶，则放入栈中，遇到左括号，放入栈中

遇到右括号，将栈中元素不断弹出直到遇到左括号为止，左括号只弹出不输出

括号优先级最高

全部转化完后，正常用栈计算

### 字典排序

a=dict.items() #会返回一个(key,value)的列表

然后用lambda排序

b.sorted(a,key=lambda x:)

对多个变量进行排序栗子：

```
lst.sort(key = lambda x : (x[1],x[0]))

以元素的第二个元素先升序排列，再以第一个元素升序排列

默认是升序排序，注意！！！！！！！！！！！！
```
