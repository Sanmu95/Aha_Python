# Matplotlib

## 画布子图


```python
import matplotlib.pyplot as plt
import matplotlib.gridspec as gs
import numpy as np
import pandas as pd
plt.rcParams["font.family"]="SimHei"
plt.rcParams['axes.unicode_minus'] = False 
```


```python
#设置画布
x = np.array([1, 2, 3, 4, 5, 6])
y = np.array([1, 4, 9, 16, 25, 36])
fig = plt.figure(figsize=(5, 5))
plt.plot(x, y)
```




    [<matplotlib.lines.Line2D at 0x24c0c920f10>]




![png](https://i.loli.net/2021/08/28/gh2wEKXbDYMjCp1.png)
    



```python
#设置子图
x = np.array([1, 2, 3, 4, 5, 6])
y = np.array([1, 4, 9, 16, 25, 36])
fig = plt.figure(num=1, figsize=(10, 5))
ax1 = fig.add_subplot(121)#plt.subplot(121)
ax2 = fig.add_subplot(122)
ax1.plot(x, y)
ax2.plot(y, x)
```




    [<matplotlib.lines.Line2D at 0x24c0ca55040>]




![png](https://i.loli.net/2021/08/28/jyHXsYO9ag4KonL.png)
    



```python
#遍历画布子图
fig, axes = plt.subplots(2,2)
axes
```




    array([[<AxesSubplot:>, <AxesSubplot:>],
           [<AxesSubplot:>, <AxesSubplot:>]], dtype=object)




![png](https://i.loli.net/2021/08/28/OvEwQ1lUFzpGKcA.png)
    



```python
#设置网格
fig = plt.figure(num=1,figsize=(5,5))
gs = gs.GridSpec(3,3)
ax1 = fig.add_subplot(gs[0,:])
ax2 = fig.add_subplot(gs[2,0:2])
ax3 = fig.add_subplot(gs[1:,2])
ax1.plot(x, y)
ax2.plot(x, y)
ax3.plot(x, y)
```




    [<matplotlib.lines.Line2D at 0x24c0cc58c70>]




![png](https://i.loli.net/2021/08/28/6rUDGNxiCJbnfsS.png)
    


## 元素设置


```python
#图形元素
fig=plt.figure(num=1,figsize=(5,5))
ax=fig.add_subplot(111)
ax.plot(x, y, color='k', marker='D', linestyle='-')

#轴范围
ax.set_xlim([0,6])
ax.set_ylim([0,50])

#轴刻度
ax.set_xticks(np.linspace(0,7,8))
ax.set_yticks(np.linspace(0,50,6))

#刻度标签
ax.set_xticklabels(['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven'],fontproperties='SimHei',fontsize=12)
ax.set_yticklabels([0, 10, 20, 30, 40, 50])

#刻度线
ax.tick_params('x', left=False, pad=8, direction='in', length=4, width=2, color='r', labelsize=12)

#轴标题
ax.set_xlabel('类别')
ax.set_ylabel('数量',fontsize=20)
ax.set_title('数量统计',fontsize=18, fontweight='bold', color='red', verticalalignment='baseline')

#轴线
ax.spines['left'].set_color("darkblue")
ax.spines['bottom'].set_linewidth(5)
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

#图例
ax.legend(('milk'), loc='upper left', labelspacing=2, handlelength=4, fontsize=14, shadow=True)

#数据标签
ax.text(6.5, 40, 'max:36', fontsize=14, color='g', alpha=1)

#网格线
ax.yaxis.grid(color='r', linestyle='--', linewidth=1, alpha=0.3)
ax.xaxis.grid(color='r', linestyle='--', linewidth=1, alpha=0.3)

plt.show()
```


![png](https://i.loli.net/2021/08/28/lHocRqXpG6kM215.png)
    


## 常用图表


```python
#条形图
plt.bar(x=x, height=y, color='b', bottom=0, edgecolor='red', label='数量', linewidth=2, width=1, alpha=1)
```




    <BarContainer object of 6 artists>




![png](https://i.loli.net/2021/08/28/Vc5ZSOUl61WodgM.png)
    



```python
#箱线图
plt.boxplot([x, y])

df = pd.DataFrame({'key1':x, 'key2':y, 'key3':[1, 1, 1, 2, 2, 2]})
df.boxplot(column=['key1', 'key2'], by='key3')
```




    array([<AxesSubplot:title={'center':'key1'}, xlabel='key3'>,
           <AxesSubplot:title={'center':'key2'}, xlabel='key3'>], dtype=object)




![png](https://i.loli.net/2021/08/28/qav9pDBKkZ2Anhl.png)
    




![png](https://i.loli.net/2021/08/28/Tq9tu2UFOyPcmgK.png)
    



```python
#散点图
plt.scatter(x, y, c=x, s=y, alpha=1, cmap='gray')
```




    <matplotlib.collections.PathCollection at 0x24c0df47d00>




![png](https://i.loli.net/2021/08/28/Btq5FmlsPKIZNTp.png)
    


# Seaborn

## 回归


```python
import seaborn as sns
sns.set(style='whitegrid')
df = pd.read_csv(r'D:\文件\data_set\example.csv', index_col=0)
```


```python
sns.lmplot(x='n1', y='n2',col='key', hue='key', data=df )
```




    <seaborn.axisgrid.FacetGrid at 0x24c12ebfd60>




![png](https://i.loli.net/2021/08/28/RWQmqYxzav7Zk31.png)
    



```python
sns.regplot(x='n1', y='n2', data=df )
```




    <AxesSubplot:xlabel='n1', ylabel='n2'>




![png](https://i.loli.net/2021/08/28/G7Ev5Vt9mJPzIRh.png)
    



```python
sns.residplot(x='n1', y='n2', data=df )
```




    <AxesSubplot:xlabel='n1', ylabel='n2'>




![png](https://i.loli.net/2021/08/28/pj3lITmUGtLRqMg.png)
    


## 关系


```python
sns.scatterplot(x='n6', y='n5',hue='key', size='n0', data=df)

sns.relplot(x='n6', y='n5',hue='key', size='n0', kind='scatter', data=df)
```




    <seaborn.axisgrid.FacetGrid at 0x24c12a4c400>




![png](https://i.loli.net/2021/08/28/ZudENVl1bCMGO8v.png)
    




![png](https://i.loli.net/2021/08/28/fQ9yxEnqjzA2KgT.png)
    



```python
sns.lineplot(x='n8', y='n9',hue='key', data=df)

sns.relplot(x='n8', y='n9',hue='key', kind='line', data=df)
```




    <seaborn.axisgrid.FacetGrid at 0x24c12d745e0>




![png](https://i.loli.net/2021/08/28/8GbHVN4Ukw3CTim.png)
    




![png](https://i.loli.net/2021/08/28/GsjkJifzNb4reRY.png)
    



```python
mask = np.triu(np.ones_like(df.corr(), dtype=bool))
sns.heatmap(df.corr(), mask=mask)
```




    <AxesSubplot:>




![png](https://i.loli.net/2021/08/28/fz4EAwoTdBnYPvK.png)
    


## 分类


```python
sns.barplot(x='key', y='n5', data=df)

sns.catplot(x='key', y='n5', hue='n11', data=df, kind='bar')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16932df0>




![png](https://i.loli.net/2021/08/28/j6s4pNJVbqcZwvl.png)
    




![png](https://i.loli.net/2021/08/28/BTM3PLfQbDnWewd.png)
    



```python
sns.pointplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', col='n11', data=df, kind='point')
```




    <seaborn.axisgrid.FacetGrid at 0x24c164071c0>




![png](https://i.loli.net/2021/08/28/myAxsqQO1iaoWeY.png)
    




![png](https://i.loli.net/2021/08/28/4A8YMXdpqzJV1yt.png)
    



```python
sns.boxplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='box')
```




    <seaborn.axisgrid.FacetGrid at 0x24c14c18100>




![png](https://i.loli.net/2021/08/28/jsJCW6S82NMev9c.png)
    




![png](https://i.loli.net/2021/08/28/UE74vafhD9uI5qH.png)
    



```python
sns.violinplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='violin')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16bfe9a0>




![png](https://i.loli.net/2021/08/28/Yjh8IAt4l27bL3F.png)
    




![png](https://i.loli.net/2021/08/28/ue7P1GF5RmB4Jzs.png)
    



```python
sns.stripplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='strip')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16415040>




![png](https://i.loli.net/2021/08/28/iztbcZm2OwWaAyh.png)
    




![png](https://i.loli.net/2021/08/28/mVUzWqp6NXvJA4x.png)
    



```python
sns.swarmplot(x='key', y='n10', hue='n11', data=df.iloc[0:100, :])

sns.catplot(x='key', y='n10', hue='n11', data=df.iloc[0:100, :], kind='swarm')
```




    <seaborn.axisgrid.FacetGrid at 0x24c17167640>




![png](https://i.loli.net/2021/08/28/UljFG1NWBxaLCAu.png)
    




![png](https://i.loli.net/2021/08/28/id2ZYswQ5LGhHjO.png)
    


## 分布


```python
sns.histplot(df, x='n10', hue='key')

sns.displot(df, x='n10', col='key', kind='hist')
```




    <seaborn.axisgrid.FacetGrid at 0x24c1488d940>




![png](https://i.loli.net/2021/08/28/3zjhsaAuwdLXTNO.png)
    




![png](https://i.loli.net/2021/08/28/8bpEoQ6HVvDqPfF.png)
    



```python
plt.subplot(131)
sns.kdeplot(x='n1', hue='key', data=df)

plt.subplot(132)
sns.kdeplot(x='n1',y='n2', hue='key', data=df)

plt.subplot(133)
sns.displot(x='n1',y='n2', hue='key', data=df, kind='kde')
```




    <seaborn.axisgrid.FacetGrid at 0x24c147b79d0>




![png](https://i.loli.net/2021/08/28/9fzuXE1NlxDb2GB.png)
    




![png](https://i.loli.net/2021/08/28/B9ZuWngs7fTdO3P.png)
    



```python
sns.ecdfplot(x='n4', hue='key', data=df)

sns.displot(x='n4', hue='key', data=df, kind='ecdf')
```




    <seaborn.axisgrid.FacetGrid at 0x24c12adcc40>




![png](https://i.loli.net/2021/08/28/YdiK1tDnah4ZUbA.png)
    




![png](https://i.loli.net/2021/08/28/wLu5GfKH1te4FnC.png)
    



```python
sns.rugplot(x='n4', hue='key', data=df, height=0.1)
```




    <AxesSubplot:xlabel='n4'>




![png](https://i.loli.net/2021/08/28/nkhbvG2utETxN4Y.png)
    


## 组图


```python
fg = sns.FacetGrid(df, col='key')
fg.map(sns.kdeplot, 'n1')
fg.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x24c1c850af0>




![png](https://i.loli.net/2021/08/28/reIXGosSz1lcDtQ.png)
    



```python
pg = sns.PairGrid(df.loc[:,['key', 'n1', 'n2']], hue='key')
pg.map_diag(sns.histplot)
pg.map_offdiag(sns.scatterplot)
pg.add_legend()

sns.pairplot(df.loc[:,['n1', 'n2', 'n3']])
```




    <seaborn.axisgrid.PairGrid at 0x24c20e59190>




![png](https://i.loli.net/2021/08/28/GnRxTgXaCh4JO3E.png)
    




![png](https://i.loli.net/2021/08/28/hbsoaKTexkFSgML.png)
    



```python
jg = sns.JointGrid(data=df, x='n4', y='n5')
jg.plot(sns.scatterplot, sns.histplot)

sns.jointplot(data=df, x='n4', y='n5', hue='key', kind='hist')
```




    <seaborn.axisgrid.JointGrid at 0x24c1d4d1c40>




![png](https://i.loli.net/2021/08/28/LdwDaOGAuUPvTQe.png)
    




![png](https://i.loli.net/2021/08/28/gTPlo9CLGSXErj1.png)
    

