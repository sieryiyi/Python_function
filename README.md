# Python_function
用来记录刷题过程中方便的API


### 1、小数转分数fractions.Fraction

！！！注意，要想小数不损失精度，要化成字符串形式，例如：

```
    a=fractions.Fraction（'1.1'） # 此时才会出现11,10 的结果
    a.numerator # 获取分子
    a.denominator # 获取分母
```

保证精度-方法二：fractions.Fraction(8/11-1/2).limit_denominator()

保证精度-方法三：
```
x1=fractions.Fraction(1,x1) # 都先化成fraction的形式
x2=fractions.Fraction(1,x2)
y=fractions.Fraction(x1-x2)
```

### 2、迭代器itemtools的用处

##### （1）用于全排列 list(itertools.permutations（[1,2,3],2）)

会得到[(1,0),(0,2)..........]


### eval的用法细节

eval('3//2')
>>1
eval('3/2')
>>1.5
