## 第一章 准备工作


```python
#重要的库
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## 第二章 语言基础


```python
# 略
```

## 第三章 内建数据结构，函数，文件


```python
# 略
```

## 第四章 Numpy


```python
#构造数组
data1 = [1,2,3,4,4.5]
arr1 = np.array(data1)
data2 = [[1,2,3,4], [2,3,4,5]]
arr2 = np.array(data2)
arr3 = np.arange(15)
arr1,arr2,arr3
```




    (array([1. , 2. , 3. , 4. , 4.5]),
     array([[1, 2, 3, 4],
            [2, 3, 4, 5]]),
     array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14]))




```python
#查看数组形状
arr2.shape
```




    (2, 4)




```python
#查看数组维度
arr2.ndim
```




    2




```python
#查看数据类型
arr1.dtype
```




    dtype('float64')




```python
#特殊数组构造
arr1 = np.zeros(10)
arr2 = np.ones((2,3))
arr3 = np.empty((2,3,2))
arr1,arr2,arr3
```




    (array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.]),
     array([[1., 1., 1.],
            [1., 1., 1.]]),
     array([[[9.15381310e-312, 2.47032823e-322],
             [0.00000000e+000, 0.00000000e+000],
             [7.56587583e-307, 1.58817677e-052]],
     
            [[6.25764281e-091, 1.49053338e+161],
             [3.63478476e+174, 1.25882617e-075],
             [3.99910963e+252, 1.43700503e+294]]]))




```python
#数据类型转换
arr1 = np.array([1,2,3], dtype=np.int32)
arr2 = arr1.astype(np.float64)
arr3 = arr1.astype(arr2.dtype)
arr2.dtype,arr3.dtype
```




    (dtype('float64'), dtype('float64'))




```python
#向量化
arr1 = np.array([1,2,3,4])
arr2 = arr1**2
arr3 = arr1 > arr2
arr2,arr3
```




    (array([ 1,  4,  9, 16], dtype=int32), array([False, False, False, False]))




```python
#索引切片
arr = np.array([[1,2,3],[4,5,6],[7,8,9]])
arr[0],arr[0:2],arr[0:2,2],arr[0:2,1:2]
arr1 = arr[0].copy()
arr1
```




    array([1, 2, 3])




```python
# 布尔索引
names =np.array(['alex','bob', 'bob', 'john','joe' ,'kevin', 'joe'])
data = np.random.randn(7,4)
data[(names == 'bob')|(names == 'joe')]
```




    array([[-0.40652676,  0.39112718,  0.72331186, -2.25557161],
           [ 0.94550158, -1.05566305, -0.8200999 ,  0.44347169],
           [ 0.46027494,  0.69968576, -1.02646626, -0.53180879],
           [ 0.39548259, -0.22220451, -0.06003978,  1.02496425]])




```python
#神奇索引
arr = np.arange(48).reshape(8,6)
arr[[1,5,3,4],[0,1,2,5]]
```




    array([ 6, 31, 20, 29])




```python
#数组转置
arr = np.arange(10).reshape(2,5)
arr.T
```




    array([[0, 5],
           [1, 6],
           [2, 7],
           [3, 8],
           [4, 9]])




```python
#通用函数
arr = np.arange(12).reshape(3,4)
np.square(arr)
```




    array([[  0,   1,   4,   9],
           [ 16,  25,  36,  49],
           [ 64,  81, 100, 121]], dtype=int32)




```python
#数组编程
arr1 = np.array([1,2,3,4,5])
arr2 = np.array([6,7,8,9,10])
condition = np.array([True,True,False,True,False])
result = np.where(condition , arr1, arr2)
result
```




    array([ 1,  2,  8,  4, 10])




```python
#数组统计
arr = np.arange(10).reshape(2,5)
arr.sum(axis=1)
```




    array([10, 35])




```python
#布尔统计
condition = np.array([True,True,False,True,False])
a = condition.any()
b = condition.all()
a,b
```




    (True, False)




```python
#数组排序
arr = np.array([[5,4,3,2,1],[1,2,3,4,5]])
arr1 = np.sort(arr)
arr1
```




    array([[1, 2, 3, 4, 5],
           [1, 2, 3, 4, 5]])




```python
#线代点乘
arr1 = np.arange(6).reshape(2,3)
arr2 = np.arange(6).reshape(3,2)
arr1.dot(arr2)
```




    array([[10, 13],
           [28, 40]])




```python
#伪随机数
np.random.seed(4567) #全局种子
reg = np.random.RandomState(1234) #独立种子
sample = reg.normal(size=(4,4))
sample
```




    array([[ 4.71435164e-01, -1.19097569e+00,  1.43270697e+00,
            -3.12651896e-01],
           [-7.20588733e-01,  8.87162940e-01,  8.59588414e-01,
            -6.36523504e-01],
           [ 1.56963721e-02, -2.24268495e+00,  1.15003572e+00,
             9.91946022e-01],
           [ 9.53324128e-01, -2.02125482e+00, -3.34077366e-01,
             2.11836468e-03]])




```python
#随机漫步
nsteps = 1000
nwalks = 5000
draws = np.random.randint(0,2,size=(nwalks,nsteps))
steps = np.where(draws>0,1,-1)
walks = steps.cumsum(axis=1)
walks
```




    array([[ -1,   0,   1, ...,  24,  25,  24],
           [  1,   0,  -1, ..., -22, -23, -22],
           [ -1,  -2,  -3, ..., -16, -17, -16],
           ...,
           [  1,   2,   1, ...,  -4,  -5,  -4],
           [ -1,  -2,  -1, ..., -26, -27, -26],
           [ -1,  -2,  -3, ...,  56,  57,  58]], dtype=int32)



## 第五章 Pandas


```python
#Series
ps = pd.Series([1,2,3,4,5],index=['a','b','c','d','e'])
ps, ps.values, ps.index, ps['a'], ps[['a','b']], ps[ps>2]
```




    (a    1
     b    2
     c    3
     d    4
     e    5
     dtype: int64,
     array([1, 2, 3, 4, 5], dtype=int64),
     Index(['a', 'b', 'c', 'd', 'e'], dtype='object'),
     1,
     a    1
     b    2
     dtype: int64,
     c    3
     d    4
     e    5
     dtype: int64)




```python
#自动对齐
dic =  {'libai':23, 'dufu':24, 'wangwei':25, 'sushi':30}
poet = ['libai', 'dufu', 'dufu', 'xinqiji']
ps = pd.Series(dic, index=poet, name='age')
ps, ps.isnull(), ps.notnull(), ps.name, ps.dtype
```




    (libai      23.0
     dufu       24.0
     dufu       24.0
     xinqiji     NaN
     Name: age, dtype: float64,
     libai      False
     dufu       False
     dufu       False
     xinqiji     True
     Name: age, dtype: bool,
     libai       True
     dufu        True
     dufu        True
     xinqiji    False
     Name: age, dtype: bool,
     'age',
     dtype('float64'))




```python
#DataFrame
dic = {
        'name':['libai', 'dufu', 'sushi', 'wangwei'],
        'age':[23, 24, 25, 26],
        'number':[1000, 2000, 3000, 4000]
        }
df = pd.DataFrame(dic, columns=['name', 'age', 'number', 'money'], index=['one', 'two', 'three', 'four'])
df, df['age']
```




    (          name  age  number money
     one      libai   23    1000   NaN
     two       dufu   24    2000   NaN
     three    sushi   25    3000   NaN
     four   wangwei   26    4000   NaN,
     one      23
     two      24
     three    25
     four     26
     Name: age, dtype: int64)




```python
#DataFrame操作
df['money'] = np.arange(4)
ps = pd.Series([2,3], index=('one','three'))
df['wife'] = ps
df['old'] = df['age']>25
del df['number']
df, df.values
```




    (          name  age  money  wife    old
     one      libai   23      0   2.0  False
     two       dufu   24      1   NaN  False
     three    sushi   25      2   3.0  False
     four   wangwei   26      3   NaN   True,
     array([['libai', 23, 0, 2.0, False],
            ['dufu', 24, 1, nan, False],
            ['sushi', 25, 2, 3.0, False],
            ['wangwei', 26, 3, nan, True]], dtype=object))




```python
#Index
indexs = pd.Index(np.arange(4))
indexs
```




    Int64Index([0, 1, 2, 3], dtype='int64')




```python
#基本功能
dic = {
        'name':['libai', 'dufu', 'sushi', 'wangwei'],
        'age':[23, 24, 25, 26],
        'number':[1000, 2000, 3000, 4000]
        }
df = pd.DataFrame(dic, columns=['name', 'age', 'number', 'money'], index=['one', 'two', 'three', 'four']) 
df1 = df.reindex(['one', 'three', 'four', 'two'])
df2 = df1.reindex(columns=['age', 'name', 'money', 'number'])
df2.drop('money',axis='columns',inplace=True)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>name</th>
      <th>number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>23</td>
      <td>libai</td>
      <td>1000</td>
    </tr>
    <tr>
      <th>three</th>
      <td>25</td>
      <td>sushi</td>
      <td>3000</td>
    </tr>
    <tr>
      <th>four</th>
      <td>26</td>
      <td>wangwei</td>
      <td>4000</td>
    </tr>
    <tr>
      <th>two</th>
      <td>24</td>
      <td>dufu</td>
      <td>2000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#loc和iloc
ps1 = df2.loc['one',['age', 'name']]
ps2 = df2.loc[:'four','age':'name']
ps3 = df2.iloc[0,[0,1]]
ps4 = df2.iloc[:2,0:1]
ps1,ps2,ps3,ps4
```




    (age        23
     name    libai
     Name: one, dtype: object,
            age     name
     one     23    libai
     three   25    sushi
     four    26  wangwei,
     age        23
     name    libai
     Name: one, dtype: object,
            age
     one     23
     three   25)




```python
#map,apply,applymap
dic = {
        'name':['libai', 'dufu', 'sushi', 'wangwei'],
        'age':[23, 24, 25, 26],
        'number':[1000, 2000, 3000, 4000]
        }
df = pd.DataFrame(dic)
ps = pd.Series([1,2,3,4], index=['one', 'two', 'three', 'four'])

ps.map(lambda x: x**2), df.apply(lambda x: x.max()), df[['age','number']].applymap(lambda x: x+1),ps.apply(lambda x: x**2)
```




    (one       1
     two       4
     three     9
     four     16
     dtype: int64,
     name      wangwei
     age            26
     number       4000
     dtype: object,
        age  number
     0   24    1001
     1   25    2001
     2   26    3001
     3   27    4001,
     one       1
     two       4
     three     9
     four     16
     dtype: int64)




```python
#sort_index,sort_values,rank
ps = pd.Series([2,3,5,4], index=['b', 'd', 'c', 'a'])
ps.sort_index(),ps.sort_values(),ps.rank()
```




    (a    4
     b    2
     c    5
     d    3
     dtype: int64,
     b    2
     d    3
     a    4
     c    5
     dtype: int64,
     b    1.0
     d    2.0
     c    4.0
     a    3.0
     dtype: float64)




```python
#统计方法
dic = {
        'name':[2, 3, 4, 5],
        'age':[3, 3, 3, 1],
        'number':[1, 2, 5, 1]
        }
df = pd.DataFrame(dic)
ps = pd.Series([2,3,5,4], index=['a', 'b', 'c', 'd'])
ps.sum(), df.cumsum(), ps.unique(), ps.nunique(), ps.value_counts(), df.apply(pd.value_counts).fillna(0)
```




    (14,
        name  age  number
     0     2    3       1
     1     5    6       3
     2     9    9       8
     3    14   10       9,
     array([2, 3, 5, 4], dtype=int64),
     4,
     5    1
     4    1
     3    1
     2    1
     dtype: int64,
        name  age  number
     1   0.0  1.0     2.0
     2   1.0  0.0     1.0
     3   1.0  3.0     0.0
     4   1.0  0.0     0.0
     5   1.0  0.0     1.0)



## 第六章 获取数据


```python
# 略
```

## 第七章 数据清洗


```python
#缺失值
dic1 = {
        'name':[2, 3, 4, 5],
        'age':[3, 3, 3, 1],
        'number':[1, 2, 5, 1]
        }
dic2 = {
        'age':[3, 3, 3],
        'number':[1, 2, 5]
        }
df1 = pd.DataFrame(dic1)
df2 = pd.DataFrame(dic2)
df = df1 + df2
df, df.iloc[0:3,[0,2]].dropna(), df.fillna(0)
```




    (   age  name  number
     0  6.0   NaN     2.0
     1  6.0   NaN     4.0
     2  6.0   NaN    10.0
     3  NaN   NaN     NaN,
        age  number
     0  6.0     2.0
     1  6.0     4.0
     2  6.0    10.0,
        age  name  number
     0  6.0   0.0     2.0
     1  6.0   0.0     4.0
     2  6.0   0.0    10.0
     3  0.0   0.0     0.0)




```python
#重复值
df1.duplicated(),df1.duplicated('age'),df1.drop_duplicates('age')
```




    (0    False
     1    False
     2    False
     3    False
     dtype: bool,
     0    False
     1     True
     2     True
     3    False
     dtype: bool,
        name  age  number
     0     2    3       1
     3     5    1       1)




```python
#重命名
df1.rename(index={0:'one', 1:'two',3:'three', 4:'four'}, columns=str.title)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>2</td>
      <td>3</td>
      <td>1</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>3</td>
      <td>5</td>
    </tr>
    <tr>
      <th>three</th>
      <td>5</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#离散化
age = list(np.arange(50))
bins = [0, 10, 20, 30 ,40, 50]
pd.cut(age, bins, right=False, labels=['one', 'two', 'three', 'four', 'five']), pd.cut(age, 5), pd.qcut(age,5).value_counts()
```




    (['one', 'one', 'one', 'one', 'one', ..., 'five', 'five', 'five', 'five', 'five']
     Length: 50
     Categories (5, object): ['one' < 'two' < 'three' < 'four' < 'five'],
     [(-0.049, 9.8], (-0.049, 9.8], (-0.049, 9.8], (-0.049, 9.8], (-0.049, 9.8], ..., (39.2, 49.0], (39.2, 49.0], (39.2, 49.0], (39.2, 49.0], (39.2, 49.0]]
     Length: 50
     Categories (5, interval[float64]): [(-0.049, 9.8] < (9.8, 19.6] < (19.6, 29.4] < (29.4, 39.2] < (39.2, 49.0]],
     (-0.001, 9.8]    10
     (9.8, 19.6]      10
     (19.6, 29.4]     10
     (29.4, 39.2]     10
     (39.2, 49.0]     10
     dtype: int64)




```python
#字符串操作
val = 'a, b, c'
'a' in val, val.index('a'), val.find('d'), '::'.join(val).replace('::', '==')
```




    (True, 0, -1, 'a==,== ==b==,== ==c')




```python
#正则表达式
#略
```

## 第八章 数据规整


```python
#拆堆堆叠
df = pd.Series(np.random.randn(9), index=[['a', 'a', 'a', 'b', 'b', 'c', 'c', 'd', 'd'],[1,2,3,1,3,1,2,2,3]])
df.unstack(), df.unstack().stack()
```




    (          1         2         3
     a -0.064633  1.150553  0.692987
     b  1.084676       NaN  0.848292
     c -0.941897  0.853164       NaN
     d       NaN -0.210822 -0.407181,
     a  1   -0.064633
        2    1.150553
        3    0.692987
     b  1    1.084676
        3    0.848292
     c  1   -0.941897
        2    0.853164
     d  2   -0.210822
        3   -0.407181
     dtype: float64)




```python
#联结合并
df1 = pd.DataFrame({'key1':['a', 'a', 'a', 'b', 'b', 'c', 'c'], 'num1':range(7)},index=['a', 'b', 'c', 'd', 'e', 'f', 'j'])
df2 = pd.DataFrame({'key2':['a', 'b', 'b'], 'num2':range(3)}, index=['a', 'b', 'c'])
pd.merge(df1, df2, left_on='key1', right_on='key2', how='left'), df1.join(df2, how='inner'), pd.concat([df1, df2])
```




    (  key1  num1 key2  num2
     0    a     0    a   0.0
     1    a     1    a   0.0
     2    a     2    a   0.0
     3    b     3    b   1.0
     4    b     3    b   2.0
     5    b     4    b   1.0
     6    b     4    b   2.0
     7    c     5  NaN   NaN
     8    c     6  NaN   NaN,
       key1  num1 key2  num2
     a    a     0    a     0
     b    a     1    b     1
     c    a     2    b     2,
       key1  num1 key2  num2
     a    a   0.0  NaN   NaN
     b    a   1.0  NaN   NaN
     c    a   2.0  NaN   NaN
     d    b   3.0  NaN   NaN
     e    b   4.0  NaN   NaN
     f    c   5.0  NaN   NaN
     j    c   6.0  NaN   NaN
     a  NaN   NaN    a   0.0
     b  NaN   NaN    b   1.0
     c  NaN   NaN    b   2.0)




```python
#透视和逆透视
dic = {
        'name':[2, 3, 4, 5],
        'age':[3, 3, 3, 1],
        'number':[1, 2, 5, 1],
        'key':['one', 'two', 'three', 'four']
        }
df = pd.DataFrame(dic)
pd.melt(df, ['key']), pd.melt(df, ['key']).pivot('key', 'variable')
```




    (      key variable  value
     0     one     name      2
     1     two     name      3
     2   three     name      4
     3    four     name      5
     4     one      age      3
     5     two      age      3
     6   three      age      3
     7    four      age      1
     8     one   number      1
     9     two   number      2
     10  three   number      5
     11   four   number      1,
              value            
     variable   age name number
     key                       
     four         1    5      1
     one          3    2      1
     three        3    4      5
     two          3    3      2)



## 第九章 可视化


```python
#略
```

## 第十章 数据聚合


```python
#分组遍历
df = pd.DataFrame({
                    'key1':['a', 'a', 'b', 'b', 'a' ], 
                    'key2':['one', 'one', 'two', 'one', 'two'],
                    'num1':np.random.randn(5),
                    'num2':np.random.randn(5)
                    })
grouped = df.groupby(df['key1'])
for name, group in grouped:
    print(name)
    print(group)
```




    key1
    a    0.790326
    b    0.119846
    Name: num1, dtype: float64




```python
#聚合应用
grouped['num1'].mean(), grouped.agg({'num1':'mean', 'num2':'sum'}), grouped.apply(lambda x: x.describe())
```




    (key1
     a    0.790326
     b    0.119846
     Name: num1, dtype: float64,
               num1      num2
     key1                    
     a     0.790326  2.264426
     b     0.119846 -2.591844,
                     num1      num2
     key1                          
     a    count  3.000000  3.000000
          mean   0.790326  0.754809
          std    1.854929  1.354602
          min   -0.919233 -0.667064
          25%   -0.195817  0.117092
          50%    0.527600  0.901248
          75%    1.645105  1.465745
          max    2.762610  2.030242
     b    count  2.000000  2.000000
          mean   0.119846 -1.295922
          std    2.545395  1.407480
          min   -1.680021 -2.291161
          25%   -0.780088 -1.793542
          50%    0.119846 -1.295922
          75%    1.019779 -0.798303
          max    1.919712 -0.300683)




```python
#数据透视表
df.pivot_table('num2', index=['key1', 'key2'], margins=True, aggfunc='sum', fill_value='-')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>num2</th>
    </tr>
    <tr>
      <th>key1</th>
      <th>key2</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">a</th>
      <th>one</th>
      <td>2.931490</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.667064</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">b</th>
      <th>one</th>
      <td>-2.291161</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.300683</td>
    </tr>
    <tr>
      <th>All</th>
      <th></th>
      <td>-0.327418</td>
    </tr>
  </tbody>
</table>
</div>




```python
#交叉表
pd.crosstab(df['key1'], df['key2'], margins=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>key2</th>
      <th>one</th>
      <th>two</th>
      <th>All</th>
    </tr>
    <tr>
      <th>key1</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>2</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>b</th>
      <td>1</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>All</th>
      <td>3</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



## 第十一章 时间序列


```python
#数据类型
from datetime import datetime
now_time = datetime.now()
now_time, now_time.year, now_time.month, now_time.day
```




    (datetime.datetime(2021, 8, 23, 21, 58, 40, 256386), 2021, 8, 23)




```python
delta = datetime(2011, 1, 7) - datetime(2008, 6, 24, 8, 15)
delta
```




    datetime.timedelta(days=926, seconds=56700)




```python
#格式转换
from datetime import timedelta
start = datetime(2020, 3, 4)
time = '2020-4-1'
start += timedelta(12)
start.strftime('%Y-%m-%d'),datetime.strptime(time, '%Y-%m-%d'),pd.to_datetime(time)
```




    ('2020-03-16',
     datetime.datetime(2020, 4, 1, 0, 0),
     Timestamp('2020-04-01 00:00:00'))




```python
#索引切片
ts = pd.Series(np.random.randn(10),index=pd.date_range('2020/1/1', periods=10))
ts,ts['2020/1/1'],ts['01-01-2020'], ts['2020-01'],ts['2020/1/6':]
```




    (2020-01-01    0.761516
     2020-01-02    0.576609
     2020-01-03    1.149412
     2020-01-04   -0.786316
     2020-01-05   -0.061115
     2020-01-06    2.141148
     2020-01-07   -0.205720
     2020-01-08    0.233272
     2020-01-09    0.304701
     2020-01-10    0.062325
     Freq: D, dtype: float64,
     0.7615158261563532,
     0.7615158261563532,
     2020-01-01    0.761516
     2020-01-02    0.576609
     2020-01-03    1.149412
     2020-01-04   -0.786316
     2020-01-05   -0.061115
     2020-01-06    2.141148
     2020-01-07   -0.205720
     2020-01-08    0.233272
     2020-01-09    0.304701
     2020-01-10    0.062325
     Freq: D, dtype: float64,
     2020-01-06    2.141148
     2020-01-07   -0.205720
     2020-01-08    0.233272
     2020-01-09    0.304701
     2020-01-10    0.062325
     Freq: D, dtype: float64)




```python
#时间范围，频率，移位
time1 = pd.date_range('2020/1/1', '2020/6/1', freq='BM')
time2 = pd.date_range('2020/1/1', periods=6, freq='3H')
ts = pd.Series(np.random.randn(6), index=time2)
time1, time2, ts.shift(2, freq='1H')
```




    (DatetimeIndex(['2020-01-31', '2020-02-28', '2020-03-31', '2020-04-30',
                    '2020-05-29'],
                   dtype='datetime64[ns]', freq='BM'),
     DatetimeIndex(['2020-01-01 00:00:00', '2020-01-01 03:00:00',
                    '2020-01-01 06:00:00', '2020-01-01 09:00:00',
                    '2020-01-01 12:00:00', '2020-01-01 15:00:00'],
                   dtype='datetime64[ns]', freq='3H'),
     2020-01-01 02:00:00   -0.773234
     2020-01-01 05:00:00    1.544144
     2020-01-01 08:00:00    0.525485
     2020-01-01 11:00:00   -0.031263
     2020-01-01 14:00:00   -0.987958
     2020-01-01 17:00:00   -1.149923
     Freq: 3H, dtype: float64)




```python
#时间区间
rng = pd.period_range('2020/1/1', '2020/6/1', freq='M')
data = pd.DataFrame({'year':[2020, 2020, 2020, 2020], 'quarter':[1, 2, 3, 4]})
index = pd.PeriodIndex(year=data['year'], quarter=data['quarter'], freq='Q-DEC')
rng, index
```




    (PeriodIndex(['2020-01', '2020-02', '2020-03', '2020-04', '2020-05', '2020-06'], dtype='period[M]', freq='M'),
     PeriodIndex(['2020Q1', '2020Q2', '2020Q3', '2020Q4'], dtype='period[Q-DEC]', freq='Q-DEC'))




```python
#时间采样
ts1 = ts.resample('6H',closed='right', label='left').sum()
ts1, ts1.resample('D').asfreq()
```




    (2019-12-31 18:00:00   -0.773234
     2020-01-01 00:00:00    2.069629
     2020-01-01 06:00:00   -1.019221
     2020-01-01 12:00:00   -1.149923
     Freq: 6H, dtype: float64,
     2019-12-31         NaN
     2020-01-01    2.069629
     Freq: D, dtype: float64)



## 第十二章 高阶pandas


```python
#略
```

## 第十三章 Python建模库


```python
#pandas转=转换Numpy数组
df = pd.DataFrame({
                    'key1':[1, 2, 3, 4, 5 ], 
                    'key2':[0, 0, 1, 1, 0],
                    'num1':np.random.randn(5),
                    'num2':np.random.randn(5)
                    })
df.values
```




    array([[ 1.        ,  0.        ,  0.5402388 , -0.87108001],
           [ 2.        ,  0.        , -0.48834832,  1.15965327],
           [ 3.        ,  1.        , -0.97721815, -1.53682414],
           [ 4.        ,  1.        , -0.81858522, -0.26373222],
           [ 5.        ,  0.        , -1.55042917,  1.84700193]])




```python
#pandas实现独热编码
pd.get_dummies(df['key1'], prefix='key1')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key1_1</th>
      <th>key1_2</th>
      <th>key1_3</th>
      <th>key1_4</th>
      <th>key1_5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#重要的库
import sklearn
```

## 第十四章 数据分析示例


```python
#略
```

## 附录 A 高阶Numpy


```python
#重塑
arr = np.arange(8).reshape(2,4).reshape(4,-1).ravel()
arr
```




    array([0, 1, 2, 3, 4, 5, 6, 7])




```python
#联结
arr1 = np.array([[1,2,3], [4,5,6]])
arr2 = np.array([[7,8,9], [4,5,6]])
np.concatenate([arr1, arr2], axis=1), np.concatenate([arr1, arr2], axis=0), np.vstack((arr1,arr2)), np.hstack((arr1,arr2))
```




    (array([[1, 2, 3, 7, 8, 9],
            [4, 5, 6, 4, 5, 6]]),
     array([[1, 2, 3],
            [4, 5, 6],
            [7, 8, 9],
            [4, 5, 6]]),
     array([[1, 2, 3],
            [4, 5, 6],
            [7, 8, 9],
            [4, 5, 6]]),
     array([[1, 2, 3, 7, 8, 9],
            [4, 5, 6, 4, 5, 6]]))




```python
#分割
arr = np.concatenate([arr1, arr2], axis=0)
np.split(arr, [1,3])
```




    [array([[1, 2, 3]]),
     array([[4, 5, 6],
            [7, 8, 9]]),
     array([[4, 5, 6]])]




```python
#复制
arr = np.arange(5)
arr.repeat(2), arr1.repeat(2, axis=1), np.tile(arr1,2)
```




    (array([0, 0, 1, 1, 2, 2, 3, 3, 4, 4]),
     array([[1, 1, 2, 2, 3, 3],
            [4, 4, 5, 5, 6, 6]]),
     array([[1, 2, 3, 1, 2, 3],
            [4, 5, 6, 4, 5, 6]]))




```python
#索引
num = [2,0]
arr1.take(num)
```




    array([3, 1])




```python
#广播机制
arr1 = np.random.randn(3, 4)
arr2 = np.array([1,2,3,4])
arr = arr1 + arr2
arr
```




    array([[1.80511669, 1.65943157, 3.20893778, 4.28159182],
           [2.29309364, 1.34171781, 2.94099706, 3.80392867],
           [2.79936584, 2.15434728, 4.97127238, 5.07763904]])



## 附录B IPython系统


```python
#单次代码测时
df = pd.DataFrame({
                    'key1':[1, 2, 3, 4, 5 ], 
                    'key2':[0, 0, 1, 1, 0],
                    'num1':np.random.randn(5),
                    'num2':np.random.randn(5)
                    })
%time df.values
```

    Wall time: 0 ns
    




    array([[ 1.        ,  0.        ,  0.47324541,  0.8849776 ],
           [ 2.        ,  0.        ,  0.15848586, -1.456969  ],
           [ 3.        ,  1.        , -0.50025804, -0.34593244],
           [ 4.        ,  1.        ,  0.19436924,  1.77909214],
           [ 5.        ,  0.        , -0.86814133,  0.17804182]])




```python
#多次代码测时
df = pd.DataFrame({
                    'key1':[1, 2, 3, 4, 5 ], 
                    'key2':[0, 0, 1, 1, 0],
                    'num1':np.random.randn(5),
                    'num2':np.random.randn(5)
                    })
%timeit df.values
```

    49.7 µs ± 1.97 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
    
