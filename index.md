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
