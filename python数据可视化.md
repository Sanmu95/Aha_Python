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




    
![png](output_3_1.png)
    



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




    
![png](output_4_1.png)
    



```python
#遍历画布子图
fig, axes = plt.subplots(2,2)
axes
```




    array([[<AxesSubplot:>, <AxesSubplot:>],
           [<AxesSubplot:>, <AxesSubplot:>]], dtype=object)




    
![png](output_5_1.png)
    



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




    
![png](output_6_1.png)
    


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


    
![png](output_8_0.png)
    


## 常用图表


```python
#条形图
plt.bar(x=x, height=y, color='b', bottom=0, edgecolor='red', label='数量', linewidth=2, width=1, alpha=1)
```




    <BarContainer object of 6 artists>




    
![png](output_10_1.png)
    



```python
#箱线图
plt.boxplot([x, y])

df = pd.DataFrame({'key1':x, 'key2':y, 'key3':[1, 1, 1, 2, 2, 2]})
df.boxplot(column=['key1', 'key2'], by='key3')
```




    array([<AxesSubplot:title={'center':'key1'}, xlabel='key3'>,
           <AxesSubplot:title={'center':'key2'}, xlabel='key3'>], dtype=object)




    
![png](output_11_1.png)
    



    
![png](output_11_2.png)
    



```python
#散点图
plt.scatter(x, y, c=x, s=y, alpha=1, cmap='gray')
```




    <matplotlib.collections.PathCollection at 0x24c0df47d00>




    
![png](output_12_1.png)
    


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




    
![png](output_16_1.png)
    



```python
sns.regplot(x='n1', y='n2', data=df )
```




    <AxesSubplot:xlabel='n1', ylabel='n2'>




    
![png](output_17_1.png)
    



```python
sns.residplot(x='n1', y='n2', data=df )
```




    <AxesSubplot:xlabel='n1', ylabel='n2'>




    
![png](output_18_1.png)
    


## 关系


```python
sns.scatterplot(x='n6', y='n5',hue='key', size='n0', data=df)

sns.relplot(x='n6', y='n5',hue='key', size='n0', kind='scatter', data=df)
```




    <seaborn.axisgrid.FacetGrid at 0x24c12a4c400>




    
![png](output_20_1.png)
    



    
![png](output_20_2.png)
    



```python
sns.lineplot(x='n8', y='n9',hue='key', data=df)

sns.relplot(x='n8', y='n9',hue='key', kind='line', data=df)
```




    <seaborn.axisgrid.FacetGrid at 0x24c12d745e0>




    
![png](output_21_1.png)
    



    
![png](output_21_2.png)
    



```python
mask = np.triu(np.ones_like(df.corr(), dtype=bool))
sns.heatmap(df.corr(), mask=mask)
```




    <AxesSubplot:>




    
![png](output_22_1.png)
    


## 分类


```python
sns.barplot(x='key', y='n5', data=df)

sns.catplot(x='key', y='n5', hue='n11', data=df, kind='bar')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16932df0>




    
![png](output_24_1.png)
    



    
![png](output_24_2.png)
    



```python
sns.pointplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', col='n11', data=df, kind='point')
```




    <seaborn.axisgrid.FacetGrid at 0x24c164071c0>




    
![png](output_25_1.png)
    



    
![png](output_25_2.png)
    



```python
sns.boxplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='box')
```




    <seaborn.axisgrid.FacetGrid at 0x24c14c18100>




    
![png](output_26_1.png)
    



    
![png](output_26_2.png)
    



```python
sns.violinplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='violin')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16bfe9a0>




    
![png](output_27_1.png)
    



    
![png](output_27_2.png)
    



```python
sns.stripplot(x='key', y='n10', hue='n11', data=df)

sns.catplot(x='key', y='n10', hue='n11', data=df, kind='strip')
```




    <seaborn.axisgrid.FacetGrid at 0x24c16415040>




    
![png](output_28_1.png)
    



    
![png](output_28_2.png)
    



```python
sns.swarmplot(x='key', y='n10', hue='n11', data=df.iloc[0:100, :])

sns.catplot(x='key', y='n10', hue='n11', data=df.iloc[0:100, :], kind='swarm')
```




    <seaborn.axisgrid.FacetGrid at 0x24c17167640>




    
![png](output_29_1.png)
    



    
![png](output_29_2.png)
    


## 分布


```python
sns.histplot(df, x='n10', hue='key')

sns.displot(df, x='n10', col='key', kind='hist')
```




    <seaborn.axisgrid.FacetGrid at 0x24c1488d940>




    
![png](output_31_1.png)
    



    
![png](output_31_2.png)
    



```python
plt.subplot(131)
sns.kdeplot(x='n1', hue='key', data=df)

plt.subplot(132)
sns.kdeplot(x='n1',y='n2', hue='key', data=df)

plt.subplot(133)
sns.displot(x='n1',y='n2', hue='key', data=df, kind='kde')
```




    <seaborn.axisgrid.FacetGrid at 0x24c147b79d0>




    
![png](output_32_1.png)
    



    
![png](output_32_2.png)
    



```python
sns.ecdfplot(x='n4', hue='key', data=df)

sns.displot(x='n4', hue='key', data=df, kind='ecdf')
```




    <seaborn.axisgrid.FacetGrid at 0x24c12adcc40>




    
![png](output_33_1.png)
    



    
![png](output_33_2.png)
    



```python
sns.rugplot(x='n4', hue='key', data=df, height=0.1)
```




    <AxesSubplot:xlabel='n4'>




    
![png](output_34_1.png)
    


## 组图


```python
fg = sns.FacetGrid(df, col='key')
fg.map(sns.kdeplot, 'n1')
fg.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x24c1c850af0>




    
![png](output_36_1.png)
    



```python
pg = sns.PairGrid(df.loc[:,['key', 'n1', 'n2']], hue='key')
pg.map_diag(sns.histplot)
pg.map_offdiag(sns.scatterplot)
pg.add_legend()

sns.pairplot(df.loc[:,['n1', 'n2', 'n3']])
```




    <seaborn.axisgrid.PairGrid at 0x24c20e59190>




    
![png](output_37_1.png)
    



    
![png](output_37_2.png)
    



```python
jg = sns.JointGrid(data=df, x='n4', y='n5')
jg.plot(sns.scatterplot, sns.histplot)

sns.jointplot(data=df, x='n4', y='n5', hue='key', kind='hist')
```




    <seaborn.axisgrid.JointGrid at 0x24c1d4d1c40>




    
![png](output_38_1.png)
    



    
![png](output_38_2.png)
    

