### 二分查找

#### import bisect

```
bisect.bisect_left([1,2,6,8],7)  # 找出7的合适插入位置或找出7在列表中的哪一个
bisect.bisect_right([1,2,6,8],7)  # 找出位置后+1

```

### 装饰器

#### @functools.lru_cache

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
