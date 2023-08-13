# notebook环境测试


```python
print('hi')
```

    hi
    

# 快速开始


```python
%matplotlib notebook
import numpy as np
import pandas as pd
import  matplotlib.pyplot as plt

```

#  创建一个系列(series)


```python
import numpy as np
import pandas as pd
s = pd.Series([1,3,5,np.nan,6,8])
print(s)
```

    0    1.0
    1    3.0
    2    5.0
    3    NaN
    4    6.0
    5    8.0
    dtype: float64
    

# 创建一个DataFrame


```python
dates = pd.date_range("20130101",periods=6)
dates
```




    DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
                   '2013-01-05', '2013-01-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list("ABCD"))
df
#np.random.randn函数是NumPy库中的一个函数，用于生成服从标准正态分布（均值为0，方差为1）的随机数。它返回一个具有指定形状的数组，数组中的每个元素都是从标准正态分布中独立抽取的随机数。

# 例如，如果你调用np.random.randn(2, 3)，它将返回一个形状为(2, 3)的数组，其中包含了2行3列共6个随机数，这些随机数都是从标准正态分布中独立抽取的。

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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 通过字典构造Dframe
df2 = pd.DataFrame(
    {
        "A":1.0,
        "B":pd.Timestamp("20130102"),
        "C":pd.Series(1,index=list(range(4)),dtype="float32"),
        "D":np.array([3]*4,dtype="int32"),
        #具体来说，np.array([3]*4, dtype="int32")的意思是创建一个长度为4的Python列表，列表中的每个元素都是3。然后，使用NumPy的np.array函数将这个列表转换为一个NumPy数组。
        "E":pd.Categorical(["test","train","test","train"]),
        "F":"foo",
    }
)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>train</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>train</td>
      <td>foo</td>
    </tr>
  </tbody>
</table>
</div>




```python
#查看类型
df2.dtypes
```




    A           float64
    B    datetime64[ns]
    C           float32
    D             int32
    E          category
    F            object
    dtype: object



# 观察数据


```python
df.head()
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.head(2)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(3)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index
```




    DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
                   '2013-01-05', '2013-01-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df.columns
```




    Index(['A', 'B', 'C', 'D'], dtype='object')



使用df.to_numpy将dataFrame 转换为一个numpy数组,**注意:转换后不含索引和列标题**


```python
df.to_numpy()
```




    array([[ 1.22758391,  0.72044776, -0.61747142, -0.83074213],
           [ 1.40190976, -1.21043107, -0.47093473,  1.40067925],
           [-0.35858254, -0.16188587,  0.05166238, -0.67545128],
           [-1.34181299, -0.48335373, -1.15000955,  0.56127612],
           [-0.75250076,  0.84637494, -1.5164457 , -0.98562954],
           [ 0.39134385,  0.97505718, -0.9916583 ,  0.80782863]])




```python
df2.to_numpy()
```




    array([[1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo']],
          dtype=object)



使用`describe()`来快速描述数据


```python
df.describe()
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.094657</td>
      <td>0.114368</td>
      <td>-0.782476</td>
      <td>0.046327</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.101545</td>
      <td>0.875515</td>
      <td>0.554549</td>
      <td>1.003442</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-1.341813</td>
      <td>-1.210431</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.654021</td>
      <td>-0.402987</td>
      <td>-1.110422</td>
      <td>-0.791919</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.016381</td>
      <td>0.279281</td>
      <td>-0.804565</td>
      <td>-0.057088</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.018524</td>
      <td>0.814893</td>
      <td>-0.507569</td>
      <td>0.746191</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.401910</td>
      <td>0.975057</td>
      <td>0.051662</td>
      <td>1.400679</td>
    </tr>
  </tbody>
</table>
</div>



使用`df.T`来转换行和列


```python
df.T
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
      <th>2013-01-01</th>
      <th>2013-01-02</th>
      <th>2013-01-03</th>
      <th>2013-01-04</th>
      <th>2013-01-05</th>
      <th>2013-01-06</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>1.227584</td>
      <td>1.401910</td>
      <td>-0.358583</td>
      <td>-1.341813</td>
      <td>-0.752501</td>
      <td>0.391344</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.720448</td>
      <td>-1.210431</td>
      <td>-0.161886</td>
      <td>-0.483354</td>
      <td>0.846375</td>
      <td>0.975057</td>
    </tr>
    <tr>
      <th>C</th>
      <td>-0.617471</td>
      <td>-0.470935</td>
      <td>0.051662</td>
      <td>-1.150010</td>
      <td>-1.516446</td>
      <td>-0.991658</td>
    </tr>
    <tr>
      <th>D</th>
      <td>-0.830742</td>
      <td>1.400679</td>
      <td>-0.675451</td>
      <td>0.561276</td>
      <td>-0.985630</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>



使用`sort_index()`按照行或者列排序


```python
df.sort_index(axis=1,ascending=False)
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
      <th>D</th>
      <th>C</th>
      <th>B</th>
      <th>A</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.830742</td>
      <td>-0.617471</td>
      <td>0.720448</td>
      <td>1.227584</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.400679</td>
      <td>-0.470935</td>
      <td>-1.210431</td>
      <td>1.401910</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.675451</td>
      <td>0.051662</td>
      <td>-0.161886</td>
      <td>-0.358583</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.561276</td>
      <td>-1.150010</td>
      <td>-0.483354</td>
      <td>-1.341813</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.985630</td>
      <td>-1.516446</td>
      <td>0.846375</td>
      <td>-0.752501</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.807829</td>
      <td>-0.991658</td>
      <td>0.975057</td>
      <td>0.391344</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_index(axis=0,ascending=False)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_index(axis=0,ascending=True)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>




```python
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>



使用`sort_values()`来根据值排列


```python
df.sort_values(by='B')
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>



这里是对这四个函数的解释和用法：

1. `DataFrame.at[]`：`at`函数用于通过标签（label）来访问和设置DataFrame中的单个元素。它的用法是`df.at[row_label, column_label]`，其中`row_label`是行的标签，`column_label`是列的标签。这个函数具有较高的性能，适用于快速访问和设置单个元素的场景。

示例用法：

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
value = df.at[1, 'A']  # 访问第二行第一列的元素
df.at[2, 'B'] = 7  # 设置第三行第二列的元素为7
```

2. `DataFrame.iat[]`：`iat`函数用于通过整数位置（position）来访问和设置DataFrame中的单个元素。它的用法是`df.iat[row_index, column_index]`，其中`row_index`是行的整数位置，`column_index`是列的整数位置。与`at`函数类似，`iat`函数也具有较高的性能，适用于快速访问和设置单个元素的场景。

示例用法：

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
value = df.iat[1, 0]  # 访问第二行第一列的元素
df.iat[2, 1] = 7  # 设置第三行第二列的元素为7
```

3. `DataFrame.loc[]`：`loc`函数用于通过标签（label）来访问和设置DataFrame中的行或列。它的用法是`df.loc[row_indexer, column_indexer]`，其中`row_indexer`和`column_indexer`可以是单个标签、标签列表、标签范围等。通过`loc`函数，你可以基于标签对DataFrame进行切片、选择行和列、进行布尔索引等操作。

示例用法：

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6], 'C': [7, 8, 9]})
subset = df.loc[1:2, ['A', 'B']]  # 选择第二行到第三行的'A'和'B'列
df.loc[0, 'C'] = 10  # 设置第一行的'C'列为10
```

4. `DataFrame.iloc[]`：`iloc`函数用于通过整数位置（position）来访问和设置DataFrame中的行或列。它的用法与`loc`函数相似，但是`iloc`使用整数位置而不是标签进行定位。通过`iloc`函数，你可以基于整数位置对DataFrame进行切片、选择行和列、进行布尔索引等操作。

示例用法：

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6], 'C': [7, 8, 9]})
subset = df.iloc[1:3, 0:2]  # 选择第二行到第三行的第一列到第二列
df.iloc[0, 2] = 10  # 设置第一行的第三列为10
```

总结起来，`at`和`iat`函数用于快速访问和设置单个元素，`loc`和`iloc`函数用于通过标签或整数位置对DataFrame进行切片、选择行和列等操作。其中，`at`和`iat`函数使用标签或整数位置定位单个元素，而`loc`和`iloc`函数可以使用标签范围、标签列表、整数范围、整数列表等进行定位。

# 获取数据和选择数据


```python
df['A']
```




    2013-01-01    1.227584
    2013-01-02    1.401910
    2013-01-03   -0.358583
    2013-01-04   -1.341813
    2013-01-05   -0.752501
    2013-01-06    0.391344
    Freq: D, Name: A, dtype: float64




```python
#使用切片的方式获取数据
df[0:3]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['20130102':'20130104']
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['20130102',['A','B']]
```




    A    1.401910
    B   -1.210431
    Name: 2013-01-02 00:00:00, dtype: float64




```python
df.loc[dates[0],'A']
```




    1.2275839085960458



**使用布尔表达式**


```python
df[df['A']>0]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df>0]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.400679</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.051662</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.561276</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>NaN</td>
      <td>0.846375</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>NaN</td>
      <td>0.807829</td>
    </tr>
  </tbody>
</table>
</div>




```python
df>0
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



使用isin()来做判断


```python
df2 = df.copy()
df2['E']=["one", "one", "two", "three", "four", "three"]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
      <td>one</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
      <td>one</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
      <td>three</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
      <td>four</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>0.391344</td>
      <td>0.975057</td>
      <td>-0.991658</td>
      <td>0.807829</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2[df2['E'].isin(['two','four'])]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.752501</td>
      <td>0.846375</td>
      <td>-1.516446</td>
      <td>-0.985630</td>
      <td>four</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2['E'].isin(['two','four'])
```




    2013-01-01    False
    2013-01-02    False
    2013-01-03     True
    2013-01-04    False
    2013-01-05     True
    2013-01-06    False
    Freq: D, Name: E, dtype: bool



# 缺失的数据
`pandas`通常用 `np.nan`来表示缺失的数据,`reindex`引允许您更改/添加/删除指定轴上的索引。这将会返回数据的副本：



```python
df1 = df.reindex(index=dates[0:4],columns=list(df.columns)+["E"])
df1.loc[dates[0]:dates[1],'E']=1
df1
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



*可以使用`dropna()`来删除`np.nan`的元素*
在Pandas中，`dropna()`函数用于从数据框（DataFrame）中删除包含缺失值（NaN）的行或列。`how`参数是用来指定删除行或列的条件。

`how`参数有以下几种常见的取值：

- `any`：如果某行或某列中存在任何一个缺失值，则删除该行或该列。
- `all`：只有当某行或某列中的所有值都是缺失值时，才删除该行或该列。

默认情况下，`how`参数的取值为`any`，即如果某行或某列中存在任何一个缺失值，则删除该行或该列。

下面是使用`dropna()`函数的示例：



```python
import pandas as pd

# 创建一个包含缺失值的数据框
data = {'A': [1, 2, None, 4],
        'B': [5, None, 7, 8],
        'C': [9, 10, 11, 12]}
df = pd.DataFrame(data)

# 删除包含缺失值的行
df_dropped = df.dropna()
print(df_dropped)

# 删除包含缺失值的列
df_dropped_cols = df.dropna(axis='columns')
print(df_dropped_cols)
```

         A    B   C
    0  1.0  5.0   9
    3  4.0  8.0  12
        C
    0   9
    1  10
    2  11
    3  12
    

在上述示例中，`dropna()`函数默认使用`how='any'`，因此删除了包含缺失值的行，并返回了一个新的数据框`df_dropped`。另外，也展示了如何使用`axis='columns'`参数删除包含缺失值的列，并返回了一个新的数据框`df_dropped_cols`。


```python
df1.dropna(how='any')
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>



使用`fillna`来填充缺失的数据


```python
df1.fillna(value=5)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>1.227584</td>
      <td>0.720448</td>
      <td>-0.617471</td>
      <td>-0.830742</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>1.401910</td>
      <td>-1.210431</td>
      <td>-0.470935</td>
      <td>1.400679</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.358583</td>
      <td>-0.161886</td>
      <td>0.051662</td>
      <td>-0.675451</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.341813</td>
      <td>-0.483354</td>
      <td>-1.150010</td>
      <td>0.561276</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>



# 操作 Operation


```python
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list("ABCD"))
df['E']=np.random.uniform(low=-1,high=1,size=6)
df['F']=np.random.uniform(low=-1,high=1,size=6)
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.697482</td>
      <td>0.525127</td>
      <td>1.668887</td>
      <td>0.515168</td>
      <td>0.253438</td>
      <td>0.191330</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.049460</td>
      <td>-1.125539</td>
      <td>0.591889</td>
      <td>0.408680</td>
      <td>0.411672</td>
      <td>-0.368798</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.959428</td>
      <td>-1.029904</td>
      <td>-0.763281</td>
      <td>-0.397577</td>
      <td>0.680651</td>
      <td>0.629230</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-0.314417</td>
      <td>-0.502615</td>
      <td>-0.120188</td>
      <td>0.804303</td>
      <td>0.566285</td>
      <td>0.530881</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>0.170488</td>
      <td>0.633975</td>
      <td>1.128840</td>
      <td>-0.097003</td>
      <td>-0.867207</td>
      <td>-0.403868</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.093353</td>
      <td>1.324194</td>
      <td>-0.922883</td>
      <td>0.225852</td>
      <td>-0.429035</td>
      <td>-0.920210</td>
    </tr>
  </tbody>
</table>
</div>




```python
#得到每列的平均值
df.mean(0)
```




    A   -0.307456
    B   -0.029127
    C    0.263877
    D    0.243237
    E    0.102634
    F   -0.056906
    dtype: float64




```python
#得到每行的平均值
df.mean(1)
```




    2013-01-01    0.409411
    2013-01-02   -0.005439
    2013-01-03   -0.306718
    2013-01-04    0.160708
    2013-01-05    0.094204
    2013-01-06   -0.135906
    Freq: D, dtype: float64



`Pandas`中，你可以对具有不同维度的对象进行操作，并且`Pandas`会自动对齐数据，并在需要时进行广播以执行操作。这使得在处理各种数据形状和维度的情况下，`Pandas`更加灵活和方便。


```python
s = pd.Series([1,3,5,np.nan,6,8],index=dates).shift(2)
s
```




    2013-01-01    NaN
    2013-01-02    NaN
    2013-01-03    1.0
    2013-01-04    3.0
    2013-01-05    5.0
    2013-01-06    NaN
    Freq: D, dtype: float64



可以看到，原来的`Series`中的值被向下移动了两个位置。最前面的两个值变成了`NaN`（空值），而后面的值保持不变。这是因为平移操作会将原来位置上的值移到新的位置，并在原来位置上填充`NaN`。

在代码`s.shift(2)`中，`s`是一个`Series`对象，`.shift(2)`表示对`Series`对象进行向下平移两个位置的操作。这意味着原来的`Series`中的值会被向下移动两个位置，并在前面填充`NaN`。


```python
df.sub(s,axis='index') #从df中减去一个值
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-1.959428</td>
      <td>-2.029904</td>
      <td>-1.763281</td>
      <td>-1.397577</td>
      <td>-0.319349</td>
      <td>-0.370770</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-3.314417</td>
      <td>-3.502615</td>
      <td>-3.120188</td>
      <td>-2.195697</td>
      <td>-2.433715</td>
      <td>-2.469119</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-4.829512</td>
      <td>-4.366025</td>
      <td>-3.871160</td>
      <td>-5.097003</td>
      <td>-5.867207</td>
      <td>-5.403868</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



`apply()`函数允许用户为数据定义一个函数应用至数据


```python
df.apply(np.cumsum)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.697482</td>
      <td>0.525127</td>
      <td>1.668887</td>
      <td>0.515168</td>
      <td>0.253438</td>
      <td>0.191330</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>-0.648023</td>
      <td>-0.600412</td>
      <td>2.260776</td>
      <td>0.923848</td>
      <td>0.665109</td>
      <td>-0.177468</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-1.607451</td>
      <td>-1.630316</td>
      <td>1.497495</td>
      <td>0.526271</td>
      <td>1.345760</td>
      <td>0.451762</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.921868</td>
      <td>-2.132930</td>
      <td>1.377307</td>
      <td>1.330574</td>
      <td>1.912045</td>
      <td>0.982643</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-1.751381</td>
      <td>-1.498955</td>
      <td>2.506147</td>
      <td>1.233571</td>
      <td>1.044838</td>
      <td>0.578775</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-1.844733</td>
      <td>-0.174762</td>
      <td>1.583264</td>
      <td>1.459423</td>
      <td>0.615802</td>
      <td>-0.341435</td>
    </tr>
  </tbody>
</table>
</div>



`np.cumsum()`函数是NumPy中的一个函数，用于计算给定数组的累积和。累积和是指从数组的第一个元素开始，将每个元素与前面所有元素的和相加得到的新数组。

函数的语法如下：

```python
np.cumsum(a, axis=None, dtype=None)
```

参数说明：

- `a`：输入的数组。
- `axis`：指定计算累积和的轴。默认为`None`，表示将数组展开为一维数组后计算累积和。
- `dtype`：输出的数据类型。如果未提供，将使用输入数组的数据类型。

下面是一个示例，展示了如何使用`np.cumsum()`函数：

```python
import numpy as np

# 创建一个一维数组
arr = np.array([1, 2, 3, 4, 5])

# 计算累积和
cumulative_sum = np.cumsum(arr)

print(cumulative_sum)
```

输出结果：

```
[ 1  3  6 10 15]
```

在上述示例中，我们创建了一个一维数组 `arr`，包含了整数值。然后，我们使用 `np.cumsum()` 函数计算了 `arr` 的累积和，并将结果存储在变量 `cumulative_sum` 中。最后，我们打印出了累积和数组。

需要注意的是，`np.cumsum()`函数也可以用于多维数组，通过指定 `axis` 参数来计算指定轴方向的累积和。对于多维数组，函数会沿着指定轴的方向将每个元素与前面所有元素的和相加计算累积和。


```python
df.apply(lambda x:x.max()-x.min())
```




    A    1.129916
    B    2.449733
    C    2.591769
    D    1.201879
    E    1.547859
    F    1.549440
    dtype: float64



直方图的应用


```python
s = pd.Series(np.random.randint(0, 7, size=10))
s
```




    0    0
    1    2
    2    2
    3    2
    4    6
    5    2
    6    6
    7    5
    8    2
    9    4
    dtype: int32




```python
s.value_counts()#统计频率
```




    2    5
    6    2
    0    1
    5    1
    4    1
    Name: count, dtype: int64



*字符串方法*


```python
s = pd.Series(["A", "B", "C", "Aaba", "Baca", np.nan, "CABA", "dog", "cat"])
s.str.lower()
```




    0       a
    1       b
    2       c
    3    aaba
    4    baca
    5     NaN
    6    caba
    7     dog
    8     cat
    dtype: object



# 合并数据


```python
df = pd.DataFrame(np.random.randn(10,4))
df
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.802180</td>
      <td>-0.682895</td>
      <td>-2.581830</td>
      <td>-1.173737</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.444665</td>
      <td>-0.689470</td>
      <td>0.270696</td>
      <td>1.556617</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.339526</td>
      <td>-0.428269</td>
      <td>-1.030391</td>
      <td>-0.063919</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.691298</td>
      <td>-0.347070</td>
      <td>-0.473780</td>
      <td>0.694776</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.269460</td>
      <td>0.752581</td>
      <td>0.862169</td>
      <td>-1.158543</td>
    </tr>
    <tr>
      <th>5</th>
      <td>-1.868742</td>
      <td>0.505397</td>
      <td>0.885893</td>
      <td>0.888626</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.528516</td>
      <td>0.909717</td>
      <td>-1.214030</td>
      <td>0.422796</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0.518792</td>
      <td>0.197425</td>
      <td>0.107369</td>
      <td>-0.656157</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-0.243101</td>
      <td>1.616426</td>
      <td>0.926505</td>
      <td>0.358935</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0.372372</td>
      <td>-0.067459</td>
      <td>1.203966</td>
      <td>0.196755</td>
    </tr>
  </tbody>
</table>
</div>




```python
#分割成几个部分
pieces = [df[:3],df[3:7],df[7:]]
pd.concat(pieces)
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.802180</td>
      <td>-0.682895</td>
      <td>-2.581830</td>
      <td>-1.173737</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.444665</td>
      <td>-0.689470</td>
      <td>0.270696</td>
      <td>1.556617</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.339526</td>
      <td>-0.428269</td>
      <td>-1.030391</td>
      <td>-0.063919</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.691298</td>
      <td>-0.347070</td>
      <td>-0.473780</td>
      <td>0.694776</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.269460</td>
      <td>0.752581</td>
      <td>0.862169</td>
      <td>-1.158543</td>
    </tr>
    <tr>
      <th>5</th>
      <td>-1.868742</td>
      <td>0.505397</td>
      <td>0.885893</td>
      <td>0.888626</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.528516</td>
      <td>0.909717</td>
      <td>-1.214030</td>
      <td>0.422796</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0.518792</td>
      <td>0.197425</td>
      <td>0.107369</td>
      <td>-0.656157</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-0.243101</td>
      <td>1.616426</td>
      <td>0.926505</td>
      <td>0.358935</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0.372372</td>
      <td>-0.067459</td>
      <td>1.203966</td>
      <td>0.196755</td>
    </tr>
  </tbody>
</table>
</div>



*在`Pandas`中操作`DataFrame`时，添加列相对较快，但添加行需要进行复制操作，可能会比较耗费资源。因此，建议通过将预先构建好的记录列表传递给`DataFrame`构造函数来创建`DataFrame`，而不是通过迭代地将记录逐个添加到其中。*

*`join`*操作


```python
left = pd.DataFrame(
    {
        "key":["foo","foo"],
        'lval':[1,2],
    }
)
left
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
      <th>key</th>
      <th>lval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
right = pd.DataFrame(
    {
        'key':['foo','foo'],
        'rval':[4,5],
    }
)
right
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
      <th>key</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(left,right,on='key')
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
      <th>key</th>
      <th>lval</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>foo</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



合并后的`DataFrame`对象` merged `包含了三列： `"key"、"lval" `和` "rval"`。由于在 `left `和 `right `中的 `"key" `列有相同的值，所以根据 `"key" `列进行合并时，每个匹配的组合都会生成一行。
这个例子展示了基于相同键值进行合并时的典型情况。在实际应用中，根据具体的数据和分析任务，可以选择不同的连接方式（如内连接、外连接、左连接或右连接），以及不同的连接键，以满足数据处理和分析的要求。


```python
left = pd.DataFrame({"key": ["foo", "bar"], "lval": [1, 2]})

right = pd.DataFrame({"key": ["foo", "bar"], "rval": [4, 5]})
pd.merge(left, right, on="key")
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
      <th>key</th>
      <th>lval</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>bar</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



# 分类
`groupby` 是 Pandas 中用于进行分组操作的一个重要函数。它允许你按照一个或多个列的值将数据集分组，并对每个组应用相应的聚合函数。

`groupby` 的基本用法如下：

```python
grouped = dataframe.groupby(by)
```

其中，`dataframe` 是一个 Pandas DataFrame 对象，`by` 是指定分组依据的列名或列名的列表。

`groupby` 的常见用法有以下几个方面：

**1. 分组并应用聚合函数：**

你可以使用 `groupby` 结合聚合函数对每个组进行计算。例如，你可以计算每个组的平均值、总和、最大值、最小值等。

```python
grouped = dataframe.groupby('column')
grouped.mean()  # 计算每个组的平均值
grouped.sum()   # 计算每个组的总和
grouped.max()   # 计算每个组的最大值
grouped.min()   # 计算每个组的最小值
```

**2. 迭代分组：**

你可以使用 `groupby` 进行迭代，遍历每个分组及其对应的数据。

```python
grouped = dataframe.groupby('column')
for group_name, group_data in grouped:
    # 处理每个分组的数据
    print(group_name)
    print(group_data)
```

**3. 多列分组：**

除了使用单个列进行分组，你还可以使用多个列进行分组。这样将根据指定的多个列的值对数据进行分组。

```python
grouped = dataframe.groupby(['column1', 'column2'])
grouped.mean()  # 计算每个组的平均值
```

**4. 自定义聚合函数：**

除了使用内置的聚合函数，你还可以自定义聚合函数来应用于每个组。

```python
def custom_agg_func(data):
    # 自定义聚合计算逻辑
    return result

grouped = dataframe.groupby('column')
grouped.agg(custom_agg_func)  # 应用自定义聚合函数
```

这些只是 `groupby` 函数的一些常见用法。它提供了强大的功能，可以根据指定的列对数据进行分组，并灵活地应用聚合函数。这样可以方便地进行数据分析、统计和摘要。


```python
df = pd.DataFrame(
    {
        "A": ["foo", "bar", "foo", "bar", "foo", "bar", "foo", "foo"],
        "B": ["one", "one", "two", "three", "two", "two", "one", "three"],
        "C": np.random.randn(8),
        "D": np.random.randn(8),
    }
)
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>one</td>
      <td>-2.560372</td>
      <td>-0.738076</td>
    </tr>
    <tr>
      <th>1</th>
      <td>bar</td>
      <td>one</td>
      <td>0.809945</td>
      <td>1.097797</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>two</td>
      <td>0.592109</td>
      <td>1.090139</td>
    </tr>
    <tr>
      <th>3</th>
      <td>bar</td>
      <td>three</td>
      <td>0.348052</td>
      <td>-2.087217</td>
    </tr>
    <tr>
      <th>4</th>
      <td>foo</td>
      <td>two</td>
      <td>-1.395620</td>
      <td>-0.124606</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bar</td>
      <td>two</td>
      <td>1.112880</td>
      <td>0.148425</td>
    </tr>
    <tr>
      <th>6</th>
      <td>foo</td>
      <td>one</td>
      <td>1.019631</td>
      <td>-0.052559</td>
    </tr>
    <tr>
      <th>7</th>
      <td>foo</td>
      <td>three</td>
      <td>-0.564069</td>
      <td>0.268908</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 使用groupby
df_new=df.groupby("A")
df_new.groups

```




    {'bar': [1, 3, 5], 'foo': [0, 2, 4, 6, 7]}




```python
df.groupby("A")[["C", "D"]].sum()
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
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bar</th>
      <td>2.270876</td>
      <td>-0.840995</td>
    </tr>
    <tr>
      <th>foo</th>
      <td>-2.908321</td>
      <td>0.443807</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.groupby(["A", "B"]).sum()
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
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">bar</th>
      <th>one</th>
      <td>0.809945</td>
      <td>1.097797</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.348052</td>
      <td>-2.087217</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.112880</td>
      <td>0.148425</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">foo</th>
      <th>one</th>
      <td>-1.540741</td>
      <td>-0.790635</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.564069</td>
      <td>0.268908</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.803511</td>
      <td>0.965533</td>
    </tr>
  </tbody>
</table>
</div>




```python
tuples = list(
    zip(
        ["bar", "bar", "baz", "baz", "foo", "foo", "qux", "qux"],
        ["one", "two", "one", "two", "one", "two", "one", "two"],
    )
)
index = pd.MultiIndex.from_tuples(tuples, names=["first", "second"])
df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=["A", "B"])
df2 = df[:4]
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
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>2.011191</td>
      <td>1.784123</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.436979</td>
      <td>0.651628</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>0.132118</td>
      <td>-1.484787</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.606706</td>
      <td>0.827361</td>
    </tr>
  </tbody>
</table>
</div>



这段代码使用 Pandas 创建了一个多级索引（MultiIndex）的 DataFrame，并对其进行了切片操作。让我逐行解释这段代码的含义：

```python
tuples = list(
    zip(
        ["bar", "bar", "baz", "baz", "foo", "foo", "qux", "qux"],
        ["one", "two", "one", "two", "one", "two", "one", "two"],
    )
)
```

这段代码创建了一个由两个列表组成的元组列表。每个元组包含两个元素，分别是 \["bar", "bar", "baz", "baz", "foo", "foo", "qux", "qux"\] 和 \["one", "two", "one", "two", "one", "two", "one", "two"\]。这些元组将用作 DataFrame 的多级索引。

```python
index = pd.MultiIndex.from_tuples(tuples, names=["first", "second"])
```

这一行代码使用 `pd.MultiIndex.from_tuples()` 函数将元组列表转换为多级索引对象。`names=["first", "second"]` 为多级索引的层级名称，分别命名为 "first" 和 "second"。

```python
df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=["A", "B"])
```

这段代码使用 `pd.DataFrame()` 创建了一个具有多级索引的 DataFrame。`np.random.randn(8, 2)` 生成一个 8 行 2 列的随机数数组，作为 DataFrame 的数据。`index=index` 将之前创建的多级索引对象作为 DataFrame 的索引。`columns=["A", "B"]` 将列命名为 "A" 和 "B"。

最后，代码中的 `df2 = df[:4]` 执行了切片操作，将 DataFrame `df` 的前四行赋值给了 DataFrame `df2`。

因此，`df2` 是一个包含了前四行数据的 DataFrame，它继承了 `df` 的多级索引和列标签。

-----------------------------------------------------------------------------------------------------
其中`zip` 是 Python 内置函数之一，用于将多个可迭代对象（如列表、元组等）中的元素按位置进行配对。它将每个可迭代对象中相同位置的元素组合成一个元组，并返回一个可迭代的 zip 对象。

在给定的代码中，`zip` 函数被用于将两个列表配对为一个元组列表。让我们来看一下代码中的具体用法：

```python
tuples = list(
    zip(
        ["bar", "bar", "baz", "baz", "foo", "foo", "qux", "qux"],
        ["one", "two", "one", "two", "one", "two", "one", "two"],
    )
)
```

这段代码使用了两个列表：

- 第一个列表 `["bar", "bar", "baz", "baz", "foo", "foo", "qux", "qux"]` 包含了字符串元素。
- 第二个列表 `["one", "two", "one", "two", "one", "two", "one", "two"]` 同样包含了字符串元素。

`zip` 函数将这两个列表中相同位置的元素进行配对，并返回一个 zip 对象。然后，通过 `list()` 函数将 zip 对象转换为一个元组列表 `tuples`。

`zip` 函数的配对规则是按照索引位置进行配对。也就是说，将第一个列表的第一个元素与第二个列表的第一个元素配对，依此类推。

在给定的例子中，`zip` 函数生成了以下元组列表：

```python
[("bar", "one"), ("bar", "two"), ("baz", "one"), ("baz", "two"), ("foo", "one"), ("foo", "two"), ("qux", "one"), ("qux", "two")]
```

这些元组将在后续的代码中用作多级索引的构建。


```python
stacked  = df2.stack()
stacked
```




    first  second   
    bar    one     A    2.011191
                   B    1.784123
           two     A   -0.436979
                   B    0.651628
    baz    one     A    0.132118
                   B   -1.484787
           two     A    0.606706
                   B    0.827361
    dtype: float64




```python
stacked.unstack()
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
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>2.011191</td>
      <td>1.784123</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.436979</td>
      <td>0.651628</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>0.132118</td>
      <td>-1.484787</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.606706</td>
      <td>0.827361</td>
    </tr>
  </tbody>
</table>
</div>




```python
stacked.unstack(1)
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
      <th>second</th>
      <th>one</th>
      <th>two</th>
    </tr>
    <tr>
      <th>first</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>A</th>
      <td>2.011191</td>
      <td>-0.436979</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1.784123</td>
      <td>0.651628</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>A</th>
      <td>0.132118</td>
      <td>0.606706</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-1.484787</td>
      <td>0.827361</td>
    </tr>
  </tbody>
</table>
</div>




```python
stacked.unstack(2)
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
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>first</th>
      <th>second</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>2.011191</td>
      <td>1.784123</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.436979</td>
      <td>0.651628</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">baz</th>
      <th>one</th>
      <td>0.132118</td>
      <td>-1.484787</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.606706</td>
      <td>0.827361</td>
    </tr>
  </tbody>
</table>
</div>



*数据透视表*


```python
df = pd.DataFrame(
    {
        "A": ["one", "one", "two", "three"] * 3,
        "B": ["A", "B", "C"] * 4,
        "C": ["foo", "foo", "foo", "bar", "bar", "bar"] * 2,
        "D": np.random.randn(12),
        "E": np.random.randn(12),
    }
)
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>one</td>
      <td>A</td>
      <td>foo</td>
      <td>-0.204743</td>
      <td>-1.128233</td>
    </tr>
    <tr>
      <th>1</th>
      <td>one</td>
      <td>B</td>
      <td>foo</td>
      <td>-1.552080</td>
      <td>-0.173445</td>
    </tr>
    <tr>
      <th>2</th>
      <td>two</td>
      <td>C</td>
      <td>foo</td>
      <td>0.695468</td>
      <td>1.248131</td>
    </tr>
    <tr>
      <th>3</th>
      <td>three</td>
      <td>A</td>
      <td>bar</td>
      <td>-0.165849</td>
      <td>0.085830</td>
    </tr>
    <tr>
      <th>4</th>
      <td>one</td>
      <td>B</td>
      <td>bar</td>
      <td>0.498267</td>
      <td>-1.104799</td>
    </tr>
    <tr>
      <th>5</th>
      <td>one</td>
      <td>C</td>
      <td>bar</td>
      <td>0.257877</td>
      <td>0.138203</td>
    </tr>
    <tr>
      <th>6</th>
      <td>two</td>
      <td>A</td>
      <td>foo</td>
      <td>1.150579</td>
      <td>-0.922050</td>
    </tr>
    <tr>
      <th>7</th>
      <td>three</td>
      <td>B</td>
      <td>foo</td>
      <td>-0.579644</td>
      <td>-1.076967</td>
    </tr>
    <tr>
      <th>8</th>
      <td>one</td>
      <td>C</td>
      <td>foo</td>
      <td>-0.932115</td>
      <td>-0.611634</td>
    </tr>
    <tr>
      <th>9</th>
      <td>one</td>
      <td>A</td>
      <td>bar</td>
      <td>1.947501</td>
      <td>-1.379133</td>
    </tr>
    <tr>
      <th>10</th>
      <td>two</td>
      <td>B</td>
      <td>bar</td>
      <td>-0.538665</td>
      <td>1.105313</td>
    </tr>
    <tr>
      <th>11</th>
      <td>three</td>
      <td>C</td>
      <td>bar</td>
      <td>-0.438790</td>
      <td>0.670351</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.pivot_table(df,values='D',index=["A","B"],columns=['C'])
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
      <th>C</th>
      <th>bar</th>
      <th>foo</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">one</th>
      <th>A</th>
      <td>1.947501</td>
      <td>-0.204743</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.498267</td>
      <td>-1.552080</td>
    </tr>
    <tr>
      <th>C</th>
      <td>0.257877</td>
      <td>-0.932115</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">three</th>
      <th>A</th>
      <td>-0.165849</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>B</th>
      <td>NaN</td>
      <td>-0.579644</td>
    </tr>
    <tr>
      <th>C</th>
      <td>-0.438790</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">two</th>
      <th>A</th>
      <td>NaN</td>
      <td>1.150579</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.538665</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>C</th>
      <td>NaN</td>
      <td>0.695468</td>
    </tr>
  </tbody>
</table>
</div>



这行代码使用了 Pandas 的 `pivot_table` 函数来创建一个透视表。让我逐个解释该代码的参数：

- `df`：这是一个 DataFrame 对象，代表源数据集。
- `values='D'`：这是要在透视表中聚合的数值列。在这个例子中，聚合的数值列是名为 'D' 的列。
- `index=["A","B"]`：这是用作透视表行索引的列。在这个例子中，行索引由 'A' 和 'B' 两列组成。
- `columns=['C']`：这是用作透视表列索引的列。在这个例子中，列索引由 'C' 列组成。

这行代码的作用是根据给定的数据和设置创建一个透视表。透视表将根据 'A' 和 'B' 列的唯一值组合创建行索引，根据 'C' 列的唯一值创建列索引，然后在 'D' 列上进行聚合计算。

透视表将使用指定的聚合函数（默认为平均值）对 'D' 列的值进行计算，并将计算结果填充到透视表的对应单元格中。

请注意，代码中的聚合函数没有显式指定，因此将使用默认的聚合函数。如果你需要使用其他聚合函数（如求和、计数等），可以通过 `aggfunc` 参数进行指定。

# 时间序列
Pandas 在频率转换（例如，将秒级数据转换为每5分钟的数据）期间具有简单、强大和高效的功能，用于执行重采样操作。这在金融应用中非常常见，但不仅限于金融应用。


```python
rng = pd.date_range('1/1/2012',periods=100,freq='S')
print(rng)
ts = pd.Series(np.random.randint(0,500,len(rng)),index=rng)
print(ts)
ts.resample('5Min').sum()
```

    DatetimeIndex(['2012-01-01 00:00:00', '2012-01-01 00:00:01',
                   '2012-01-01 00:00:02', '2012-01-01 00:00:03',
                   '2012-01-01 00:00:04', '2012-01-01 00:00:05',
                   '2012-01-01 00:00:06', '2012-01-01 00:00:07',
                   '2012-01-01 00:00:08', '2012-01-01 00:00:09',
                   '2012-01-01 00:00:10', '2012-01-01 00:00:11',
                   '2012-01-01 00:00:12', '2012-01-01 00:00:13',
                   '2012-01-01 00:00:14', '2012-01-01 00:00:15',
                   '2012-01-01 00:00:16', '2012-01-01 00:00:17',
                   '2012-01-01 00:00:18', '2012-01-01 00:00:19',
                   '2012-01-01 00:00:20', '2012-01-01 00:00:21',
                   '2012-01-01 00:00:22', '2012-01-01 00:00:23',
                   '2012-01-01 00:00:24', '2012-01-01 00:00:25',
                   '2012-01-01 00:00:26', '2012-01-01 00:00:27',
                   '2012-01-01 00:00:28', '2012-01-01 00:00:29',
                   '2012-01-01 00:00:30', '2012-01-01 00:00:31',
                   '2012-01-01 00:00:32', '2012-01-01 00:00:33',
                   '2012-01-01 00:00:34', '2012-01-01 00:00:35',
                   '2012-01-01 00:00:36', '2012-01-01 00:00:37',
                   '2012-01-01 00:00:38', '2012-01-01 00:00:39',
                   '2012-01-01 00:00:40', '2012-01-01 00:00:41',
                   '2012-01-01 00:00:42', '2012-01-01 00:00:43',
                   '2012-01-01 00:00:44', '2012-01-01 00:00:45',
                   '2012-01-01 00:00:46', '2012-01-01 00:00:47',
                   '2012-01-01 00:00:48', '2012-01-01 00:00:49',
                   '2012-01-01 00:00:50', '2012-01-01 00:00:51',
                   '2012-01-01 00:00:52', '2012-01-01 00:00:53',
                   '2012-01-01 00:00:54', '2012-01-01 00:00:55',
                   '2012-01-01 00:00:56', '2012-01-01 00:00:57',
                   '2012-01-01 00:00:58', '2012-01-01 00:00:59',
                   '2012-01-01 00:01:00', '2012-01-01 00:01:01',
                   '2012-01-01 00:01:02', '2012-01-01 00:01:03',
                   '2012-01-01 00:01:04', '2012-01-01 00:01:05',
                   '2012-01-01 00:01:06', '2012-01-01 00:01:07',
                   '2012-01-01 00:01:08', '2012-01-01 00:01:09',
                   '2012-01-01 00:01:10', '2012-01-01 00:01:11',
                   '2012-01-01 00:01:12', '2012-01-01 00:01:13',
                   '2012-01-01 00:01:14', '2012-01-01 00:01:15',
                   '2012-01-01 00:01:16', '2012-01-01 00:01:17',
                   '2012-01-01 00:01:18', '2012-01-01 00:01:19',
                   '2012-01-01 00:01:20', '2012-01-01 00:01:21',
                   '2012-01-01 00:01:22', '2012-01-01 00:01:23',
                   '2012-01-01 00:01:24', '2012-01-01 00:01:25',
                   '2012-01-01 00:01:26', '2012-01-01 00:01:27',
                   '2012-01-01 00:01:28', '2012-01-01 00:01:29',
                   '2012-01-01 00:01:30', '2012-01-01 00:01:31',
                   '2012-01-01 00:01:32', '2012-01-01 00:01:33',
                   '2012-01-01 00:01:34', '2012-01-01 00:01:35',
                   '2012-01-01 00:01:36', '2012-01-01 00:01:37',
                   '2012-01-01 00:01:38', '2012-01-01 00:01:39'],
                  dtype='datetime64[ns]', freq='S')
    2012-01-01 00:00:00    122
    2012-01-01 00:00:01    144
    2012-01-01 00:00:02    337
    2012-01-01 00:00:03    178
    2012-01-01 00:00:04    220
                          ... 
    2012-01-01 00:01:35     48
    2012-01-01 00:01:36    119
    2012-01-01 00:01:37    464
    2012-01-01 00:01:38    235
    2012-01-01 00:01:39    410
    Freq: S, Length: 100, dtype: int32
    




    2012-01-01    24807
    Freq: 5T, dtype: int32



这段代码使用 Pandas 库来生成一个时间序列数据，并对数据进行重采样。让我逐行解释代码的含义：

```python
rng = pd.date_range('1/1/2012', periods=100, freq='S')
print(rng)
```

这段代码创建了一个时间范围（`rng`），从 '1/1/2012' 开始，每秒钟生成一个时间戳，一共生成了100个时间戳。`pd.date_range()` 函数用于生成时间范围，通过指定起始日期、生成的时间段数以及频率（`freq`）来确定时间戳的间隔。

```python
ts = pd.Series(np.random.randint(0, 500, len(rng)), index=rng)
print(ts)
```

这段代码创建了一个 Pandas 的 Series 对象（`ts`），其中包含了随机生成的整数值，并以之前生成的时间范围作为索引。`np.random.randint()` 函数用于生成给定范围内的随机整数。`len(rng)` 表示生成的随机数的数量与时间范围的长度相同。

```python
ts.resample('5Min').sum()
```

这段代码对之前创建的时间序列数据进行重采样。`resample()` 方法用于将时间序列数据从一个频率转换为另一个频率。在这个例子中，它将时间序列数据从每秒钟的频率转换为每5分钟的频率。

`.sum()` 是一个聚合函数，它对每个重采样时间段内的值进行求和计算。

最后，这段代码会打印出重采样后的时间序列数据，其中每5分钟的时间段内的值是原始数据对应时间段内的值的总和。



```python
#Series.tz_localize() localizes a time series to a time zone:
rng = pd.date_range('3/6/2012 00:00',periods=5,freq='D')
ts = pd.Series(np.random.randn(len(rng)),rng)
ts
```




    2012-03-06   -0.072064
    2012-03-07   -1.270414
    2012-03-08   -0.219330
    2012-03-09    1.018295
    2012-03-10    0.904882
    Freq: D, dtype: float64




```python
ts_utc = ts.tz_localize("UTC")
ts_utc
```




    2012-03-06 00:00:00+00:00   -0.072064
    2012-03-07 00:00:00+00:00   -1.270414
    2012-03-08 00:00:00+00:00   -0.219330
    2012-03-09 00:00:00+00:00    1.018295
    2012-03-10 00:00:00+00:00    0.904882
    Freq: D, dtype: float64




```python
#Series.tz_convert() converts a timezones aware time series to another time zone:
ts_utc.tz_convert("US/Eastern")
```




    2012-03-05 19:00:00-05:00   -0.072064
    2012-03-06 19:00:00-05:00   -1.270414
    2012-03-07 19:00:00-05:00   -0.219330
    2012-03-08 19:00:00-05:00    1.018295
    2012-03-09 19:00:00-05:00    0.904882
    Freq: D, dtype: float64




```python
#Converting between time span representations:
rng = pd.date_range("1/1/2012", periods=5, freq="M")
ts = pd.Series(np.random.randn(len(rng)), index=rng)
ts
```




    2012-01-31   -1.410678
    2012-02-29   -0.722583
    2012-03-31    1.294834
    2012-04-30    0.666620
    2012-05-31   -0.484888
    Freq: M, dtype: float64




```python
ps = ts.to_period()
ps
```




    2012-01   -1.410678
    2012-02   -0.722583
    2012-03    1.294834
    2012-04    0.666620
    2012-05   -0.484888
    Freq: M, dtype: float64




```python
ps.to_timestamp()
```




    2012-01-01   -1.410678
    2012-02-01   -0.722583
    2012-03-01    1.294834
    2012-04-01    0.666620
    2012-05-01   -0.484888
    Freq: MS, dtype: float64



在周期和时间戳之间进行转换，可以使用一些方便的算术函数。在下面的示例中，我们将 $11$ 月结束的季度频率转换为季度末下一个月的上午 $9$ 点：


```python
prng = pd.period_range("1990Q1", "2000Q4", freq="Q-NOV")
prng
#在这个例子中，时间范围从 "1990Q1"（1990年第一季度）开始，到 "2000Q4"（2000年第四季度）结束。而频率参数 freq 被设置为 "Q-NOV"，表示季度频率的结束月份为11月份。
```




    PeriodIndex(['1990Q1', '1990Q2', '1990Q3', '1990Q4', '1991Q1', '1991Q2',
                 '1991Q3', '1991Q4', '1992Q1', '1992Q2', '1992Q3', '1992Q4',
                 '1993Q1', '1993Q2', '1993Q3', '1993Q4', '1994Q1', '1994Q2',
                 '1994Q3', '1994Q4', '1995Q1', '1995Q2', '1995Q3', '1995Q4',
                 '1996Q1', '1996Q2', '1996Q3', '1996Q4', '1997Q1', '1997Q2',
                 '1997Q3', '1997Q4', '1998Q1', '1998Q2', '1998Q3', '1998Q4',
                 '1999Q1', '1999Q2', '1999Q3', '1999Q4', '2000Q1', '2000Q2',
                 '2000Q3', '2000Q4'],
                dtype='period[Q-NOV]')




```python
ts = pd.Series(np.random.randn(len(prng)), prng)
ts
```




    1990Q1   -0.421815
    1990Q2    1.619325
    1990Q3    0.337948
    1990Q4    0.852425
    1991Q1    1.021911
    1991Q2    1.056612
    1991Q3    2.369892
    1991Q4    0.698598
    1992Q1    0.412831
    1992Q2   -0.433981
    1992Q3   -0.469723
    1992Q4   -1.366564
    1993Q1   -1.325320
    1993Q2   -0.837164
    1993Q3   -1.532736
    1993Q4    0.766995
    1994Q1    0.719767
    1994Q2    1.074556
    1994Q3   -0.938306
    1994Q4    0.667705
    1995Q1   -0.675715
    1995Q2   -1.544151
    1995Q3   -0.850746
    1995Q4    0.410846
    1996Q1   -2.490573
    1996Q2    0.564735
    1996Q3    0.043320
    1996Q4    1.028809
    1997Q1   -0.178464
    1997Q2    0.018437
    1997Q3    1.142269
    1997Q4    0.442643
    1998Q1   -1.670793
    1998Q2   -0.597091
    1998Q3    0.966874
    1998Q4   -0.125893
    1999Q1    1.037253
    1999Q2    2.539866
    1999Q3    1.625617
    1999Q4    2.153096
    2000Q1   -0.048592
    2000Q2   -1.257287
    2000Q3   -1.164212
    2000Q4   -0.419758
    Freq: Q-NOV, dtype: float64




```python
ts.index = (prng.asfreq("M", "e") + 1).asfreq("H", "s") + 9
ts.head()
```




    1990-03-01 09:00   -0.421815
    1990-06-01 09:00    1.619325
    1990-09-01 09:00    0.337948
    1990-12-01 09:00    0.852425
    1991-03-01 09:00    1.021911
    Freq: H, dtype: float64



这段代码使用 Pandas 库生成一个随机数的时间序列数据，并对时间索引进行处理。让我逐行解释代码的含义：

```python
prng = pd.period_range("1990Q1", "2000Q4", freq="Q-NOV")
```

这段代码创建了一个季度范围（Period Range），与之前解释的相同，从 "1990Q1" 到 "2000Q4"，使用 "Q-NOV" 作为频率参数。

```python
ts = pd.Series(np.random.randn(len(prng)), prng)
```

这段代码创建了一个 Pandas 的 Series 对象（`ts`），其中包含了随机生成的标准正态分布的随机数，并以之前生成的季度范围作为索引。

```python
ts.index = (prng.asfreq("M", "e") + 1).asfreq("H", "s") + 9
```

这段代码对时间索引进行了处理。首先，`prng.asfreq("M", "e")` 将季度范围的频率转换为每月最后一天的日期范围，其中 "M" 表示月份，而 "e" 表示每月的最后一天。

然后，`(prng.asfreq("M", "e") + 1)` 将每月的最后一天加一天，以获得下一个月的第一天。

接下来，`.asfreq("H", "s")` 将日期范围的频率转换为每小时的时间范围，其中 "H" 表示小时。这将生成每个月的所有小时的时间范围。

最后，`+ 9` 是对时间范围进行偏移，将每个小时的时间范围向前推进9个小时。

通过这些处理，时间索引被转换为每个月所有小时的时间范围，并向前推进了9个小时。

```python
ts.head()
```

这段代码打印出 Series 对象 `ts` 的前几行，以便查看生成的时间序列数据和处理后的时间索引。

通过这段代码，你可以了解到如何生成随机数的时间序列数据，并对时间索引进行灵活的处理和转换。这种处理可以让你根据具体需求调整时间索引的频率和偏移，以适应不同的时间分析场景。

# 分类数据
在 Pandas 中，Categoricals（分类数据）是一种数据类型，用于表示具有有限数量的离散值的列或数组。它在某些情况下可以提供更有效的存储和性能。

Categoricals 可以被看作是具有固定类别的变量，类似于枚举类型。它们通常用于表示具有有限数量的可能取值的列，例如性别（男、女）、地区（东部、西部、南部、北部）或教育程度（初中、高中、大学）等。

使用 Categoricals 数据类型可以带来以下优势：

1. 节省内存：相比于存储字符串或对象类型的列，Categoricals 可以显著减少内存使用。它们的底层实现将类别存储为整数，并使用一个类别编码映射来映射整数到实际类别值。

1. 更快的计算：由于 Categoricals 使用整数编码，可以在许多操作中获得更快的计算速度。例如，排序、分组和连接等操作可以在 Categoricals 上更高效地执行。

1. 易于分析：Categoricals 提供了更直观的方式来处理和分析具有固定类别的数据。它们可以通过 `.cat` 属性访问一些特殊的分类方法和属性，例如 `.cat.categories` 可以获取类别的列表，`.cat.codes` 可以获取整数编码的 Series。

要创建 Categoricals 列，可以使用 `pd.Categorical` 函数来将现有的列或数组转换为分类数据类型。也可以在读取数据时指定数据类型为 Categoricals。

总之，Categoricals 是 Pandas 中用于表示具有有限数量离散值的列或数组的数据类型。它们通过节省内存和提供更快的计算速度来优化数据的存储和处理。


```python
df = pd.DataFrame(
    {
        "id": [1, 2, 3, 4, 5, 6],
        "raw_grade": ["a", "b", "b", "a", "a", "e"]
    }
)
#Converting the raw grades to a categorical data type:
df['grade']=df['raw_grade'].astype('category')
df['grade']
```




    0    a
    1    b
    2    b
    3    a
    4    a
    5    e
    Name: grade, dtype: category
    Categories (3, object): ['a', 'b', 'e']



这段代码使用 Pandas 创建一个 DataFrame，并将某一列的数据类型转换为 Categoricals（分类数据类型）。让我逐行解释代码的含义：

```python
df = pd.DataFrame(
    {
        "id": [1, 2, 3, 4, 5, 6],
        "raw_grade": ["a", "b", "b", "a", "a", "e"]
    }
)
```

这段代码创建了一个 DataFrame（`df`），其中包含两列数据："id" 和 "raw_grade"。"id" 列包含了一些整数值，而 "raw_grade" 列包含了一些字符串值，表示原始的等级。

```python
df['grade'] = df['raw_grade'].astype('category')
```

这段代码将 "raw_grade" 列的数据类型转换为 Categoricals（分类数据类型），并将结果存储在名为 "grade" 的新列中。

`df['raw_grade']` 选择了 "raw_grade" 列的数据，而 `.astype('category')` 将这些数据转换为 Categoricals 数据类型。

通过这个转换，"raw_grade" 列的数据将被重新编码为整数，并使用一个类别映射将整数与原始的等级值相关联。

```python
df['grade']
```

这段代码打印出 DataFrame 中的 "grade" 列，以便查看转换后的结果。

通过这段代码，你可以了解到如何使用 Pandas 将列的数据类型转换为 Categoricals 数据类型。这种转换可以提供更高效的存储和计算，以及更方便的处理和分析具有有限数量离散值的数据。


```python
#Rename the categories to more meaningful names:
new_categories = ['very good','good','very bad']
df['grade']=df['grade'].cat.rename_categories(new_categories)
df['grade']
```




    0    very good
    1         good
    2         good
    3    very good
    4    very good
    5     very bad
    Name: grade, dtype: category
    Categories (3, object): ['very good', 'good', 'very bad']




```python
df["grade"] = df["grade"].cat.set_categories(
    ["very bad", "bad", "medium", "good", "very good"]
)
#重新添加缺少的类别
df['grade']
```




    0    very good
    1         good
    2         good
    3    very good
    4    very good
    5     very bad
    Name: grade, dtype: category
    Categories (5, object): ['very bad', 'bad', 'medium', 'good', 'very good']




```python
# 排序是按照类别中的顺序排序,而不是按照词法顺序排序
df.sort_values(by='grade')
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
      <th>id</th>
      <th>raw_grade</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>e</td>
      <td>very bad</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>b</td>
      <td>good</td>
    </tr>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>a</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>a</td>
      <td>very good</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Grouping by a categorical column also shows empty categories:
df.groupby("grade").size()
```




    grade
    very bad     1
    bad          0
    medium       0
    good         2
    very good    3
    dtype: int64



# 画图


```python
plt.close('all')
```


```python
ts = pd.Series(np.random.randn(1000), index=pd.date_range("1/1/2000", periods=1000))
ts
```




    2000-01-01   -0.711425
    2000-01-02    0.944274
    2000-01-03   -0.633926
    2000-01-04    0.897589
    2000-01-05    0.439313
                    ...   
    2002-09-22   -0.354482
    2002-09-23   -0.416545
    2002-09-24   -0.289728
    2002-09-25    0.527962
    2002-09-26    0.186044
    Freq: D, Length: 1000, dtype: float64



`cumsum()` 是 Pandas 库中的一个函数，用于计算指定轴上元素的累积和（cumulative sum）。

具体来说，`cumsum()` 函数将返回一个具有相同形状的新 Series 或 DataFrame，其中的每个元素是原始 Series 或 DataFrame 对应位置之前所有元素的和。

例如，对于一个 Series，`cumsum()` 将计算每个元素及其之前所有元素的累积和。假设我们有以下 Series：

```
import pandas as pd

s = pd.Series([1, 2, 3, 4, 5])
```

应用 `cumsum()` 后，将得到：

```
0     1
1     3
2     6
3    10
4    15
dtype: int64
```

在上述示例中，第一个元素是 1，第二个元素是前两个元素的和（1 + 2 = 3），第三个元素是前三个元素的和（1 + 2 + 3 = 6），以此类推。

对于 DataFrame，`cumsum()` 函数将按照指定的轴（行或列）计算元素的累积和。

例如，对于以下 DataFrame：

```
import pandas as pd

df = pd.DataFrame({
   'A': [1, 2, 3],
   'B': [4, 5, 6],
   'C': [7, 8, 9]
})
```

应用 `cumsum()` 后，将得到：

```
   A  B   C
0  1  4   7
1  3  9  15
2  6  15 24
```

在上述示例中，第一行是原始 DataFrame 中的第一行，第二行是前两行的累积和，第三行是前三行的累积和。

`cumsum()` 函数在数据分析和时间序列分析等领域经常使用，用于计算累积总和、累积增长或累积变化等指标。


```python
ts = ts.cumsum()
ts.plot()
```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAHgCAYAAAA10dzkAAAAAXNSR0IArs4c6QAAIABJREFUeF7snQV0VEcXx/+4J7i7BgkkSHAJwaVYC6VI8VKkLfBBcbfiFKcUKVSgLdYWgiY4BALBCRJcA8El6Hfmbd5mk91Ndnc27Ev2P+f0lOzOHfnN3Z278+bem+jDhw8fwEICJEACJEACJEACJOA0BBLRAHSateZESYAESIAESIAESEAhQAOQikACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIkQAIkQAIkQAI0AKkDJEACJEACJEACJOBkBGgAOtmCc7okQAIkQAIkQAIkQAOQOkACJEACJEACJEACTkaABqCTLTinSwIk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" width="640">





    <Axes: >




```python
df = pd.DataFrame(
    np.random.randn(1000, 4), index=ts.index, columns=["A", "B", "C", "D"]
)
df = df.cumsum()
plt.figure()

plt.legend()
df.plot()
```


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,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3/9+XHPNNbFnz54YPHjwMb9zBOiYRK5AgAABAgTaTsD+7qACWE4DUz70sXLlyqYIltPArF27NrZs2RIjRoxoThFT3idYzvNXLuXl3HK6l2984xu9LwF/+tOfjlIMy2315SJAfVFyHQIECBAg0F4C9ncHFcASrXIKmJ4TQY8fPz7KhzzKM4PlMmXKlBgzZkysWrWq+b/Lhz7uuOOO+O53vxvPPPNMnHnmmfGBD3yg+f+ddtppfUqqAPWJyZUIECBAgEBbCdjfHVYAX+10CdCrLe7rESBAgACBvID9rQCmUiRAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD9rQCmgidAKT7DBAgQIECgioD93WEFcPny5bFo0aLYuXNnjBs3LpYuXRoTJ048Yrh27doVX/ziF+OHP/xhPPfcc3HWWWfF4sWL49JLL+1TIAWoT0yuRIAAAQIE2krA/u6gArhmzZqYNm1arFixIiZNmtQUuXXr1sXWrVtj+PDhhwRv3759cdFFFzX/dsstt8TIkSPjqaeeitNOO60pj325CFBflFyHAAECBAi0l4D93UEFsJS+CRMmxLJly5qU7d+/P0aNGhWzZs2KOXPmHJK8UhTLs4VbtmyJk08+uV/JFKB+sRkiQIAAAQJVBezvDimA5dm8oUOHxvr162Pq1Km9oZo+fXqUl3k3bNhwSNDKy7ynn356M1f+/cwzz4wrr7wybr755hg8ePBhg7l3794o//VcSoBKydy9e3cMGzasaph9cQIECBAgQKBvAgpghxTAHTt2NC/hbtq0KSZPntx79GfPnh0bN26MzZs3H5KIt73tbbF9+/a46qqr4rrrrott27Y1//P666+PuXPnHjZB8+bNi/nz5x/ybwpg377hXIsAAQIECLSDgALYxQVw7Nix8eKLL8aTTz7Z+4zfnXfe2bws/Oyzz3oGsB2+Q90HAgQI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" width="640">


    No artists with labels found to put in legend.  Note that artists whose label start with an underscore are ignored when legend() is called with no argument.
    


    <IPython.core.display.Javascript object>



<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAHgCAYAAAA10dzkAAAAAXNSR0IArs4c6QAAIABJREFUeF7sXXVc1ecXfijpFhAEC3OzZs/ujtnO9ufMqdPZMWu2Tt2cPWt2d01nd87GwgIRUAFFOn6f816/t7gXbqAS5+yPAffN5/te73PPe85zTJKTk5PBxggwAowAI8AIMAKMACOQbRAwYQKYbZ41b5QRYAQYAUaAEWAEGAGBABNAPgiMACPACDACjAAjwAhkMwSYAGazB87bZQQYAUaAEWAEGAFGgAkgnwFGgBFgBBgBRoARYASyGQJMALPZA+ftMgKMACPACDACjAAjwASQzwAjwAgwAowAI8AIMALZDAEmgNnsgfN2GQFGgBFgBBgBRoARYALIZ4ARYAQYAUaAEWAEGIFshgATwGz2wHm7jAAjwAgwAowAI8AIMAHkM8AIMAKMACPACDACjEA2Q4AJYDZ74LxdRoARYAQYAUaAEWAEmADyGWAEGAFGgBFgBBgBRiCbIcAEMJs9cN4uI8AIMAKMACPACDACTAD5DDACjAAjwAgwAowAI5DNEGACmM0eOG+XEWAEGAFGgBFgBBgBJoB8BhgBRoARYAQYAUaAEchmCDABzGYPnLfLCDACjAAjwAgwAowAE0A+A4wAI8AIMAKMACPACGQzBJgAZrMHzttlBBgBRoARYAQYAUaACSCfAUaAEWAEGAFGgBFgBLIZAkwAs9kD5+0yAowAI8AIMAKMACPABJDPACPACDACjAAjwAgwAtkMASaA2eyB83YZAUaAEWAEGAFGgBFgAshngBFgBBgBRoARYAQYgWyGABPAbPbAebuMACPACDACjAAjwAgwAeQzwAgwAowAI8AIMAKMQDZDgAlgNnvgvF1GgBFgBBgBRoARYASYAPIZYAQYAUaAEWAEGAFGIJshwAQwmz1w3i4jwAgwAowAI8AIMAJMAPkMMAKMACPACDACjAAjkM0QYAKYzR44b5cRYAQYAUaAEWAEGAEmgHwGGAFGgBFgBBgBRoARyGYIMAHMZg+ct8sIMAKMACPACDACjAATQD4DjAAjwAgwAowAI8AIZDMEmABmswfO22UEGAFGgBFgBBgBRoAJIJ8BRoARYAQYAUaAEWAEshkCTACz2QPn7TICjAAjwAgwAowAI8AEkM8AI8AIMAKMACPACDAC2QwBJoDZ7IHzdhkBRoARYAQYAUaAEWACyGeAEWAEGAFGgBFgBBiBbIYAE8Bs9sB5u4wAI8AIMAKMACPACDAB5DPACDACjAAjwAgwAoxANkOACWA2e+C8XUaAEWAEGAFGgBFgBJgA8hlgBBgBRoARYAQYAUYgmyHABDCbPXDeLiPACDACjAAjwAgwAkwA+QwwAowAI8AIMAKMACOQzRBgApjNHjhvlxFgBBgBRoARYAQYASaAfAYYAUaAEWAEGAFGgBHIZggwAcxmD5y3ywgwAowAI8AIMAKMABNAPgOMACPACDACjAAjwAhkMwSYAGazB87bZQQYAUaAEWAEGAFGgAkgnwFGgBFgBBgBRoARYASyGQJMALPZA+ftMgKMACPACDACjAAjwASQzwAjwAgwAowAI8AIMALZDAEmgNnsgfN2GQFGgBFgBBgBRoARYALIZ4ARYAQYAUaAEWAEGIFshgATQCMeeFJSEl6+fAl7e3uYmJgYMRJ3ZQQYAUaAEWAEGIHPhUBycjLev38PLy8vmJqafq5pM9Q8TACNeBwBAQHw8fExYgTuyggwAowAI8AIMAJfCoEXL17A29v7S03/RedlAmgE/BEREXBycgIdIAcHByNG4q6MACPACDACjAAj8LkQePfunXDghIeHw9HR8XNNm6HmYQJoxOOgA0QHh4ggE0AjgOSujAAjwAgwAozAZ0SAP78BJoBGHDg+QEaAx10ZAUaAEWAEGIEvhAB/fjMBNOro8QEyCj7uzAgwAowAI8AIfBEE+PObCaBRB48PkFHwcWdGgBFgBBgBRuCLIMCf30wAjTp4uhwgSjVPSEhAYmKiUXNl9M5mZmYwNzdnOZyM/qB4fYwAI8AIMALQ5fM7q8PEMYBGPOG0DlBcXByCgoIQFRVlxCyZp6uNjQ08PT2RI0eOzLNoXikjwAgwAoxAtkMgrc/v7AAIE0AjnnJqB4hEoh8+fAjyjLm5uQlSlFXFosnLSWQ3NDRUeDoLFSqUbYU1jThO3JURYAQYAUbgMyHABJCvgI06aqkdoJiYGDx58gR58+YFecayg5Gn89mzZ8ifPz+srKyyw5Z5j4wAI8AIMAKZEAEmgEwAjTq2uhDA7ESGJNKbnfZs1AHizowAI8AIMAJfBAEmgEwAjTp4TABV4WMCaNRx4s6MACPACDACnwkBJoBMAI06akwAmQAadYC4MyPACDACjMAXQYAJIBNAow5eViaA58+fR9WqVdGwYUPs379fJ5zYA6gTTNyIEWAEGAFG4AsjwASQCaBRRzArE8AffvgBdnZ2WLFiBe7fvw8vL680sWICmCZE3IARYAQYAUYgAyDABJAJoFHHMKsSwMjISKHnd+XKFUyYMAElS5bEmDFj0sSKCWCaEHEDRoARYAQYgXRGICkqCm/XroNj82Ywc3bGm5UrER8YCLf+/WGRO7fG2ZgAMgE06hjqSwBJLy86/vNXBLG2MNNLg3DlypVYvHgxLl++jH379mHw4MFC0zAtHUMmgEYdJ+7MCDACjAAjoCcCyYmJ8G/WHHH+/sjh6wubMt8gfOs2MQqRP9+jRxDw4wAkvXsHn5UrYPqxUAETQCaAeh411eb6EsCouAR8Nf6wUXMa0vnu5AawyWGuc9cqVaqgXbt2+Omnn0QZO/IGbt26FTVr1kx1DCaAOkPMDRkBRoARYATSAYHwXbsQNGq01pEK7N8H/yZNxeu558+HQ8MG4mcmgEwAjTp+WZEAUrxf8eLFERgYCHd3d4HPgAEDEBERgbVr1zIBNOrEcGdGgBFgBBiB9EQgYMgQvD94SKchHVu0gNfMGUwAP6LFpeB0OjaaG+lLADPDFfCIESMwe/ZsUcJOMlq3paWlqGvs6OioFTH2ABpxmLgrI8AIMAKMgFYEQv9YgOhbt5B73jyY2dnK2z3r1h1RFy/qhJy5hwd8j/wjroHZA8geQJ0OjbZG+hJAoyb7DJ3putfb2xtEAuvXr68y43fffYdhw4ahb9++TAA/w7PgKRgBRoARYARkCCQnJcHvq6/Fz669esF96M9yaB5Wr4GEkBCAnBaJSjH25uZAQkJKCC0sUPTqFbyPiREODbrdcnBwyJZQswfQiMee1Qjgrl270L59e4SEhKTw9I0cORLHjh0TiSHajD2ARhwm7soIMAKMACOQAoGkDx8Q+/gxnrZrL14ztbGB7+FDMHdzQ2JkJB6UKy/+blOhAqIuXRI/29erB1NbW0Ts2iV+ty5dGjF+fkiOiRG/Fzh4ALGurkwAk+l+j80gBLIaAWzWrBmSkpI0Cj9funQJFStWxI0bN4QsjCZjAmjQMeJOjAAjwAgwAloQeNa1m5zYSU2cO36PXOPHI/rWbTxt2xZmrq6wr10b4Vu3iiYeY8YgKSYGoXPnit8LHvsX0XfuIHDgIPG7z19/IalkCSaATAANf99lNQJoOBKynkwAjUWQ+zMCjAAjwAgoI3CvaLEUgFiXKoW8mzbCr9hX4jWbcuVg+VUxhP0tS1QkD6GZa068XrwIJjlywP2nn8TfX/Tpi8iTJ5Fr0iSYNWrIBJAJoOFvNiaAqtgxATT8LHFPRoARYAQYAVUESOD5fpmy8j96Tp+OoNGjYebkJLJ5idCRuQ3+CVZfF8eLPn3g0r07PEYM1wjlq1+nIGz9erj27g2rH3oyAWQCaPhbjgkgE0DDTw/3ZAQYAUaAEUgNgbiAQDyuWxcmlpYo8t91JBMhLFtOdLGvVxfvjxyFQ+NG8JozByampkiKjoaptbXWId+sXIWQWbNgVaIErPr0hle9epwEwkfQMASYADIBNOzkcC9GgBFgBBiB1BBIePNGCDgnhofD1NERRS5eEM0fVKuGxNDX8q4Uz2dXtYpOYL47/A8CP14HRyYmosKjh0wAdUKOG6VAgAkgE0B+WzACjAAjwAikPwKvly9H6G+yJA6yYn73xP+fduqM6KtX5X8vdOY0zHPm1GkB0bfv4GmbNqItE0DWAdTp0GhrxASQCaBRB4g7MwKMACPACGhE4Fn3Hoi6IPP6WRYtigK7doqfX44Zi4gdO2R9TE1R9NZNmCgVLkgNzoSwMDz8tjITwI8gsQ6gEW8+JoBMAI04PtyVEWAEGAFGQAMClPzxoGIlJMfHw6l9e7h07wbL/PlFy9dLliJ0/nzxM2kBFjp9Si8Mg6fPQNT167Ds2RO5GzbgK2C90OPGcgSYADIB5LcDI8AIMAKMQPoiEHn6NF706g0LLy/4/nsUJiYm8gmirl3Ds46dxO8WefKg4D+HDZqcS8HxFbBBB0fqxASQCaBRB4g7MwKMQJZAIGzzFqEv5zVrJszs7D7rnuKDQ2Du7qZCkj7rAj7BZG9Wr0bIjJmwb9gQ3vPnqcxAtSsk/T+qClLkmiIeUJ+lMAFkAqjPeUnRlgkgE0CjDhB3ZgQYgUyPQPSNG3javoPYR+758+DQsOFn21PE/v14OXQY3AYPRs6+fT7bvJ96ouDp0/F2zd9w+d//NGr6kYcwYNBPcB8yBC5duxi0HCaATAANOjjsAdQMGwtBG3WcuDMjwAhkMgSS4uLwtG07xN6/L1aea8J4OH///WfbxYMqVZH45o2YT8qS/WyTf8KJiNy9/+cfUdJNG8FLTkiAibm5watgAsgE0ODDQx2zqgewe/fuWLNmjRwbFxcXlC9fHrNmzdJaB5gaMwE06jhxZ0aAEchkCIRt2oRXEyfJV51z0EC49e//2Xbh37wFYh88EPORULKpldVnm/tTTvSkXXvE3LwJ7z8XwL5u3U8yFRNAJoBGHaysTACDg4OxatUqgc+rV68wbtw43Lx5E8+fP9eKGRNAo44Td2YEGIFMhgBd/dIVsGTOnTsj17ixn20XElGiCXNNnADnDrKr6Mxsie/e4WG16kiOjUWBvXtgWajQJ9kOE0AmgEYdrKxMAMPDw7Fr1y45PmfOnEG1atUQEhICNzc3jbgxATTqOHFnRoARyCQIkEzJs85dEHP3rlgxxaq9XbkSDk2aIPdvc+S7SI6LQ/ju3bApWw6WBWQyJullypp2NKZt9WrIs2xZeg3/xcaR4hpzFPRFgb17P1lyCxPAbEIAZ8yYgdGjR+Onn37C/I/6QURWhg4dik2bNiE2NhYNGjTAokWL4OHhofPB15sAJicD8VE6j59uDS1sAKU0+rTGpStgZQIYGRmJYcOG4d9//8X9+/dhamrKBDAtEPl1RoARyLIIhG/fgaCxMk+fZZEicO35P7wcMRK2lSsjz8oV4u9xAQF4XLee+NmqeHHk37Y1XfF4vWQJQuf/Lh/T1M4OhS9e0FkUOV0Xk06Dxb98iaBfxuPD2bNwbNkSXtOnpdPIKYdhApgNCODly5fRrl07ODg4oFatWnIC2K9fP+zfvx+rV6+Go6MjBgwYIIjN2bNndT5wehPAuA/ANC+dx0+3hmNeAjlsdR6OCOC6detg9TGe5MOHD/D09MS+fftQpkwZreOwB1BniLkhI8AIZGIEwnfsRNCYMWIHtjWqw6VLV7z44QfxO13FJn34ABMrKwT/OkW+y4L/HoVF7tzptuvA4SPwbu9eWH/zDeL8/ZEYEQGXbl1hW6UK7KpXT7d5jBmI6vlSgkxSTAwsCxdGDm9vkIzL+8P/CFKcw1uBR1J0NB7Vq4/E17I6vzn794PboEHGTJ9qXyaAWZwAkueKCAt59qZMmYLSpUsLAhgRESGuMTds2IA2H+sC+vn5oVixYjh//jwqVaqk06HLygQwMDAQixcvFjiEhYUJDA8cOIBLly4hb968GvFhAqjTseFGjAAjkMkRCNu4Ea8mTRa7cP2hp8j8fVQn9WSF3Av+gEM9mUcwPexJ+/aIuXETuX//HVFXriBs7Vr5sIUvnIeZk1N6TGPUGI+bNkXco8diDMkL+v7oUQQMGAh1Db+Iffvxctgw+Xy5fp0M57ZtjZo/tc5MALM4AezWrRsog3XevHmoWbOmnAAeO3YMderUEcTGSelNQsRm8ODBGDJkiE6HTm8CmEmvgAmMxMRE4SklfIhMazImgDodG27ECDACmRwB5XJkRa5egYmNjVycWNvWiADlnj9fxetlKAyJkR/wsFo1JEdHI//uXYi6eBHB06bLhytw4EC6xxwastZ7RYupdCt46iTerlghNP7IlDOXQ+bNx5ulS+XtfZYvh121qoZMq1MfJoBZmABSbN/UqVNBV8B0lalMAMnz16NHDxH7p2wVKlQQ18QzZ87UeICovXIfOkA+Pj4aawlmZjKkHgNIYCQlJQmy3KtXL/z2229MAHX6J4YbMQKMQFZEIHjWbJH04dKjBzxGjhBbfNy4ibiKVTe6+pSkWpRjBI3B5c2KlQiZPRvmHh4oeOQfvDt4EC9HjpIPmXfDBtiU+caYKYzuS9fg98uWUxnHuUsXmFhYCOwkK3jiOCxy5ULAwEF4f+SI+LNVyZLIu2olTG11D13Sd8FMALMoAXzx4gXKlSuHI0eOyHXr0oMATpw4EZMmKTSfpANHV8oUY6hsmZ0AKsvAkKf0zz//FFfC5D0lLDVZZt6zvv94cHtGgBHIvgi8HDcOEdu2w23wT8jZt68AIj4oCGGbN+PNEoUXi/7uPmwoQuYovjQXvXPb6ESNgCFD8P7gIbj9/DNy9u6F98ePI6CfQn/QsVUreE2b+kUfUIyfH5581zLNNeSaPAlObdvicYOGiH/+HD7Ll8GuWrU0+xnbgAlgFiWAJF/SsmVLmJmZyc8IXWFSQWlK9Dh8+DDq1q2r9xVwdvIAKgtB29vbo2jRohg5ciRat26t9X3HBNDYf5K4PyPACGQGBCRvlcf4X+DSsaPKkmP9nyAxIhzPu3WHQ/NmyNm7N560bYekiAjRrsD+fbD09TVqm48bNkLc06fw+esv2FWtgqhr1/FMbR15Vq2E7bffGjWPMZ2VSWnuub/hzZo1ImZRk5k5OyMxLEx4BwudP/dZ6ikzAcyiBPD9+/d49uyZyjmjK1+JxNC1LSWBbNy4UU5oSN6EXv+kSSDGvJsyQV8mgJngIfESGQFGwGgESAOQEi+85syBY9MmGscjrUCTHDlEuTLKfH3WpQuir1yF54zpcPruO4PXQJm1D6vIYuMKnTsLcxcXxD5+DP8mTVXGtKtbBz5//mnwPMZ2DN++HUFjx8n1CaVrc2lcwiFo1OgvtmYmgFmUAGo6uMpXwPQ6ycBQVivJwND17cCBA0W3c+fO6Xzu9U4C0XnkzNmQCWDmfG68akaAEdCMQHxIiMhWNbOzkzeQiA39QZ9Yu+DpM/B2zRoYWy2EvIkxt27BslgxFNi5Q6wrITRUVM9QNpKhKXLpoiChX8JeL1+O0N/mwrFFC3jNnCHiFAOH/CyW4vHLONhVqQLyZCpb3vXrYFO27GdZLhPAbEwAJSFo8gIqC0HnypVL58PHBFAVKiaAOh8dbsgIMAIZHAEiVY/q1oOFpycKHDwgr0ihnNla6OwZmLu66rSTiL378HL4cFiXLo18mzbq1Ee9UfTNm3jarr2MRI0ZDZeuXcXPSXFxuF+ylPiZrlGT4+PFz+mtPajPooNnzMTb1atFlRSPEcNBOn/+Lb4TcX75tm+DVdGi8Pu6uMqQRW/fEh7Tz2FMALMRAfwUB4oJIBPAT3GueExGgBH48ghEnjqFF737iIXk37VTEBblv9Hfi967q3OpstgnT+DfqDFMLC0hpGMMIDqvly1H6Ny5Gsu+kTZhYmQkXH/4AY/q1EHCyyDk27wJ1qVkxPBz28uRIxGxe49IgqE1kZF8TfyL57AqJpOHedatu5CwITNzdBSVTD6XMQFkAmjUWWMCyATQqAPEnRkBRiBDIUBxe1SL1vrrrxEXGIjAgbJKFB6jR8GmQgU8adlKvl59a+8mJyXhQYWKSIqMFNp9VkWK6L33kDlz8OavFXDp1k2sSZtJItHeC/+EfZ06WtvRmoLGj4eZrR3cR43UmczqsvDnvXrjw+nT8Jw6FU6tFbgp96V4xvigV4h//kx4Ri28Pl+lLCaATAB1Ocda2zABZAJo1AHizowAI5BhEKBEjedduorkDlN7e+Ts01su32L5VTE4t2uPVxMnivVa+PigwK6deuvUSR4vz6lT4JSKooI2UIImTET45s3IOWAA3Ab8qBW7Fz8OQOS//yLXxIlw7iC7MtZk0bdu4+nHahvGVCqh6/IPly7BoVEjmHysFS/pIkqZyhnmQX9cCBNAJoBGnUkmgEwAjTpA3JkRyAIIxD56hJh7fnBsppqFmtm2FvvwIfybNZcvO4evL+Iey8qYkZlYW4vKG7ZVq8Jr9iyYOzvrvcXg2bPxdsVKOHVoD8+PZFKfQQJ/Hop3Bw6oxP9p6i8RRddeveA+VJZ4ocne/v23vIKIa7++cP/pJ32WI9omJyTAr3gJ8bPP0iWwq1ED0j7pbwWPHxNxlBnNmAAyATTqTDIBZAJo1AHizoxAJkYgKSYGcc+e40mLFmIXaV03ZvStfrhwAc+790hzmaRp59C4cZrtNDWQEkFsypVD3nWK2r26Dva8d298OHUantOmwamVdpHlsE2b5d5KSmCxzJ9f4xSBw0fg3d694jXnjh2Ra/wvui5F3i76xg08bd9B/O4+fDjoGv31woXy1ylOMhnJ2PFwB0q5lUIh50J6z/EpOjABZAJo1LliAsgE0KgDxJ0ZgUyKAHl9nnXpiujr1+U7cO7aBbnGjMmkOwLeHTqEwMEp68CTRyvy5EmxL3M3N1DpMhOlIgP6bFgimeRd9N2/T5+uou3T7zsKzNO6rk2Oi4Pfx6xg6lf05g2NcjD+LVsh9t49MbZD06bIPWe23mt6f+w4AvrLqpCQd/TDmTPyMaTSd/v992PUaVnM4q1ut/Se41N0YALIBNCoc8UEkAmgUQeIOzMCmRSByNNn8KJXL5XVW5ctC49Ro2BdQlXaI7NsMWzTJryamLLUJ5VVI3KYHBUFt6E/I6favvXZX8yDB3jSvAVgZgYheWJiok93+DdrhtiHj5Bn9SrYVqqUal9luZqCJ0/CwsNdpT3JstwvUxZITpaRt2rVkGf5Mr3WQ43Dd+2SCzpL1+T0d4s8eVBgz26YWllh0vlJ2PZgGxNAvdH9tB1Mkinylc0gBJgAMgE06OBwJ0YgkyNAkiOvJk3WuIu8GzfA5ptvMt0OXy9ZgtD5vwvhZ7rGlMx9xAjY1aiOyOPHRfYt6ewZaspVPPQVhI4PDMSjOnXF1Pm2bYN18a91JoD5d+9GDu/cwpNpV7Om+L8kyiwNYlWqJPJv3qz31kjcmkSulY0ypD1/nSInnRPOTRBXwGTnvz8PuxwKYW29J0ynDuwBZA+gUUcpKxPAV69eYerUqdi/fz8CAwPh7u6O0qVLY/DgwaijRVaAhaCNOk7cmRHINAiEzJ+PN0uWalwvxcdRnFxmM6lSR46Cvoh7JEv+cO7SBe4/D4GptXW6bCc5MVFF/Dj/zh2CUFJWsamlZapz+DdvgdgHD0Qb3yP/IIePT6rt3x3+B4EfkzryrFmDV79OFvtyHz4MIbPnyPva1a6NyGPHkCNfPvgeOqj3PkP/+AOvFy1W6be3Twl4NWiOzl91RmJSIgYfH4wTASdEm+3Nt6Owc2G950nvDkwAmQAadaayKgF8+vQpqlSpAicnJ0yePBklSpRAfHw8Dh8+jGXLlsHPz08jbkwAjTpO3JkRyDQIvBw1GhG7dmldb8Fj/xqt6UZkiSpfWH39NUw/Qzmz5z1/wIezZ0XlivAtW5DDt4BBHrG0HqLy1axyW9Lhc+3eXWP3hLdv8bByFfEalVajOrq6XB9TcgYlaZAcjCRhY1ujOj6cPCWfhzKaXw4fATMXFxQ+dzat5YvXqRweEUYq2/bq1ykIW79epd+o7mbw9zTBgVYH0GJXC8QnySqTkDXK3wgzq83Uaf06LcbARkwAmQAaeHRk3bIqAWzcuDFu3ryJ+/fvw9bWVgWj8PBwQQw1GRNAo44Td2YEMg0CTzt1RvTVq1rX6714Eexr1TJqP6+XLkPovHn4HMklyterPsuWClFi8syll+dPGYiH1WsgISREIzaWRYsi34b14hpa2fy+KSMkaKi+b9H/FIk3aQH8ol9/cXVNGIb9Lcs6pkQNqiWcGBEhfqdyceJqmeISb92U6/hpG1tZLockXkJ+m4t3+1QTWvoMMEOYvQmq5q6KM4GKpBBpzKX1lqKyV+W0lv9JX2cCyATQqAOmLwGkcMvohGij5jSks7W5tc7ftt6+fYucOXOK69/Ro0frNR0TQL3g4saMQKZEQJ7IkMrqDRU6loaMDw7Boxo15DMU85Nlqn4qe3/8OAL69YdF3jzwPXRI538vDVlPQlgYHn6rnfx4zZoJx+YKPUJlLCyLFUOBnbJYOl3s5egxiNi5E7ZVqgjvJpll4cKIDwpC0vv38P5zgdDtExnDyckodOY0zHPmTHVoih980aevaEOJHlTbV906jDRDkqlqgksBxwLwj/AXTTsV64RRFbRXMtFlb8a2YQLIBNCoM6QvAYyKj0LFDRWNmtOQzhc7XoSNheo3Sm3jXLp0CRUrVsSOHTvQsqV2nSlN/ZkAGvJ0uA8jkLkQiNizBy9HjBResoTXrxEfECBi/sK3bcOHi5eAxES4/fwzcvZWzRLWdZf0RflxnbqIf/lS3uVTE0ApkcG+YUN4z5+n61INbiddA1vkzg2ntm0QvmWrfL+5Jk2Cc/t2CPhpMGLv3xfeu+DJv4q58m7YAJsyuifYBM+ajbcrV8I8Vy4kvHolxiAvYnJMjPi58KWLMHNwwINq1ZAY+hr5d2yH1Vdfpbqv8J27EJSGc6DdaPMUY5xufxqr76zGitsrUMylGLY022IwfoZv7wUFAAAgAElEQVR0fPXhFRKTE5HbLrfozgSQCaAh50jeJysSwIsXL6JSpUpMAI06GdyZEci6CLxZsRIhs2fDoVkz5Bo3FnEvAuQZqVIFiLRq1aaGDnmnHtWqLW9CsWmFzp75ZF45kkMJnjkT4Zs2w7V3b5H08antRf8f8eHcOfge2C9iJR83bIS4p0/FtJSk4dSuHR6Ur6CyDEMqdbxZuQohs2Zp3I6pgwMKX7wgcH3SqjVi7t6FLlf30vPXhtF/+U2wqqc3mhZoiuW3lotmu1rsgq+TL56/e44mO5uIv/1V/y9U9Pw8DhGKQSyztoyYV3KIMAFkAmjU+1xfAshXwEbBzZ0ZAUYgAyAQPGMm3q5eDZcePeAxcoTKipTJYe7ZmolHWlt4f+IEAvr2U/FU0bVl/u3bjJJgUZ838sxZvPjhB5U/e/02B45NZATlUxoluBDxNLOTyaFI+n70s2WRIrD09RUl35TNkJJqEfv24+WwYRq3YlOpEvKuXoX4xHg87N0DJmevQvI+Sh3oM0s92US5zJvUztzDAwnBweJXuv6t4lMdv9X8DbMvz0Y5j3JoXEBWOYUygkuvLS1fz+cShb7/9j7a7G0j5vWy9cLOFjuREJ0AR0dHREREwMHB4VM+7gw7NusAGvFo9CWARkz1Wbs2atQIt27d4iSQz4o6T8YIZA4EAocNF0H/VPbLtef/VBYtiQLbVv4WeVauNGhDr5ctR+jcubCrWweRR/+Vj2FqawvvRYtgW1HVM2bQJAAe1qwlvxalMUzt7FDo9KlPkviR1hqfdu6M6Cvak2qoP5VU0yXzV3kuupJ/3q2bxulde/0A96FDMfHcRLgs2IJ615ORs39/uA0aKNqTMHbI3Hmivq+yrqMUVygN6tS+vejzpGUrPPraCSMq+aPLV10worzqlwOpfbu97XDvrSym82ibo/Cw9UgLHqNf3/N4D8aeGSsfp3/p/uiUvxMTQBaCNvxsZVUC6O/vL2RgXFxchAxMyZIlkZCQgCNHjmDx4sW497F0kDpyHANo+FninoxAZkHgWbfuiLp4ESQf4tismcqyP1y6hOddZYTDa84cODbV35smEUy3wYMROn++KiwmJih2767RUCV9+ID7ZcvJx6EyaC5dOsO6VCmjxzZkgBg/Pzz5LvWYa0PiIGP9n8BfqW6xx9ixICId9+QJXLp2EaXtSqwpgdZnktD+dJKIR/T8VRZvKMUpUkZykWsKcirJ5Uj7LHr3jsgcTk5Kwo/HBuB04Gn8UukXtCvSTiMUIVEhqLO1jnhtYZ2FqO5d3RDIdO7zMOwhWu1ppdK+ilcVzKo4iwkgE0Cdz1GKhlmVANJGg4KCRCbwvn37xM9ubm4oW7YshgwZgpo1a2oEjQmg4WeJezICmQGBpNhYkcFKlTLybd2aouxbemTvSoLHFI8WMmu2ICvKlhYRojrFcS9eCJ06bR6zqMuXRS1jurosdFImUPylja5bKe4vKTJS41LS2remToLoUixhUpJ42eevv2BXVaYnKBkRwFo3ktDvgKyNlAiirFfoOW0anFq1BK3xUe06SAgKAukJunTqBLvqCgLXZk8b3A+7j8V1FwsJGG3W92hfnA08i8mVJ6NlIf2SDfV9Tq33tMaDMJmAtmQ5rXNid8PdTACZAOp7nBTtszIBNAQVJoCGoMZ9GIHMgwAlLjz/X0+Yu7uj4InjKTTjiCD4FVNkkRa+cgVmdqpaorTbqOvXER8QCMdmTVU2LyRSqlYTmcQU85YcGysSJJQtLSL09u+1CJ42LdW6vW///hvB06aDqmD4LFqYYR7Ag6rVkPj6tXw9JAnz5q8VyPnjj3BoUN+gdSpf2ebeswMXLQNQIVcFWJlbIYdpDpT8uyRKPU7C2C0yAkhW8OQJPKqh+kWfSuIpJ5QUvnAeZmqasDU318SbmDfY2mwriroU1bpeuo6la9nBZQajZ4meeB/3HnYWdnpfcesCyDdrv0FCUoJoOrXqVPlV8L5G+5DPIx/HAOoCIrdJiQATQFVMsgIBJImLqKvXkOuXcTAxTyllwO8DRiA7I/Bm9WqEzJgJ+/r14f3H7xqheNG3HyJPyLxqOQcMgNuAH1O0k7xL+TZvkl+7UsLC64ULhcePpEjIE0X2evlyhP42Vz5GkatXxDWmNlP2XGkji1IlEyJWbgMHZJhH+rB2bSS8DBLroSQbygim61VjTFm4edrU4vgvUlbJycnSCQtqL0CXg12Q71UyZq1KlE+jnNShaW5NVUMowaPMujJISk7C8XbHQV42bfbbld+EJEzXr7riK9evMO7MOLQp3AZjKyni9IzZs3Lfyhsq4338e/GnTU024afjPyE4KhiOSY44+7+zTADTC+jsNg4TwKxHAKUPj9wL/oBDvXrZ7UjzfhmBVBF4OW4cIrZtV0kWUO9A18MkKyLJmqhfFSt7CaWs0/jgYBWPU87+/eA2aJAYOvHdO4Rt2iwSQ8jyrluLHL6+MHd21rhW/+9aIvZjucqit29p/CLn36w5iBh5L1oI+9oKyZkv/fgfN2iIuGfPxDLS8nTqs9YeY79GoilwvaAqmczvmB9PIp7APCEZv65NhK9MKjBNy1GgAOLWzsE/z/5BrxK9cPjpYbhYuWDAsQEwNTHFtc7XYGZqpnWcVbdXYe7VuWhWoBn2+u+Vt/un9T94+eElynqUFX+jsxKTGANLM0sxriFWY3MNvI15K7qebH8SQ08MxZXgK0iMTsS9fveYABoCKvfJuqXgDH22md0DmBgejgeVvhXbz5E3LwocOvhJriQMxZf7MQJfGoGnHb5H9H//CeFnB6XkAvV1BQwZgvcHD4k/55o4Ac4dOsibEEG8X0b2Ae8xehRIM1C6kpUa+SxfDrtqqjFkT9q2EyXMyEwdHVHo1EmYWlqmgERaI70gCR0rNyL5FZEAkpSEgidPwsLD/UvDKp//5ZixiNghq/SRXgTwRugNdD7QWac9TlqbgGIBiqYkSUNi1OpmWaggWrSR6RaWyFkCt17LngsZef7IA5ia7X60G+POjkNeh7x49k5GeMlMYIJkJGN78+0wNzFHpwOdEBkfib6l+uLH0ik9yWltiq5+y60rJwSgJ3w7QXgZydu4+/FuJoCEN8cApnWEtL/OHkBVbDI7AaS4pGffd5Rv6nNpghl+ArknI/D5EFBOUsi/ZzesChfWOnnAwEF4f+SIeF1KIJAax796hUc1ZXWCpSvYoEmTEL5xk6yJqSmKXL6U4po38Oef8e7AQfmcBfbvE3p56ubfshViPyoVaNLOk97nZm45Ufj06c8HoA4zUX3e0IUL4diiBay//lqHHtqbkIeNPG26WLXc1UT2ruebZEw86wnnOwGw/uYb5Nu4AedH/ACnPbIycpKRLmOL1rKybuqmS5WPC0EX0Osf7ZVi6uSpAyodJwlJF3QqKLT79DUil013NoWVmRUudroovIi3Qm+h44GOTACZAOp7nFTbMwFUxSOzE0D1EkfOnTqJWMD0NApy/3DqFOzq1JGLwKbn+DxW2ghs9tuMJTeXoH2R9sKzwKYbAvJrWjMzFLl+DaY5cmjtSJUuIo8dE6+7jxwJ1x7d5W1j7t/Hkxbfid8d27SG15QpIrGEEkyIWNC1bA5v7xRjh/z+O94sXqL4u7k58m3cmCIT+RGVkQsMFO3USWJSTAzul5aVUpOEkHXbfcZrRYSc/tN0NUpJFZU3aq83rL6b/7r8h9pba8uvSm0TLbC//WG42rrh7+srsOnfeXjhZoIt02XJFNa1a6JZxTMaQantUxu/19YcHyp1oCtZuprV1cxNzXGp0yVYmFro2kW0OxVwCj/++yMKOxcWXkXJRp8ejd13dvMVMHsA9TpPKo2ZAKpil9kJ4KvJkxG2YaN8U1RAPc+Kvww/IGo9SSfrcd16ouancoyTIRPQWFS83cRMe5yNIeNm5T4UpO731g/9/+0v/6C72fUmX/Pr+NDfHTmCwIGDkCN/fvgeVK1SoT5E9J07eNpaVnlBvbyasrfPukwZ5NuwHo/q1Uf8ixfIu/Zv2JQvr3FF8SEheFRdlTSQ1IvvoYMiVixk5iyYWFshbP0GJL17J8bIt2UzrEuWlI/34cIFPO/eQ/yuLHqsIwQZqhl50EhTjzJuc5ipknHJ8yUtmOLzpDg49U3s/m638LZ1PdgV10Ouy18eWX4kOn/VGXOvzMWqOzJP4ui4eqhyLgxPfmyKgXcmasSjU7FOGFVhVJpYkfyMPra+8XqUdFM8S219YxNjceLFCZDW346HOzD7ymzUz1tfVCaRLCYhBnvu7EH70u05BlCfh8BtFQgwAVQ9DZmZAEbfuoWnbVWFS8kbUWDP7nQ78sofYMaQy8TID/Bv0gSWBQvC56/lTGB0fELTL07HBr8NKq0Ptz4MLzsvHUfI3s2e9+mDDydPaSwBpwmZ4Jmz8HbVKpg5OgpPnHnOnCCNPr/iqh/8jt99h4hdu8QQhc6dhbmLi1ag4wIC8bhuXZXXycNokcsDgUN+TtEvz6qVsP1WFtdL9nrJEoTOl3mnqL6wuatrpnyoVL6NMm7JVjZYifK5VEnzfyH/iexesn6l+qFH8R6CFG2+vxlXgxWizs19m2NKlSni35ARJ0fg4FPFFXujfI0wq8YsIZtCki1kDfI1wJwaczDo2CAcf6E5zm9YuWHo9rXm6iPKYO99vBdjzozRGf92hdvhl29/SbP9hnsbMP3SdHjbeaOSVyVse7BNJKoMKiNLKpKMawFzDGCahym1BkwAVdHJzAQwcOgwvNu/X2VDZs7OKHz+nFFnRLmzsleE/k6ltJw7tE9V0kLT5FFXruBZZ9k/7vm2bzM6VijdNpjBB/pu13d4HPFYZZV/1PoDtfLI4tHYtCMgv7Y1NZVdq+bPnyZcb9evR/CvU0Q7y0KFUGDvHrxevBihv/+hsS8lXvkeliWOpGYproJTaez95wLYKxFGeRm7YUPhqlYHOK15M9Lrr6Nfo9YW2bmdV3Me6uZVJcXHnx/HoOODhM7f5c6XVa6JJc8bJVlc76rw+G25vwW/XpBVASHzsffBgVYH8P2+73H7zW3xNym+r+3etsKbrsn+rP0navjodr077OQwcU27ttFaULIK6RMGRgaChKIl61CkAzbd3yTmXl5/uSB0VNt3erXpItOYrrtX3FqB1oVaw8fBBzQmZSWT2ZjbICohCtOqTkMzX9WqNUwAmQAa9Z5mAqgKX2YmgEG//ILwrdvEhjynTkXQWJkeVdGbN2CSSqyTPgdIKnKv3IfKXeXs20efYfD+6FEEDJDV63Tu2gW5xuj+LVqvibJY4+a7mgvJC2UbXWE0OhZTJP5ksS2n23ak+FibChWQ9+81Oo0beeoUXvRWnO3cf/yOwEE/yfs6NG+Gd3sUEiDOHTsi1/i0PTyJkZGiFrG5uwcC+vdPdS1eM2eIhIrk+HjA3BwvelKs4XmQwLJj8+Y67SM9GtGVIwkk57bLnR7DwT/cHy12txBjDS83HF2/7qoyLl19Tjg3AZTcsajuIpXXKAN30vlJmFtzLmr6KMSe45PiMfXCVDhYOsiTRyibt8G2BohLihNjUDLFnu/2oP52VVHq32r8hqEnh4o2VztfTXElrW3TNGdUfBQcLR3lTeg6n8SpJfu91u9Cu49MInT0s/Tl7c/rf2LpzaXi9VvdbqHvkb44+1I1aUXT9TETQCaARr0ZmQCqwpeZCaBU35KU7elqyK9UaSAhAT7Ll8GuWjWjzonUOWzrVrz6ZbzKWLZVqyLPX8v1Gj9s8xa8mjBB9MlIpaz02sQXaKysByZN/0OJH/BTGQUp+QLLyhRThv7xB14vWgyndu3gOXmSTmumsnH36X2kwQoc2A/LAgUgeeSoSeErl/VKjKI42JfDhqlkBmuai75khW3ZDAt3D1HCLvbBA40l0XTalIGNOu7vKKRSdjTfgULOhQwcRdHtr1t/4fdrsqts8nxNrKwaj0cesfnX5oOueKn6hbrRFbKFmfaEinrb6uHVB4UoIBEvklKh+Dprc2tEJ0SLIUeUH4EyHmWEd27t3bXi/xU8Kxi9P+X4QCKhkrdTeeDx345H28JtQQkd+/z3iZcOtjqIfkf74ek7mUSNZGe/PwuHHA4qf2MCyATQqIOaVQlg9+7dsWaN7Fu+ubk5XFxcULJkSXz//feg10y1KNNnZgL4qEEDxD97jjx/r4FthQqifmbS+/cwJlZP/XCRvMPrBX+KzEerosUQPGUKSGerwG5Z/JMulhQXh5fDR+D9YdkVB1nhixdEnBWbdgSoOgGVhKL/9ynZR1whnQg4gRa+LTClquyakk07AhJRcxv6M3L20i7foT4CVdZ5OWJkioEljbtY/ycI/OgFT01XMLVnI2UQ6/P8pHq3+vTRty1dZbpZuwlvmERo/lf8fxhSdoh8qMi4SNha2OoVx0vkq8J6BcmiEmpEkqi0G3nDSDePvGgU70qxfz+XTRkbmdZeyHtIXkTJ6GqWPHXSVbD090+VRDXg3wE4GXBSlIc79/05FY+gNDeVmqMEGPW1atobeQbVjQkgE8C03gepvp6VCWBwcDBWrVqFxMRE0M+HDh3C9OnTUa1aNezZs0cQQ3XLrAQwOTERfiQNER8v6o9aeHrKg8WtSpRA/q1bjDonCaGhIG9F0Nhx+HDmjIj9o6u0p23binHVRXXf/PUXKF7QY9gwWOTOjfjgELw/egRObdrg1fjxiNgtC8iW7FPI1Ri14QzWmcRgSf3/2AuZLAldUe3334/x58aLTMEl9ZSkRTLY2jPKcp6274DoGzeQe/58ODRsoNeyNJHA9BI5poVI1UmUF2Xu5gZ632kzqnVr4eGh1z6ocVxiHBZcXyDKqHX/ujtCo0NxM/Qm6uWtp0Li6G8kYlzZqzIW1VmE0mtlntAuX3URXjMy0qPrfLAzun3VDT+X052kaUqeIIkTSnqouKGiyp4kL5m+Gw2PCce0S9Nw8IksKYRKthEZW3RDcZ3sauWKE+1lJf/S2yJiIzDv6jw0LdAU5XKVU0lEUZ6LPH6zL8+Wv7el19yt3dGnVB8R0yjVG1ZfIxNAJoBGndusTADDw8Ox62NmngTSsWPHUKdOHSxfvhw/aAigzqwEkGRZHtWuAxMLCxT577qQVqFqB1RRwMLLCwWP/WvwORHk8uviKv0piJ5qaT78VqbTZVejBnL+2B+vFy6CU7u2CPhRVpvUuUsX5Bo7BgGDh+D9oUOwr1cX748c1biW9PxANXizGbTjlVdX0OOwTPpDfPB2u4WzgWdFoLmhArMZdKufbFkPKldB4tu3oj4v1enVx6KuXcOzjp3kXfLv3gWrIkX0GSLVtlGXLyNo/ARRQ1gyzxnTxfuZZJ1i7t5FcrTsylIyQ2N76Zpz1uVZYhgic/Q72ZK6S1AldxX5+MqZs8vqLUPvI73lr5HI8azqs9DzcE/8F/qf/EzqAgh59hrtaCQSJZSN4uRIyqXZLtVEhxX1Vxh8JUve8snnJ+PAkwNif/kc86lo96VV71eX/ejThvQ7p1xU9davabhGXIVfC7mmMlSrQq0wqfIkvIx8CQ8bD41l6ZgAMgHU5/ylaKsvARTCnWr/EBm1AB07m1hb63XFQNe8mgggTVe6dGl4eXnhwIGUOmCZlQB+uHgJz7t1E+XfpCzEuBcv8LhefZhYWQnRW5JJoODzt2vWwKFRY1gWSDsLkvBKePsWDysrPhjoWRS5dlWMJ11dWZcrCyQlI/qa6j9iVG6pwN69UC5ur/zIHVs0l3sDi969Y3TReB2Pk87NEt68QcjcuXDp2jVdP/B1XsDHhrse7cIvZ2XJBRRsfqbDGfEB2nB7Q5DA7MWOF3UOWtd37qzQnmSHHpQrJ7ZS+PIlmNnb67Ut6QsWdSLPXKHTp/Tqr2vj4OnT8XbN36I51Qu2+bhm+l16P9PPll8VQ4GP5dbSGpti3ugLBMXtudu4o9vBbinIBo0x6JtB6FVScTU+/ux47HykvXIFeaUoRk8yTVeUmtamTUCZrpUp0WTxjcUq3Y60OYJctrnS2maqr5N+JmXbKidnfErvn7bFnAs8hz5HVRPmlBNEZlabiZGnZeEGRLq/9VLI/2gakwkgE0Cj3hj6EkDlGphGTaxnZyIcpjY2OvdKjQB26NABN2/exN27d1OMl1kJYMhvv+HN8r9gV6sWfBbLrjhUPvSuXBbVO94dPCg8cKZ2dihy5bJOeFLBeSo8L5mFtzcKHpWVyIq+dVt+DaxtMPJISpUL1Nvk27pFrl1Y+MJ5UAJLRjKJ4FJ8IsUpfimTsgTp2o5kJCh2iD7Mqm+ujvDYcGxovAEl3PQTpf1Se/kS85IH7Umr1uJ80TnT15S1/z7lWQjftg1B42REv8CBAym+pMU8eAAkA5a+BWCiIYRF074kTx55kQZ+M1DUr9VkPb7uoXKNS1846IuHNnO2dEZYbJj8ZfoSYmOR9r/R0tUyrWdvy71YcmMJVt5eKermJiTLqnQoW3rH6EmxjJTNfKh12pI9+p6V1Nq/ePcCjXc2VmlSybMSqKwc2bZm24TGIUnkDPhmgMYKKcqdmQAyATTqfGZHAti+fXvcvn0bd+7cSYFdZiSAie/f41Gt2kiKjIT3okWwry3T1iKCQMQrOTYWlsWKyWuLSptO68qVYviCRo2GXe3aeLNUJlFA5rNsKeyqVxc/U1k46RpY20F0atsW4Vu3anyZCt1TTVX6YkHVEKgqQkYyZc9lWnh9ynVLWYKU7UtZv5L9cPgHXHx1UWRJUrYkm2YEXk2dhrC1a2HzbSXkXaVbbVn1kaSzoKvWnyHPQlnMPT2+EJH3r9qmavKM17TWtLvFbhRwKiCaUfkx0rdTtiLORXA/7L7GYYi8FHFJ+1qcYldHnR6Fsh5lsbrhamx9sFVc02qykjlLYn2T9WktW6/Xy6wtA5Ju0VWUWa/B02hM89L82kxXEi31ZwLIBNCo86kvAcwKV8CUDZwnTx7s2ydLu1e2zEgA3x06hMDBQwR5ImkKE6UM58cNGyHuqaqcgLTftAjNk3btEXPzpgo+lkWLosAuxbUQJYb4fWV4wXdaA8Uu0hVbvk0bYV1as+SGUYfcwM501v2KKWLFDLk6NHDqFN0o1urSq0tCOJaCyiWTKh9o0lFLr7l1GSfgfYCQ1/B18tWl+WdtQ2frcZOmInTFZ/ly2FWratD8kSdPijg919694NJJEQ9o0GBaOpGnkeJ2TSwtxRUwhVkYY8rVNNTHGVtxLKZeVJVXkeLOqG3rPa3xIOyB6EbSKFR3unGBxiD5lmU3l6VYlvqXE23rXn5zOf64/odc3uXcy3Poc0T1WnRA6QFCsoXmdLVO30onJP5MJLR3yd6wz6FfKIAxz0LqO/j4YNx5cwclcpbAkWeymxQyKj1HJej0MSaATAD1OS8p2upLAI2a7DN21nYFLCWBrFy5Ej16KILqpaVlRgL4dsMGBE/+Ffb16sF7gWqFgpj7D/CkhUxsVd3SJICtWovgc2WjZBJKKlE2ZS9ZjoK+iHukWqlCamtiY4PkqCjxKxFJ95+HCE/ik9ZtEHPnDryXLIZ9TYWo62c8LhqnSoyIwIOKleSv5du2DdbFDSe7xuyn5e6WeBT+KEVcEIneUoUBTWWiSCeN4gTzOORJ8yrJmLVR3zpb64iarsoeJGPHTI/+cc+f43F9WcYvJS1R7F5Grz1NXzzIjCF/dIVI5OJS0CUcfa456Ypi9kgnb8SpEfL6uW0Kt8GEbycIqaGK6ysiJjEGf9X/CxU9FZm56tU2ehbviRW3V4iwBEpoICkXUxNTrY9PKmco6VeqX4vOqDYDTQo0SY/Hn2HHIHwprGP5LYV+KoV20HWwPsYEkAmgPuclRdusTAC1ycDUrFlTZAebmZmlwCOzEUC6pqX6ofHPn8OxdSt4TU0pmPqkTVvE3JaVQVK2ovfupvohQ54IyiSWTJucjDIBpKSP2IePZB9gVlZIjomR96crXgqgj755EzaVKsnnlgSsPadNg1Orlkad5/TsHPvoEfybKjISKXOUSKqFu3t6TpPqWBS8PuPSDEHyyEgqo7BzYXmfhf8tFDFUmq6z6JqNPB3ahHR12QRd8ZOZOztrbU6ev3LrZAkW5LEZV0lzjJku86V3m9dLlyF03jwxLGWq+yzNHnI5UmiAhCclPFAVD8nWNV6HUm6lxK8Uc9b9UHf5axQnSNU32u1rJ+LyLnW+BAtTheCyslfRBCZCRqX2ltrCY0fWt1RfIedCV8XkmVYnsj+f+FmQU8njRdei5deVl/ff2XwnCjoXTO+jkOHGW317NX67+pt8XYbU9GYCyATQqIOdlQmgshC0s7MzSpUqhY4dO6Jbt25ZRghamXy5dO8Oj1EpBWtfTZ4spCTUjaoWkCwGaQaS3IS6+ZUoKcpP5fD1hZmzEzwnTBD1UNVNW4YvkaWAvv3kzYvc+A+mlpYp+r+a/CvCNmwQfycvYX4RCD8OtpUqwm2QavHztA575OnTsCxcBBYexpO0D+fP43mP/6lM6diqFbympSTZaa3L0NePPjuKIScUorvqshXr760XBJE03KgslrKVXVtWXv7qvy7/aZSRSG1dUdeu42m3rogzTcbthf0QYQdx/ZzXIa9KN+WarvTC6fan4WhhD5IPMk2nEoSG4vd6yRKEzpdVm7CrUwc+C/80dKhM1U+5CgUtnHT6TgWeQlHnoiJeVLmCBnkc/777N+ZcmZNij/kc8olEDWUj71Wpv2XksbhrcWxsuhGS6LH6AOreQ7GWj1nIc2rMQYN8Mu8seSFJr48y2kk0mSp1ZHWjsAmSw5HMkPcoE0AmgEa9T7IqATQUlMzmAVQmX24/DULOfgrCJWFAXpzgqdNA5CgpIkIODdXgDft7LXIOGAC3AT+qQBaxdx9eDh8u/lbw1MlUvV7Ka6CqIx/OnhXyFRTDRLVUKW6Kfs89Z7bGx6JcF5gaWOTJIzyaZGldUysPKNUpNve1xz8AACAASURBVHd3R6FTJw09AvJ+EXv3ioolymaRNw8KKlUwMXoStQFIJ2zetXlYWm+pqFlKXjy6+pXsepfr4kNSMimgnqocrGiwQv53+lAvu66sCHYno2oDdEWnj4UuXYrX82QyH7NbmeJyEVMhHny6w2mVYaSarmUfJqH3wSTc71YVNf4NRdKHD/ClmNQvSAKVBZYzWoypPs9Cn7bqdWipL0mN1M5TO9VhHoY9RKs9rVTa/Fj6R+HRU7c7r++I2rVUwq2GTw0cf34cg46n/LIm1bpV7k9Xy1EJUSIBhBJByN5EvxEktH6++vja9cuEWeiDcXq1rbOlDkKiQ8RwusroKM/NBJAJoFFnkQmgKnyZiQAmRUfj/jeKjDKPcePg0ll7EHHE7t14OXJUyvNiZoZid2RXxKQ1FjxlKmLu3UNCSAhsq1dDnmUpA76VB1EmgFSdIGLnTjh37qxzTVSqt/qidx9EXbyYYm2FzpwWRIIyL9MyIprhW2QVT0h6xtTKKq0uGl+nYP/4oCAkfYhCyOzZIoM6MSIcCS+DRPtC58+leiVq0KQfO6l7btTHUv+QkMSgSeONarRK9j7uPSpvlIl0k02rOg3NfFUFdtNa56NxIxC/TeH96TjcDIlmwPHcc+BU4Vt56T5xJXigM7bMkF0BRucArONko5MmpS7PLq21GPr6s+49EHXhAnIOHAC3H1W/5Bg6ZkbvFxoVitpbFWSPEjg2Ntmokwd4yPEh8phB+qJxudNllS8c2vZOlWqI2MUlfXzwHxvOrjEbDfM1lHc7/PQwhp0cJn4/0PIAfBx8Mjqcn3R9ylf1TAANg9okWYqaNax/tu7FBFD18WcmAqgc4E678Jo5A45aEj7odbqSIw3A14sWiWLyklmXKYN8G9YLkegH5cqrAJJ3w3rYlNEuW0CN00sqJWzrVrz6ZbzK/FJSiS7Zmy9HjxHkk0yXdWt646tn/lIblx494DFyBB7WqImE4GDk27IZ1iVLpvu/G9oEcqWJSMT337aqFV2eRjyVV04gb03PEj1FvJbklZP69ivVD/1L95evmfZ5/MVxkYnoZuOmcS9Xu7WBzUWFVNLI7mao+CAJrc4l43XlIqi2UqYRdzrgNIbu74c182QEUNnybd4E61Ky68IvYY/q1kN8QADyrl8Hm7Iyb1NmN3p2FPsZEBkgSoSpiyTT8+j/b3/ksc+Dvxv9La5TddHnI1yUq3+QRh5p5elqVLGi8Y7G8lg+6vdLpV/Qrkg7McQ/T//B0JNDxc9etl5Cg8+YRBdd15WR2z179wwTz00E1Veu5l1N76WyB5A9gHofGuUOTABV4cvIBJD+4Q/ftAkfLl2C1/TpIrHjWecu8g2k5QGUGj7r1l3F22ZdtizyrV+HNytWIGS2Ig6IsiYLnjieZhyXf7NmIvGDqoHkW7fO4PP44cIFPO+eMjObBjT39ESh47I6uNrs6fcdEX39ung516RJcG4v++DRxxLfvcODCqq1SN1HjIDr/3rgacdOotJJ7nlz4dBIEbujz/iptb0RegOdD3RO0YSC8umKbVq1acjvqFq9RTkeizpOqTJFZFD+ce0PrLqj0LtrnL8xZlafKR9bqiyiKcaLGkXGReJs/W+R55VCmPfXDqb4ZVOSYn3VKyLfgoU48OwQlu2bgPnLUhJA78WLYF9Lpkv5uU2IN5cqDSQmouDJk+kSF/q596BpvvMvz6uUZVvZYCXK51J8caP6sySs/F3B7/BrlV/1WjKRke0Pt4s+hnikqKQZycRIRmeX5FbIlL3bI8uPROevUp51vRbLjcEEkAmgUW8DJoCq8GVkAhgwcBDeH5HpRpG3j2KrKANYMqrPa+mbtg4bVfWg6h6SSWWlXgwYgMijCg+Ta98+cB88OM3zFR8YiLBNm+HcpbNRGbIkaP2gfAWt81GsolWxokKYWpPn4GHt2vJrWrqCpoQVmwrlYZlft5J3NDFVWnjSXFU2x2v2bDg2a4rA4SPwbu9euA8bClcNdaTTBCqNBuoJH1LztCohUD1gugpOzcjTt6GJLNGGTNIVpJ+v1j6AwJ8Gw7lTRzi1bi1e33Z1DQp1m4EcCUCcgzVyvIvG781N8dMeJQII4M++uXHKORhfPUvCxA2qr9E4nlOnwqm1alyZsTjp2j8uIACP69YT7xNRH1tJH1PXMTJiOym7W1pbLZ9a+KO2Qv6JvkTQlwkif0QC9bGdD3di/DmZF94QAugf4Y+B/w7E8/eyGF7yPlK9YZIpKr9eQVLn15oPqifMZhwCTACZABp1gpgAqsKXUQkgXd/6fV1cvliPsWOB5CQET5sO26pV4TFmNCwLyBT807KwTZvwauIkgDJ/Kcs3Xz5RheNF336IPHFC3p3KtFmX+LzlxV4vWSo8kd5//onn//uf8N6om9fsWXBo2lSFBIqqJyVLiaxldXNs0xq5xozRqZQgJa1QPKKy5Vm9CraVKiFk3nxREcWpQ3t4TpyYFsx6v77h3gZMvzQdnraeWFF/BR6EPxBF4IvnVDx3TYOSlhtJwUieG+U2pd1K47/Q/+T1g+k15WoEvi+TMX2NAuOu4+xEPVinbSdQYst1BHtZw7fot4g8dgzPqhVE3tOKhBQaa1ZrU1wpZIIlfybCJTLl6tyG/oycvRT1ZfUG5WMHinelLy0kRaTrtaH0LHMUKCCSUTKqUbwmZXPTlS0JLWszkgQij2+NLTVAfSSjpIlNTWUyQdEJ0ai8obIoqXaw1UF423vrtW2ag9ZSLlc5fOWqEEHXaxAAK26tUKkTvLDOQlFZRLItTbegmGsxfYfl9moIMAFkAmjUm0IXApg3b17Y6FGH16gFfeHOUVFRePbsGfLnzw8rA5MIPsUWYu7fx5MWim/zpo6OcG7XVtT/pWxeIji6GpHJqEuXADMzPO/aDVLWrH/LVqJcHBEmittybttW1yE/Sbsnbdsh5tYtMba5l6fcu0e/m7m6IueP/YWQdA5vbySGh+NBJe2F08kjmGvc2DTXGbZlC16NnyAqMVAJPTKpJquURGPsVbe2RUjXZx2LdsToiqPTXKtyA/K8tNiVUvCbRHXJY0T2T+t/8Od/f8LMxAw7H+2Ee1gy5i5PRA4ljt1utCzDeMHiBHiEA0E/tUbR50kitjLexR4WbxXEg9rdzmuCf74xwc+7Unr/pPUVvXPbaPHl4Jmz8HbVKriPGgnX7grNutRACv1jgYh3dWzRHF4zFdffegH7GRpLdZ5pKm2lwEhrsdXuVnjx/gWSkQw7Czvh0W2+q7nIFr/U6ZIgxnff3EX7fe3hYuWCE+1O6EyW03ub6tU9KAZ18Y3F8mn0LXmW3uvLKuMxAWQCaNRZTu0AJSUl4eHDh0Iw2c3NDTly5Phi/6AYtUkdOpMHKS4uDqGhoUhMTEShQoW0agXqMJzBTWgdSe/fw8zBQWWM18uWI3Suqs4bxeiRjp+hXpZY/yfwbyzzOLj26SOv95t/925YFVGIDRu8GSM7Bv3yC8K3bpORsL17QFfX6iZ5L9VFm9XbEVaFz6V+TUol80gz8cO588LLZ+lbEAmhoXAbMlice8qMftKyFUzt7UHX7eY5c6brtaIUgK9rSS3lPUbERqDqJlmJs6q5qwox5ntv7olrtrpb68qlJuh12+hkDNiXhLKPZBUnlK3bEDMkmAPrZ8tYYdyeZci1/Szerlmj9WmeL2qCb/1SjiV1KPjvUVjk1j2ZQNNEyolGlBlO2Kdlz//XEx/OnYPH+F/g0rFjWs2/2OvKiRfaxIDV40PpSl9o7G2QxatKhEoiXgWdCmJnC0XJxi+xOdK5G3l6JG6G3kQN7xo4GaCQZjLkevlL7CGjz8kEkAmgUWc0rQNEpCgoKAjkGcsORp5OT09PQXa/hJEocvi2baJmqW1FRTzc006dEX31KqgahXp5trSyf7XtI/7VKzyqmTJAv/CVKzCzs/0S21eZkyRpyOtpW6UyvBcsEFeAmkggaQVKCSR03Zf45g2ojJu6adtXUlQUXi9eLLypkrkN/gk5+6rqnyXFxeFB2XLya2a6dnfp2lVlGno2r36dghy+BeAxapTOUjg0SNeDXUVJrtnVZ6NhfoV0Br0WdfWqiGWzLFJEY1KOsvZbTZ+aWFB7gXxdw08Ox6Gnh+S/N7qchB5HFR671XVM0epcEhyigf3lTHArnwlGbUsSci7Fr91AxLK/8PoPxXjquMZYAFbxgMnQ3ki8egOmJ2RyPpHWJrCLTkZ6ZAJTMofkkXUfORJ2NarDzN5eVJbRZFSjmpJ5kiIjkX/HdvG+yaimHMO5uenmFFevMQkxKvFztI9mBZoJQWeKqyPvIGX7Lry+EE/ePREl+cp5lMOqhookoC+191mXZ2Ht3bVws3ZDaHSoWAZJ0qQV1vCl1pvZ5k3r8zuz7ceQ9bIMjCGofeyjywGiD5eEhAThGcvKRp5Oc3PzL+rl1Cap8rBWbSQEBSHPmjV43q2bymOQYtT0fTaaMl5pDH3El/WdU9/2tEZTa2tRqYQ+1O+X/gbJcapaY669fkByfALerl4N28qVkRQTI7J11Y2wUybV0uvK1SKkv3nOmA6n71IG0AfPmCnmkcz3yD/I4SPTMlOXkCHxa685s/F64UIhbp1WLFyNzTVAUjDqJEDZu0n7y7NSIfisvEcpy7JunrqYV0tW/ows+EMw6m6rK/slORnT1iSioEzSUFj//mYYvCsRhV+qIhbmZY/Kxy5BqjUtvWo7ajCaYAFmrUxEPpmGrTCvRX8iws4Ud4b1x9aqpvjufBIKBQHeC/+EfR3DA/5FfCcRb7UvoSTK7XvggMbrZQkzqixT5NJFmJgrxLNVd/nlf2u3tx3uvb0nFrKs3jJ866UayuD31g9t96qGY5D8C0n+1N9WH0EfgkTpNZKFkUz9DHypXRL5IxIoWaN8jTCrhuL3L7WurDKvLp/fWWWv2vbBBNCIJ8wHyAjw0rmr+jWvVKuXiI9f8RJAUpKQZSFyE/izTE/LzMlJJtViQLwiJUxQuTdlc2jcCLnVrprTeZtGDSfpumkbxLlTJyTFxiBim0zKQtlce/WC26CBKmXvBLYlSwEJCrkT6uOz4i/YVamSYgzy8D1pJcuUJbNv2BDe82VkiyquPPxWIb5Mf7P5thKizl8Qr+dd+zdsyqvqLErjSMLN9lHJ2OX9K9waNxfEhuomU+a3sndSWw1niQBqqsc75/IcIfDrcuuFXMol3sMZCytFwLZRA3y/8RXsTsokdCSzqV0LeRctAgljv+ij8Ibmnj8PI8x2If+6U2h+UXH1m3/Pbpj65hMVSMiGb0tE+YfJyDVxIpw7tDf4uaeWHW5ibS3EptXrM7//918E/DgAVsWLI/+2rQbP/Tk6KleDUBdOjk+MF5IuFLtJZmpiii7FuqB3qd5wyOEg4v0o7k/dqELHxMrpn6ikLx7keSYPtGRUrpDKFrKlDwL8+c1XwEadJD5ARsGXbp2p2gV5OZSNKk6Y2tjgebfuiP7vP/FS0Vs3EeN3H08/JmjYN2gA799l5boMMcnjSFm19nXrCA+aevyhIeN+qj5P2rQV+ofajLQQ6aqQKnhoMqd27eA5eZL8pTcrVyFkVkqPhDbdONKWe/BtZRGnSUaxbRTjRhb7+DH8mzTVujbX3r3h/rOirq9yw0dhj9ByT0uM3mGCb+7Hw7VfXzg2ay6P0VQ5F1pi4LY/2I4dj3aAym+5WrtqXMevw75Fm33hSCheCCW27cH9t/eF2G/U4hV4s3iJSp/Cly6Ks0CxkY8bKnQP85CntVJFRF6/hhedu4pMbauvvwaVWiNPrVTkvtehRNS7noycP/4It4EDDD4SpHtJyUrazL5ePXgvUMigULu369YjeMoUaHrN4IV8go6U1Us1mylrl2xcxXFoX1RBlon8ka6fZFSZw8pcUeGm39F+OBN4JsXKehbvicFl05Zw+gRbUhnyavBVdD+kSNrh5I/0RZw/v5kAGnWi+AAZBV+6df5w/jye9/ifynhUcYLq975eoChgT9ezyp4m5y5dkGus7hnA6gumQPnYp0+Qf/NmrfFU6bbJdBhIWaqGdArfLFmqMipd85paWeJp+w4aZ6MEDiI2dI1McjPqsW1UScWlW9dUY8biQ0IQtmGDfO48f69B2Nq1iDx5KsX1tPIiUpOPuRZ8Dd0OdcOW6QpPpOe0aQjSkN2tizwPZXq/WbkSthUqqFTieDJ7KmJWrINzx47INf4X+fLU6x4rk1V1T7Gy3mRcQKAok0cxdsryLFRT9qsD99HpRBLs69UVMZyGGsVUhq1fL76cUFIHmXPH7xG2YaP4marF+O7bpzJ8yJw5ePPXChj7/jB0zbr2ex39GrW2KOJwlYWTaYwya8vI6zmTnt6I8qq1qSedn4RtD2SJUso2rNwwdPtaO2nWdX3GtqNKF013yr4U2VvY41xH2fNjSx8E+PM7CxPA6dOnY8eOHfDz84O1tTUqV66MmTNnokiRIvLTQ7p1Q4cOxaZNmxAbG4sGDRpg0aJF8PDw0OmE8QHSCaZP3ih85y4EjVaV/iDJi4hduxHr5yefnwigcqyZS/fu8Bg10uD1iSqK8fEiwSAzWNAv4xG+VXalR1iEbd4iPD1EUoQXausWkZkb6+8P/8ZNRDsSuo69K4uxIiMC82bZcpCsi7JRsgJdGdLVa1qmPL56W1MHB3iMHIkg0mpUMuXrdfIkRl25iuhbN+Hcvj3ORFzHyP0/YtV8RZxtzv798HrRR+kMCwtYFSuGmJs3kXv+fDg0bJDqEuVaj2oxnS/HjkXE9h1QT3KheswkswJTM0EOTa2tVHB4OXIkInbvEZJDHqNHpxknO+HcBNw4uV1oDJrY2qDIhQsqV+9p4av8upTN6zl9OiwLFxI1iCN27JBjQ7WG6RpY2QKHDsO7/fvhPnw4XHuqfrHSZ+5P3ZYyZDsdUNTv7lSsE0ZVUNTrpteoDZnI+vVUrVJDHtwO+zqIUm9UBWbQ8UFa237qvWgaPyo+Sp6pTOXfDrc5/CWWkWXn5M/vLEwAGzZsiA4dOqB8+fIiCWPMmDG4ffs27t69C1tbWZZmv379sH//fqxevRqOjo4YMGCAkC85ezZ1yQvpHcEHKGP82/B66TKEzpsHKstmX7uWKMlGGY70wZz07p3QMqMPZqmuqh8lQ8TEaI1Vyxi7Sv9VSNI16lffFCuXI08eERMpmXS9nXvBH7ApXVoIS1PJOp/ly/Cil6w8lWT5tm6FdYnUBZeV21Pm8P0ymmvL2tevD68Z01O8blulCvKskGUaK8d7kmfwdmknOExaKjJxJbMqVRIxN2Qf/rS+sI0bBfFx6fk/eAxXxFVpQvlB5SpCIohMOanneZ8++HDyFDyn/AqnNm3S/wF9HJFkS7rs74R1sxNhkQhxTW6oFMzjJk0R9/gxlJOdSJYmePoMMRs988IXzqvsRcqazz33Nzh8lDr6ZJs1YuB1d9dh5mWFRiHFx1GcnGQtd7fEo/BHWFx3sZD30fiswx4IXUCKCWy9pzXyO+XH4jqL0yTpRixbr65SbKqPvQ8OtDqgV19unDoC/PmdhQmg+qMnjTp3d3ecPHkS1atXR0REhNDn27BhA9p8/MecvIXFihXD+fPnUalSpTTfP3yA0oToszQg+Re6ViQ9PtcfeuJhteqC4ElW+PIlIXshGZW5IlmUL1Vn9bOAomUSugInLNLK7Iy5/wCxfvfg0Ly5+DAkAkgaf8qJGTQFEQQiCvpa6KJFGuVRnL7vAM8JEyBdQyqP67NsqRCvVs72JiHuhBCldFq1hfgsXQK7GjUQsWcPXo6QeXvNc+US16qaSKt6okrRmzeEh5e8veQVjXvyBNKY+u5Zn/aUuTpgym24RwB5N2yATZlv9Oku2tKaSXqHCHeBgwfkZf3Cd+xUuR5XH/9R7TqIf/nS4Hn1XqgBHRKSEvDNWhkmVDKNqniUzFkS65usl48mZYZva7YNRVwUNz/apiO86D9KFskotuD6Aiy7uQw/lPgBpHHJln4I8Od3NiKAjx49EgLFt27dQvHixXHs2DHUqVMHYWFhcFLyfFDljsGDB2PIEM0B58rHjw9Q+r0ZjRkpYOBAvD9yVC5aK8U9iTHNzFDsjvbEB2PmzU59pWtB9T2nlpyRFj7h23ekuOr1+m0OHJs0wYcLF/FcQ9UKqoyhXNaPJGLin8tqp2oy36NHkcM7t8YsY2WNO4r7I4mahJBQFeFm2xrVkWfpUqEfSRnMRAYLnTqp4i1Na5+GvE6lv+pOO4aigdDp2lrTHMoZwEWuXZWX85Oqskh9KCYw13hZDdsYPz88+a6l+Lng8WOw8PQ0ZPmfvA9V9Wi8QybE/n3R77HRb6Mo/Xe0rSypiBJEiCDS/4+1PQY3G82ah598oekwAYlCU4lDM9O0wyvSYbpsMwR/fmcTAkhVOZo3b47w8HCcOSPL+iLPX48ePUTsn7JVqFABtWrVEvGC6kZtldvTAfLx8RHeRAe16hPZ5l2UATb69PuOiL5+Hbl//x0ODeoLz4ekfWbu4YFCJxU1ejPAcjPlEpTjB5U34D5iBFz/18OgPalnb5MsTO7f5oj4udgnT+DfKGVt10LnzuJh5ZQSM9IClMvQmVhZgYgPxTWShcydhzfLlsnX6j58GFx79hS/v/vnHwQO0uxhIRHsiB3bZbWjla6iDdq0jp3Gnx2PfLO3iSohLiOHwaOHbJ36mJRZTck7RS5fkndVJ4A2FSuKK2Ly9N4jaaOPNaGL3r6VpqdYn/WkZ9vzL8+j95HeIgt7baO1qL21tvDcXet8TRAl5QSRa12uwcLUIj2n57GyAAJMALMJAaRYv4MHDwry5+0tK/BtCAGcOHEiJk1SyGBI7wEmgF/2X4PHdDXn7y+EniWx4vdHj4Kuupy/7wC7atW+7AKzwOwBg4fg/SHVZAHalrGlwqR4M+nqV4KKSHzQuHFIivyA94cVwe+axLyV4SXZFBKPJqM40EKnT8lfFkk7CQmg8xL/4gWUZW3e/r0WwdOmaXxSOQcNlF9XO7VtC89fJ3/yJ7rl/hY8nzIRTS4nI75DE5ScOCfNOUn25ID/AUyuMllUxIi6fBnPunSFeqJHfHAwHtWoqTKeQ7Nm8Jo1E37FFFU/MpKoufrmCZ9fL/yK6t7V8Xut3+XXwQdbHQSVh7sfdh8f4j8IgniodcpzmyaY3CDLI8AEMBsQQErs2L17N06dOoX8+fPLD7UhV8DsAcyY/yY8qFJVlDDLv3sXrJSyvDPmajPnql6OG6ciEE11hEnjzthrQopPC9+1Cw6NGuH/7F0FVFRbF/5oJFTEFgPBLuzERFTsZ3d3d/uw69nt099ni92JrdhKWJiIiiKghIoi8a99rnfmDjPADMMQevZab72Ze09+d493s8/e3za0slIJTtDKVTKjTmxgmCcPYrJnQZyPPMv7e+nCKLV0HV40dBYMwLx5UOT8eaUxRQ8Yeb4KbhEqk1CSyIcZcsMuoaNlMgZzDB6s84dIR5eLRzmi2alPCHYsCcd/lcm5pYuQUob0Lt0boyqOknk1M5Uvj0K7drLmFCtH1SXKxOVDy7Kd8GbAAFYmkTgzKU5QNAzzzJmDrG3+0vk+kzuBSOHStURXTKgyATV21QARgrvYuuDEK3myBBmIqxsIfxBw4QhIEeAG4G9sANJf+8OGDcPBgwdx8eJFFv8nFTEJZNeuXWjTRqhO4Ovri+LFi/MkkAz07wSjdaFjq+hoVtXDKHfuDLT6jLNUqn38smUrxFLy1MgRIAodKjUXv4qErnZEFUekZeyoVFyYYxkYLRVqts5rp48pow6wYH8xScTIxgb27meVlhTp84CRgTNew2tXWVxf/JJ2xJNIuvTBVdHjn2PEcGQfNEhX21QY9+Ca0Si+4iQ+FMuOeoevJDrnwWcHMd1DiONrVKgR/qnzDz7vdsMHV1dYNGiA/KsFPsyZ12di71OBCsi7uzfiIiOVMq6pJrTdieOpskdNJ/n8/TNi4mJAGb6hP0KxvuF61MhbA00PNIV/hL8sIUQct1epXhhdabSm0/D2fwAC3AD8jQ3AwYMHs2Ne8v5Juf+I7oV4AUnoaPjEiROMBoZi+MhgJPH4RZia1G+AK1BSCOn+fsT5C3j7yyNT7P49VvuWi+4QYMeoQKrTZEgzf2l+Ip1+1d8Z/kOH4rMlsNZFH3e63YWJgYnMAFRFckx9qYTds9p1EBMczGoDE0ly/DrFxIGXuakLnteVEw1TX7G97hCWj3zl2DpkH7scgdYGqHPVRwFzqlFMsW7ZM2VnHSZemYjjLwWjrUz2MtjZdCeC165F0PIVyNK2DfLOns3uUWUJqjBBcqXDFWQ1zaqQVU3XpQZjauxTnTlI74geh5JjwqPCWReK+bvT9Q6L7+tyvAu8gwXaH6nMqjkLreyV61KrMydv83sjwN/fv7EBKGXWl6rx5s2b0fNXdqFIBE1eQCkRdG41vUhcgVL/H4jvvr4sJsy6b192bCU1DBKq85r6q+QzpjQCz+rWQ/SHD7JhKdbvTjM7jL8sr+7g08OH3Q/ZuJEZPpTYYFZRNd/gmyFD8eXcOVmt3YBJkxF28KBs/NwzZ8CqfXu8Gzce4UePsuvEiWjp5JRqxu9Ln2v40a4vvhsBi+Y5YI3TWmawUYJDi4MtkMkoE4tvo+NiojyhmDeSbKbZcKHZCfh17MTojqiOc84xghdMWv92d7PdKGVdSskATMkScGE/whDyPQSFsxTWSiXcnrhh9k3BiBVFmvVLhuHlt/J4T7HNTpedKJOjjFZz886/JwL8/f0bG4CpobJcgVIDZcU5pFmKFOBPnH+ipOeg9dRH6veaMfLhQ/i1kZMvE/fgicLhmHNzDtvofMf5aFpYqF5CEhsVBf1EKrS8n/43QvfsgRjT92bwEHyRxAvmW7qExSUSb2LAxInI3LgJsrZOXU9S1NcIvKhYhe2nxygD9Kw6GIMdBmO152qs8xJqD+9tcxsK7QAAIABJREFUvhfjLo2DX7gfzI3MZUbg1Dv5UfbsK9bGcsIo+Dcqja0Pt+JagJzkfnGdxXAu5IwXzZoh6vkLAThDQ9jucUu0nB8ZdWaGZjAyMMKSu0tw+tVpLKm3BEWzFmXXpOK8zxnvv77H4VaHtTICRUJk6djlcpTDdpft7BIlfhx5cYR9Jj0QvaHXO12HhbHF7/Vj4LtJEQT4+5sbgFopElcgreBLVmepx09KSmxe2xEFJBQfyRqcd0rXCHy7exevu3Rlayx89Ai2RF4AEeXWzFsT6xoKBpG68nH5coSsXQdKkLBZsxpvhw5jyRCi2B46CNPixdUdTmftnlSugriICIzqZ4DK1VqDjjQ7H+8Mn2DB2+mQwwGeQZ7sc4+SPXDg+QGWDCGtizxosAFCsugprZH48yZXnYyf797hy7VryNqqFeiAPzHD2S/MD1SruF7+eizOsOzWsrJxW9u3ZhnIotCxrXh/QuUJ6FpSeHaayhm/MxhzaYxSN+eCzlhcVyAhX+u5Fmu81rDPNzvfxM4nO1k8IJWH48IRUIUAf39zA1CrXwZXIK3g07gzeXV8y5ZT6mdsa4vChw9lmJq8Gm+cd2AISOlLivt44x/PZdj6aCt6luqJMZWUDYTEYPu0bTsC5wjeQ5PixRVqRtO14o8eyvgD0xJ+0Ts3q6M+rGvXxwLHBai+qzo79jX9EYc4PeCHsR6s9CxwzGU/+l4ficefHmPVmmhWReR6cT0sba2aQJhi5xbVXoQGBRskucUXoS+gBz20PNxS1payjYl6Ripe3b1klTSkXHxUo1eVMUZGIiV1GOobqlwDxStS3KIoNhY2ePvlLftKlTGoQgYJxQWe9jvNqoGoU/UjyQ3zBr89Avz9zQ1ArZScK5BW8GncWSS2jd/Rqls35J4yWePxeIeMh0D42bMwsMwM82pVZYkPUkNA3R2FHT2GAFU1gQ0NkWPYMGQfoFjvWN1xU7qdf+8++OrhgdVN9RFdrRxGNpgOKhNX7G0cpuyOQag5MK6PAbb8Zwn90AicHFAO/1l6YceiGBjGAoOGGCAks6L3j5In6uevD3d/d7V48h6HPGaxg1QmLSk50uoIbLMIdFuUtNH1hOD161emH4ZXGK7Ufei5oXjy6QkOtTyk8qhWpHsRO3p282Sl0SJjIjHEYQhL+uHCEUgOAvz9zQ3A5OiNrA9XIK3g07hzxLlzeDtkqFK/PHNmI+svKh+NB+UdMiwCjfc3xrsv77DWaS1q5aul0T4iLlzA20HKfH7a8hpqtAg1GovJKcGWQPYI4NOoThhouhfDjsTA8aFgkFEG9KATsezz2yblMMvuAdavikG0PtBlnAHi9BUNQEoS2d10N5z3OzPPG1XPkCbNEdVKr1O9UNy6OGbVmIWNDzZijadwvKpKZtecjVWeq/Dh6wfQ55b2gpeQSKknXBHqL7ewa4E5tQSPqyjSer6UqUvH21L5EfMD9fbUY0faooiJPmpAx5twBBJFgL+/uQGo1U+EK5BW8GncOWTT//Bx0SKYVa7MqhyIUmDrFphXEYLlufwZCDz7/IzFohnoGeBap2ssAUITISqYj4v+YQTQcd+/y7pKa+ZqMp6u2qoiwW4/yRALt+mj0NsopWljqjtgSjEfzP8vBiGWwMQx1qCkDakUzFwQe5rtQdWdVdnlG51vKOAnVtmge1OrTmVxhY9CHiW4RTLKFt9ZjP8e/odCmQuxhA/yMm702Yjl95azftam1jjZ5iQ+ff+EnJlysmQRqnHb5EAT2bhn255FbnM5j+eOxzsw/9Z82X1t4gh19Xz4uBkXAf7+5gagVtrLFUgr+DTuLNajzT54ECMFDtm4iY1h534Wxr9K/Gk8KO+QIRFYcGsBtj/eDqcCTlhab2my9/Bh7lx83rpN1j+9UQl9uXwZb/oPUNjfwwJAKf+Et/zVNhfMXwXiZW5g4aCczOiSClG/7Gq6C5W2V0JUbBSjkqGjVMrsNTMyw+iLo3H2tUCgTdfJE2esb4w2RdvgytsrLMbunP85dn9/i/0oalUUF99cxLDzAo/qJudNqJKnCuIf37Yr2o6RUFMsIMUE3np/C33OyGscb3TeiKp5BKOUZPaN2XDzdUPbom0xssJIZDHJkuznzDtyBOIjwN/f3ADU6lfBFUgr+DTu7N+vP75euQI68o0JC8fHhQvZGMW9vXgCiMZoZuwOg90H48q7K3Ct7soMk+TKx3/+kf0hQWOkNyohqrbytIrcKNJkn/fs9LChew5QNYzFd4VsWZKquatiY6ONaLC3AT5++4gldZcwGhVKoGhk24hVC4kv1fNUxwbnDeyy1LMnHslSUkqT/U0Q8DUA/cv2x+0Pt3H/4/0El0v9tj/ajgW3F8jazHOch2aFm8m+U3zgpbeXML36dJDxyIUjkJII8Pc3NwC10ieuQFrBp3Fnvw4dEenlBZtVK5kH8N1oIfMzvb20Nd4Y76AxAm2PtIXvZ1+sabAGjjaOGvcXO8SPBUyPuuTXqTMi76s2popc98DzBk7QNzKCVY/uCHXbg+jAQLa9e4X18Gxqe7jWcGWeu8HnhJhHSgBZXn852hxpg6efn6qFnVhzlxp/+/mNGYxOBZ0UuBfXeq1VGStoaWSJiJ/yOD4aY53TOgx0H6gw9+iKo9GrdC/ZNUp2oQQRbZ+xWhvkjf44BPj7mxuAWik9VyCt4NO48wuXpoh6+RIU80cVHgLnzkOmCuWRpamcAFjjQXmHDIkAVb6go819zfdpRftBNCRhhw4zz7JVp44svjS9ydcbN+DfU24YievLu/gfpvtR/v7QMzSEUd687JbIlfmtYE4UP3aCxfdRDB9l8pKICRlSPkFVeyYevcjoSHbr7+p/s6PYxOTc63MYeXGkUhOaTyRpVtW/c/HOjLePklMudbjEmsTExqC2W21G7yIeM6e358LXk7ER4O9vbgBqpcFcgbSCT+POT2s5svqt6YWkV+MN8A4pgkBUTBQqbhdKvF3ucBlWplYpMm56HmTc3t7oPe26bIl5Fy1Cluby41Lp2oPXrUPQsuWwWb0Klg0Ejj/K0G24ryH7TMepdKy66v4qrPdeD0tjS4VMW3GsIlZFQMk2JCf/OgkbS5tEIXoT/gYuB10U2sysMRPEIbjl0RaVfck4LJ+zPIsXJDnR+gQrcdf+aHsERQYhs3FmnGt3DqaGpun58fC1ZUAE+PubG4BaqS1XIK3g07jzk7Ll2NGv/Tl3GOXLp3H/9N7B/bU7e1l2LN6RB7wn8rDeRLyBywEXlphwp+udVKvNm5b6M+vKdLQcuBdGMcIqCu3dg0xlVNe4ZeTKoaEwtJIbxtKqHA0KNMCyestA175Ff2MewvVe6xmViyhjKo5hOkhZvE1sm2BCFYHOJTGhOMByW+VE7WRoTqo6CVsebpFlA9e2qa1Qs5eeH62j8g7B8zqjxgx2X0wy6VisI6ZUm5LU1Pw+R0BjBPj7mxuAGiuNtANXIK3g06hz7I8f8C3nwPoUvXMbBhapU9+TXkSUrUgxUPkz5090zS9DX7Ijs1LZS2m0N2oc9C0I9ffWZ/0o47FPGXl2pMaD/eYdxHg2+6z2ONjy4G++W2F7+57uA4ZOk2X/2l+6CKNcuTTau1hPt0z2MtjZdKdC3/P+5zHiwgh2jUqpUTZwcmTylck4+eok8zC2LtKaDXHw2UFM95jOPo+rNA6L7ixin6mc3Ir6K9jnfmf64cb7G+wzVRwRSac59UtyngLvow4C/P3NDUB19CTBNlyBtIJPo87RQUF45lgb0NdH8Qc+qVamq/rO6vjy8wuq5K6CTY0E2hlVQoHxIq/ahfYXkD1Tdo32J42fal+0PaZVn6ZR/9+9MXmJyMNkoG/APEr/3PkHDQs2ZBmsf4IQGfKcqfXR48gX6OfJjaJnz7K4P03E1cMV+5/tx6r6q1Anfx2FrhRzR5jSHy/STFxNxqe2qkq7UaxmXbe6bCiqFNL8UHP2ebDDYAwqN4h97nO6D259uKU03fJ6y1G/gPCHEReOQEoiwN/f3ADUSp+4AmkFX6KdP+3ciaDlK2CzcgUjeRbLwOlnyYJiNwVPga5FatTRXESK26G4EEgfX46+OIrJV4VydKpesImtlV6+VN9VDLiXekZ0vceMMP7P2J8sJow46f7X6H+MAJoqgAwoOwBDyytXhskIe0rOGslLHBPwATlyFoRB5swaD0F6RrQveSzyaNxX2w6BXwPx4dsHlMtRjmUQewd5Y1uTbchqmpUN3fFYRzwMeag0DbVxyCl4/rlwBFISAf7+5gagVvrEFUgr+BLtLGYyUiOi5gg7fBgBEybCtGRJ2B7Yr7uJJSOPvzyeHWdJJX4pKvJK3flwh3lWTrw6wZpSdQoKmlf3RSsN0Kf+xMe2o+mOVNljRpjEL8xP5jUiEmGqEEESv3JERtgLX6NqBK4HXEf/s4r1l6kqyIm/TsBI34jDxhFIcQT4+5sbgFopFVcgreBLsHNsZCR8y1eQ3afyXO9dXRF+5CisBwxAzlHKVBMpvRJp0Lw4NpW38urupTDVrie7MPfmXKXpOxTrgKnVpqq1LLGsmdg4p1lOlvnIRUCASIV7n+6tAIddFjscanWIQ/QbISBWd6EtiWTVv9H2+FbSGQL8/c0NQK1UkiuQVvAl2DnSxwd+7drL7hdy243ARYsQeecu8i1dgsxN5PVDdbMC4PP3z4yHTCp5zPPgTNszCtec9znj/df3SsuokLMCtjRRTX0RvzFVTOh+sjsM9QwRHRfNbtNRZ+Xc6Y+TTld4JzbuqVenMO7yOIUm0soUabEmPmfKI0DZv0PODWEDa8vvmPKr4yP+bgjw9zc3ALXSaa5AWsGn1DnS0xORPg+gZ2KMD9P/lt3P3KwZwo8dY9+JBJpiAnUtD4IfoNPxTmyaDQ03sOMpIsa91UUeqP7883O0PiJkOoqyusFq9hIrka0E9jTfo9YyxRcf9aHjLu9gbzQv3BxzHQXPIsUiGhkY/bFHYdsebcPC20LZP1Gq5amGf53/VQtf3ihjIEBe900PNiEkMgTjK4//I+h9MsaT+T1Xyd/f3ADUSrO5AmkFn0Ln6E+f8KxGTXZN39ISsRGKpaPExoWPH4OJnV3KTZzASKf8TmHcpXFwyOGAtU5rWZIGycX2F2GdyRpeQV7oeqKrQu+KuSqyFxdVXKAsYMoGVkeOvzyOiVcmskxjon8ZcHYAyNs4ttJY/Ij5gcV3FiOvRV4l6g51xs7obSjGctm9Zdj8YDPoCJ6+kzjmc8QapzUZfXt8/RwBjkAaIcDf39wA1Er1uAJpBZ9C52/37+N1p84K17K2b4/QPYpetKI3rsMgq5A5qEvZ5LOJGR5NCzfFvFrzUGF7BUTHCsezZAQSQe7B53IOurI5ymJSlUnIZZaL8fmRsXKv6z1GW5KUuD1xw+ybs0EEvXNrzUXNXTVlR8HSvsmhl0lqbl3ep8oQi+8uRs9SPZOVyUn8cXNuzmGeT6LiIXJioilZeX8lIwy2zWKry+XzsTkCHIHfGAH+/uYGoFbqzRVIK/gUOoefOYN3wwUiWhJ9MzMUPnkCz+sI/GGiFH/0MFU4AGden4m9T/eif9n+GFZ+GKtwIHqf6trUxcW3FxXW5d3dmx1ZEdUGlSmLiYuBe1t3UNmydd7r0KtUL9hb2asEbI3nGqz1WouWdi0xu9ZsdDnRhdFkxJd1TutQM5/gJc0I4rjbEaE/QpEcwmaifqmwTZ4IRPul6hVkJHPhCHAEOALaIsDf39wA1EqHuAJpBZ9C50/bdyBw9mzZNbPq1VBw82ZZYXvxBlHCpIbQMaxHgAeolilVNBh7aSxO+51WmrqAZQFmmFDdVFEa72/MeOpq5q3JxqCqBqWtS2NXs12sCRl8VO1gkMMg/Iz5ybyLJJ2Ld2als6TZkHSsbKhviJvvb2aoCiFkCDtsE/jbKLnlfvf7eBX2ipENk1FNfHCJiX+4P5oebKrQ5ECLAwo4p4Ye8Dk4AhyB3xMB/v7mBqBWms0VSCv4FDp/XLoMIevXy65l69ULuSaMVzAAUyv+jxbR7GAzvA5/jU3Om1AlTxWE/QhDk/1NEPFTMTbxaserSnV7+5/pj+vvryvsz8LIAtc7X4eU84947CjBo+XhlqztxCoTQTx3Ox/vxLxb89g1OlYmgmg6jm5SqAkW1lFMhki5J5CyIxHhcIO9greOCJxvd7nNCJyfhz5XSqYRZyajUTwylxJri/cpAYcScbhwBDgCHAFtEeDvb24AaqVDXIE0hy8uJgbvRo5ExFl35F24AFlatGCDBEyYgLDDR9hnAysr2KxZDbPy5fG8USP8fO2PrO3aIc+smZpPmIwedNRbaXsl0DHkqTankM8iHxslPh/dmTZnVJI9Dz03FJfeXlKameoJb3+8XXZ9ad2lLL5t6HmhmgXFDFK2r5QOY2uTrcxIHOg+EIUyF8LR1kc13hHRzFBSCRHrppbQETYdZYtSzKoYfD/7yr7HJ9Qmwm0i3s5rnhcBXwOUlkkxljtcODl2aj0/Pg9H4HdHgL+/uQGolY6nhgKREUJHgqWsS8mKq2u16DTsTDQPr1q1xg9fuSFgf/4cjPLmxcuWrdh1m1UrYdGggYwCIur1a0ScPQur7t2hb2ycKqsXvXRU0eNO1zvsCJZEWpGCDLe7Xe+qpKqQ1vVNbMF0LExGmbu/u0JdWykx9I3ONxD+IxzO+53ZUeq9bvc0oseg8lpUZis+hQ2ti8pzkZFWOntpLKqzKEVpZs74ncGYS2MS3L7UAFRFuh2/IyWA9CzdM1WeP5+EI8AR+P0RSI33d3pHUS+O/vXlkiwEUkOBjrw4wmpnkqxpsAaONo7JWmt66PTz3Ts8b+CksJSc48fDqktn+FaoCMTEwP7CeRjlSf1apdJF3Q28i56nejLPH3kARfn68yuq7azGvmY2zoxrna4lCOvjkMdof0xOZp0U/pQkMrrSaNaMfpKU/UoVQShejqhgyCNJ4tHJA5bGlkkNJ7sv5dC73OEyrEytZPdE+hm6sKj2IjS2baz2uEk1VMXdJ+0jNQADvgSg0f5GiQ5JpfVsLG2Smpbf5whwBDgCaiGQGu9vtRaSho24AagF+LpWoHVe67Dac7VshZqQC2uxLZ11jXz4EH5t2iqMn61HdxDRM1X+oKPfIh7XNPJw6WKxotGtqhxVmS1l2JSqysJJ1yJN7hCvU3k4MuoeBj/E+TfnFZY+rdo0tC+WsMFYdUdVfIv+huOtj6NA5gJqb3ut51qs8RL48lbWX4m6+eVZ1SLVDd2j2EOKQUwpIaqWDd4bGCH240/KiTvicTfNp6rSB10nDyvV/TU2MGbr48IR4AhwBFIKAV2/v1NqnbochxuAWqCrawXqdqIbPIM8ZSvMapIVVzpe0WLFadv1y7VreNOnL1uEdf/+CNmwgRl/ZpUq4oPrDJjXrIkCmzam7SIBRslCmbp/FfmL8c1JpfzW8oyjj46HPbvLn42qRVMGMB3nUuYryd/V/0bbom0ZVYyYISv2W99wPWrkrZHg3sXM4m1NtmnEqUfeYzJoSYaXH45+ZfvJ5ph9YzbcfN3Yd8rK3e4ij0/U9iGIY3cv2R1bH21lw9lY2LAkGMKPEmDEmERp1rN03vhxgtquiffnCHAEOAIiArp+f2cEpLkBqMVT0rUCuRxwwZuIN6wiBBkRmpALa7EtnXUNO3YcAWPHwqxKFWRt2wYB4yeA6F6McuVG2KFDsO7XDznHCMegaSVPPj3B/x78D5SUQPx/dAQrFbpPFUIGOwxGE9ukaxJT9nCt3bXYEJsbbUal3MJRLh0l05GyKCdan0D+zPkT3HanY53wIOQBVtRbgXoF6qkNT4+TPXDv4z1Ze/KqkUeNYktHXxgt4zOkY2XKaCYdSwkZf2k8TvqdxITKExiJ87/e/2JKtSnMuCYjcKfLTpTJUUaBBkc6r7QUXkqsh4/BEeAIcASkCOj6/Z0R0OYGoBZPSdcKJBoJB1sclNWcvdLhCrKa6r4ShhawJNhV5PqzbNSIZfW+6dsX+pkzI/brVxb/V+C/zTCvJsTYpYXceH8D/c7IPWTzHeezSiDaiNTbJ6WMeRH6gsX5UWYxCSV3UGJJQjLIfRCuvruKIQ5DMLDcQLWX5LTXCYHfAmXtqS8dQVOcIx0pS6WFXQuMqjgKu5/sZl67ERVGJPvoVeRRpMomze2aMxJtMi47H+8Mn2AfLK+3HPUL1Ic0zOFoq6PIlikby4Kul78ezI3M1d4nb8gR4AhwBDRBQNfvb03WklZtuQGoBfK6VKDv0d9ReUdltjpKNmi0rxHzpNBLslCWQlqsOu26Bq1ajeBVq5C1QwdYdeyAV63/ki3GMHdu2J9zh55B0qXTUnoHLDs5/BWrN3vo+SHZ8Lua7mIZstrKy7CXiI2NVVkJhO7RcXLBzAUTnWbJnSXY/HAzKAzAvZ0749ZLSqgKCSWPEBG1ulIhZwUFj6E6x7CPQh6h/9n+yG+RH7NqzoKZkRlGXxwNykBe3WA1atvUlk0//PxwXHhzARTz2K5oO5CX++2Xt6zmMlHeUDUVLhwBjgBHQNcI6PL9reu1p9T43ADUAkldKpCYGSnSjTQ50IRVl9A0BkyL7aV41w8zZ+Lzzl2wHjAA2Xr2wLPq8pi3vAvmI0tLgRA5tWW913qs8lylMC2RLi+ovSDdGCRfor6g+aHmCI4MZuTQnUso1k1Whdmq+6uw3ns9zAzNcKbtGdlRtLRtHZs6KjkLxTZJGYDEMTj24lh8jPwoG5bmI6OTCKzj6+us67Ow5+ke5sU8738eTz8/ZZ5P8o6S4ciFI8AR4AikBgK6fH+nxvpTYg5uAGqBoi4VyCfIB51PdGaB8hQwL8aAxc/k1GL5qd7Vv3dvfPW4jjxzZiNrmzbw69wFkfeE+DT7SxdhlCtXqq+JJhQTLMTJxfJvabKYRCaljNj5t+aDqopcaH8BpoamiS6RKm9QEgolX5xsc1Jpn9SZElNmXFdMdJEOKs3Wpdg9KolHJetcCrsg6FsQ6u+tn+gajrQ6AtsstrI2YlYyeQXpqJckI1U4SW86wdfDEeAIJA8BXb6/k7ei1O/FDUAtMNelAl18cxHDzg9DSeuScGvmBrG6BPHFkfeEvCV0dHng2QFQlQRpLVottqTTrs/q1EV0YCAK7trJqnxE+vjAv3cfxvtne/hQmnnbau6qifCocNne9zXfh2LZiukUi+QMTnF0VI6OKmVQckXXkl1VDkPJJRMuT5B59g63OozCWQrD1cMV+5/tV+hD9XXJUJQK1TC+9eEWSxTZ32I/iloVZbdpzBOvTrDP5Bnc/mg7FtxeIOtKhNnRsdGy7+TZu9n5JqtuIopoxErbJlRRJTkY8T4cAY4AR0AdBHT5/lZn/vTQhhuAWjwFXSoQGXZ/e/wNx3yOWOO0hnl+6OVJQnFaW5psgftrd4y6OEr2QtZiKzrvSokevhWFDNiiN2/AIEsW9jnmyxfoGRunWpWP+Bslo6r8tvIsSYGkTZE2zCuWXmPRNvpsxPJ7y2FlYoUa+WqAYkUpS1wkSSb+QYodjYmLYfuhdpc6XGL7+fT9EyZdmQTyLos1jcnDR3WLyRvXukhrvP/ynv1BQckalDySM1NOuNZwRa18tdDnTB9Z0goZgNOvTcfB5wdlkJKxR0fpRAJNUjZ7Wexoqli+7djLY2wNorSyb8XiBrlwBDgCHIHURECX7+/U3Ic2c3EDUAv0dKlARJux4v4KiC/I+JUVPLt5gsh2Nz3YxHbg3d073RottL6ot+/wwskJeiYmKO6VOH+eFo9E464UW1d9V3XW73qn67AwttB4jNTsQEZcHbc6ClNmM82Gi+0vMu8bxeSRoSaKfVZ7HGwpN9LoupR4OaEYv4lXJoIqhYjS2r61grFHFVIo9o+oaUjWO61nBmlEVARq7BJiOweUHYCh5YU6x6JI6xzTNfJmU2YzF44AR4AjkJoI6PL9nZr70GYubgBqgZ4uFUgkx+1dujej5rjgfwHDLwyXrZbiuugYzS/cj11zb+uOXOZpE0OnDoTfnzxhdYANsmdH0avph8yaPF5UZzex2r7q7C+12sT3WErnJX0gQ23v072yy+TRJA+eVIiaZvvj7cyTTFx8qkSTUnZEU2RvZS8b5uCzg3gd/hpDyg9Rorbx/OiJbie7ydpS9RFe5SO1tIfPwxHgCIgI6PL9nVFQ5gagFk9KlwokEumOqzQO3Ut1x+fvn1HbTU6nEX/Z/2v0P1TOLdDGpEf5dvs2XnfrDmNbW9idFOLI0oP4fvJF26NtQV40OirNCFLXrS5CvockulSqY0zVPYh8meoWayqBXwPhtE+xbnNCY9DRr7oZvK/CXqHFoRayoRbWXqgWobam6+ftOQIcAY5AYgjo8v2dUZDnBqAWT0qXCtT3dF/c/HAT8xznoVnhZmyVRBo88fJERrERFBmksHLX6q5oU7SNFrvRbdeI8xfwdvBgmJYtC9s9Qvmx9CBEiNzzVE/Gw3es9bH0sKQk19D6cGs8D32eaLseJXtgbOWxSY6VUANVtYypbdU8VZmXkY6ISSjG8HJHIZtXHQmJDEHdPfJ6xP86/4tqedKO/FudNfM2HAGOwO+HgC7f3xkFLW4AavGkdKVAZ1+fZUS6JBsabkD1vEKMmlTKbS0nS1yg671K98LoimlbRi0xKMMOH0bAhIkwr1EDBf4nxC2mBxGzrUtbl8auZrvSw5KSXIP4xwE1JMOVjlvjS0p4hMtsUT4epj9IyucszyhlSEpkK4E9zfckuWaxAWUWV9hWQdY+vWZcq70h3pAjwBHIkAjo6v2dkcDgBqAWT0tXCiR98UppOKRLnXJ1Co68OMKOLikxoG7+uiCOwPQq0jJwNsuXpZtl/vfgPyy+uxh1bepiZYP0i58UMMqipWxaEqJx2flkJ/Y93SdrUjFXRfzX+D+tMa6/p76Sp3mT8yY45HRAxe0V2fjV81Q87gYDAAAgAElEQVTHBucNGs1F2e2U5U5yvt155DDLoVF/3pgjwBHgCGiLgK7e39quKzX7cwNQC7RTWoGI14+oNxruayhbFRH+Zs+UXWmVlPEZ+iMUVFO275m+MNQzxJHWR5DfMr8WO9Jd1+B16xC0bDmytG2DvLNn624iDUcm7G6+v5kor56GQ+q8ubR+7u0ut1n2NxmF4T/CWRYz0dhYmVppvQ7SLYrZo9Jt9McGyek2p5HXIi/EP1LUrUoSfzEbvDcwnkGeAaz1Y+IDcAQ4AslAIKXf38lYQpp34QagFo8gpRVotedq0MtdKkT3YqCfcH1cygptf7Q9fD/7YkaNGfiriCKprxbbS9GugYsW4dOm/yFbz57INXFCio6d3MHI4CbKEqqxnJGOIikWtPfp3mzbSZVqSy420n5iQhJd8+ruBX09fZx4eQJPPj3BsArDlDJ9U2JOPgZHgCPAEdAlAin9/tblWnU1NjcAtUA2pRVIVcyVOi94kSS6Z6meGFNpjBY70l3XgClTELb/AHKMGI7sgwbpbiINRhYNKT3o4W7XuwoVKzQYJk2a7ny8k3l7HW0cdT7/kHNDZGXb1NFHnS+IT8AR4AhwBLREIKXf31ouJ026cwNQC9hTWoHiG4AjKoxA3zJ9k1yh2xM3zL45G3Vs6mBVg1VJtk+LBm8GDMSXS5eQe+YMWLVvnxZLUJpTLAFHhtSJv9IPNU26AEeyiHuB99DjVA80LdwU8x3np7fl8fVwBDgCHAGNEUjp97fGC0gHHbgBqMVDSK4CUdLG1XdX4WLrwsicSeg4suzWsrLVjKwwEn3KyCs6JLbMa++uYaD7QFazlZJG0qO8atce3318YLNmNSzr10/TJdKxOVW5mHx1MluHuoZ2mi46jScnXkCKRU0sHCGNl8in5whwBDgCaiOQ3Pe32hNkgIbcANTiIYkKFPzkCaIPHEC2Pn1glDNnkiN2O9ENnkGe6FemH4ZXEKp7SEto0fedLjsTrNIQf4IHwQ/Q6Xgn5DHPgzNtzyQ5f1o0eFa/PqID3qOQ225kKlcuLZYgm5OMP5HHLpNhJtzofIPFtXHhCHAEOAIcgT8DAW4AAtwA1ELXRQV60LUb9G/fhrGdHeyOJ04mLPX0SUl0n35+ijZHBCLns23PIrd5brVXRjxwzQ42g4WRBa53vq52v9Ro+OPlS3y9cQOBM2ex6ezc3WFsky81pk5wDlcPV+x/JnhKNeWxS9OF88k5AhwBjgBHIEUQ4AYgNwC1UiRRgW4VLwGLuDg2VvFHD6Gnr9qb9DbiLSuDRfQXJFlNsuJKR6Eu7o7HO0DJHFTOjUh8NRE6Uq7jVod1SSprWJNxtW0b8+ULnlZSLE9X7P496GfKpO3QWvVfcncJNj/YzMZwLuiMxXUXazUe78wR4AhwBDgCGQsBbgByA1ArjRUV6G6VqsgUFsbGKnLdA4ZWqjnYRl4YiXP+52RzGukbMSLf46+OY6/vXlbfdVTFUehdWqD4UFekZbuudryKLCZZ1O2q03Zfb92Cf/cesjmMCxeG3YnjOp1TncHn3JiD3b67WdOJVSaiS4ku6nTjbTgCHAGOAEfgN0GAG4DcANRKlWUeQPsisDAQuPoKHz8GEzs79jnC3R0f5s6FzZIlyOTggPJbyyM6LlphThMDE/yI+cGukeF2vPXxZBlwVXZUQWR0JMtmTS9k0CGb/8PHBQtk+y24YzvMKgoVJNJSxlwcgzOvz4Di/zw6ecgScdJyTXxujgBHgCPAEUg9BLgByA1ArF69GosWLcKHDx9Qrlw5rFy5ElWqVFFLC1UZgIY5c8Lu1ElEnDuHgHHjFYyf1q8mI+BrAKZXn47l95Yj7IfgNRSlYcGGWFJ3iVpzx2/UYG8DfPz2Ebub7UYp61IJjhH77RuCN2xAZmdnmJYsmay51O30/m9XhLq5yZrbXzgPozx51O2us3a9TvXCncA7WFR7ERrbCjVtuXAEOAIcAY7An4MANwD/cAPQzc0N3bt3x7p161C1alUsW7YMe/fuha+vL3Kqkc2rygCkn88TxwIofsVf6ZfUa6wJvhrFsCSPQe6D8Dz0uUIbbehIWh9uzcbb0HADquetnuCv+OPy5QhZK1QbKfHksU5+7XExMYCeHt4OHYYv58+zOQyyZUORK5eh98tTqpOJkxh0wa0FOO9/ntW3pThMqmtbJY96xn5arJfPyRHgCHAEOAK6QYAbgH+4AUhGX+XKlbFqlUCeHBsbi/z582PYsGGYOHFiklqXkAEYZgZk+abc/Y69HjY3NsKZwXeZAXjj/Q2FRtoc3w47PwwX31xkSQ0GegbMs1W/gDLfnn+fvvh67Rqbt/gDH8RGRsLA0jLJvarbIC46Gq/atCUwASND/Hj0GFbdu8G6b1+1KHLUnUdsFxwZjIfBD1HbpjariZuQvPvyDo33K3r7jrY6ikJZCmk6JW/PEeAIcAQ4AhkcAW4A/sEGYFRUFMzMzLBv3z60atVKpso9evRAaGgoDh8+rKTeP378AP0nCikQGYwvW+ZGzNcy+PnmjVo/CaKL2TukFHYEyatPLHBcAJfCLmr1V9Voj+8ezLohUK2QFLAsgON/CQkXcT9/4vPevTCvXh0fFyzEl4sX2XWzKlXw7fZtFLl8CYY5ciR7bmnH776+eNVSjifdK7R3DzKVKZMi48cfpMuJLvAO8oZrdVe0KSrQ6KiSU36nMO7SOIVbNzvfhJmRmU7WxQflCHAEOAIcgfSLADcA/2ADMCAgAPny5YOHhweqV5cfmY4fPx6XLl3CzZs3lTTX1dUVM2bMULr+ZEpWmLc+gogu/dXW9tAGFdC/ijf0Y+Ow2bsaCpWvjWzdu6vdP35DKY+geE+khPm0YwcCZ80GjIxgUac2vrjLM5Gpba5pU5Gti+aZsBRPqG+maECF7j+A91OmKCzP/uIFGOVWn9dQXRCknIr2We1xsOXBBLtS7dx5t+Yp3Od1bdVFmrfjCHAEOAK/FwLcAOQGoEYGYEIewAqriyHK3AgrN8QhV0iMwq/E01YPV0rrYdjRWIXrehbmGDjOAs5+mdF68zN2LzEOwaR+ekQFQ5nA0izjk3+dhI2lDd6OGImI06cTHCLXpInI1kNO15LUXHQ/eN16BK1YgdzTp8OqYwdZl4CpUxG2T1KOztAQxe/fg56RkTrDatQm6FsQ6u8VjrmJOJtiKxOSlfdXYoP3Bm4AaoQwb8wR4AhwBH5PBLgB+AcbgMk5Ao7/MxAVqMTaEjDIZIBhR2Lg+FAghF7eQh+fLQBfGz3YvQdmbxMMQ48ZrVDj70Psc6F7NxG+dQc+LVvBvtufPwejvHmT/WtruK8hPnz9IOu/3mk9auSrgYAJExGm4khbbJhj9Ghk799P5byU0EFHxubVqkHf3ByxUVF407cfvt26xdqbOzqiwL+CYRUXG4vn9Rsg+oN8Dcb2drA7lnh1lORumGIo+50R1m1pZAmPzh4JDjXj+gzse7oPrexb4V7gPbQu0hp9y/RN7tS8H0eAI8AR4AhkYAS4AfgHG4Ckt5QEQpQvRP1CQkkgBQoUwNChQzVKAhENQOuwODh5xuJMBX20iw7HBiuBkNn4ZxxWrItBiCVguPEf2LaaBPz8CaJF+TB7Dr6cE45kC/xvE8xr1Ej2T6rjsY54GPJQ1n9urblobtccb4YOVTr2jT9J8cePlJIo6Ig11G0PPri6snXlHD8Or1q1VuhqXrMmCmzayK5FXLyItwMHsQxg/KqMQv1oX7qQA88O4G+Pv2VD3+16F8YGxiqnGnF+BM6/OY9p1aahfbH2ulgOH5MjwBHgCHAEMggC3AD8ww1AooGhpI/169czQ5BoYPbs2YMnT54gV65cSaqx1ANoaaKH3tm74m22b6j84gbMP/hgZC4hsaKsdSkEhgbAPntxrHJeg1f1GzIvWcFtW+HffwDiIiMFQ7FQIcDMDCvr9EXBknYY1bBokmuQNhh6biguvb0kuzSu0jh0KfiXUjk2VYPaHjwA0xIlZLcivbzY2mJ/VTihGybFiuGHr69Cd9NSpWC7fx+79mHmTHzeuQtWXbrArFpVfFz0D/LMcGXJJ7qQFfdW4F+ff2VDu7d1Ry5z1c+t24lu8AzyZDyLxLfIhSPAEeAIcAT+XAS4AfiHG4Ck+kQBIxJBOzg4YMWKFcwzqI6IClRxdTFcDvqAm0Umo17n8cDqangV+gwtbITjXK9czaHfeC7Io0ZUJa/atsP3Bw9g2dAJEWfdlaY6VNgR68u2ROl8mdG8bF4MqCNUFklKiAbm70NDkT8oDl6F9TDpRwM4RdoiZN161pWOeoOWLIGxrS3z0kW9fCkbMrOLC/Iu/kfmBXzVvgO+e3snNSU7sqajaxL/3n3w1cMDeebMRtY2CWfkJjmomg0mXpmI4y/lpeX2Nt+L4tmKq+zd6lArvAh7wbn/1MSWN+MIcAQ4Ar8zAtwA5AagVvotKtDeJe3QNuw0ruTsCsfBq4F5+YEf4dhvYY7MsbFomKUoMOCybK43AwbiyyW5py7HiOGMpiU64L2szdC6I/Eiqw37/mxOExgZ6Ce5VjIwn5QQqnucddBDQ08hHpEkW69e7AiXjptNy5ZF9Pv38OvcBSDS5l+S959/kKVZU/btVbv2+O7jozSnQfbsyDt3Dt70HyC7V/jkCWYIvnRpip/v3qHg9m0wq1SJGbwxcTEpWmrt/sf7yJ4pOyt31/NUT9wNvCtbhxjzqAoo533OeP/1PXY13YXS2UsniSVvwBHgCHAEOAK/LwLcAOQGoFbaLSrQ2Y3T4fRmGXzMq6PM4O3Aongeu6KNgc7ykmjxM2VtDx9GzOfP8O/ZU2E942sOhE8OexweUhPl8mdNcq3f7tzB667dVLaTGndiA6JxoQSRiLNC9qx5bUcU2CAkdIjePPpsmDePzDi1bNIYNkuXIvrzZzyrLo9XJDoYGo+EVfywzob2x9ojDnHY6bITpoamSa4/qQY+QT7ofKIzaza56mQQtYtfuB+M9I1YZY+ZNWay5A4ihr4WcA29S/eWGZ81d9VEeFQ4Drc8jMJZCyc1Fb/PEeAIcAQ4Ar8xAtwA5AagVuotKtCpwzvR6N5AYayaI4Bry4HcZYA6EwC3rkAeB2CA3OP3cekyhKwXjmX1M2dG0RvXoaevj/CTJ/Fu1GjZmvbZ18Gm0s0xtWkJ9HVM2mgJXLgIn/73P5V7KnLdA4ZWVkr3yGAkw5GEPIO2ewRD1b9ff3y9coV9zv/vBrwdNhxx37+jwJYtMK9ahXn3RG+jdFB9S0sUvXUTgd8CQVnJJBOrTESXEprzDMZf7JK7S7D5wWalPdTIWwMeAR7oWaonqJxe+W3lWZsOxTpgarWp7DNdi46NZlQxRBnDhSPAEeAIcAT+XAS4AcgNQK20X1Sgc7c8Uf94bcWxmi4B8lUANtQFLHIDY+XJE5+2bUfgnDmsfaZy5VDIbTf7/P3JE4Us20e1m2OMVW1MCbuF6IJ2yNPYCa3K51O55ujgYLxo3ASxX74o3TccMxBF+o1Q2S/i/AW8HTyY3SNPX5Hz5/Hl8mXZEW+W1q2Rd95cfLt7FzGhobBs0EA2TtCKlQhes0ZxXH19lHj0EA+CH6DT8U7sXinrUtjdTNhjfDnx8gSsTK0SrV8s9hl5YSTO+SuSWNO9URVHYendpSrHp3mLZi2KCtsrsPvXOl1DZuPMWj133pkjwBHgCHAEMjYC3ADkBqBWGiwq0L1nb+H53yj0MpSQLY96BOgbAouLAnr6wNQgwMCQzRd+6hTejRzFPmdu0Rz5Fi4U1hH2FqHjqiDIzwLR/gb46dQYk7/bYtHVtez2coe2WLbNFaZGBkrrDjt6DAHjFEudhZoBu+vo43w5PexrsR/FshVT6keevK9Xr+JNv/6MrLmYt5eCZ6/Q7l3I5OCgEifi/XtSspTCvZwTJ8C6Z09c8L+A4ReGy+6pKrt26tUpjLs8jh3hnml7hsX2JSbNDzZnR75SMdY3xnaX7ey4WZUMLz8c7Yq2g6ObI7t9v9v9FI1J1EqBeGeOAEeAI8ARSBMEuAHIDUCtFE9UIP/3wWi67Bw8TIbBQu87UH0o0GgOEBsDzMoBxMUAo58AmfOw+aj+7utuQtm37MOGIseQIcI67mwGjo1E6MtMeH/LCmZVq+KbpCRdUKYsiNl9BPWK5VRad/DatQhaLhBKi3KpoilWO0ezr71K98LoivLjZWk7Inf2LVuOXbI/547nDZxkt5Mip37Z+i/8ePyYHWUX2r0bxgULQM/AAHuf7sXM6zNl46x1WovX4a/R0q4lLIwt2HUpbc3YSmPRo1TC1Ugoxq/CNsGLJ5WsJllxpeMVtDzUEi/D5FnNYpsWdi0wxGEIGu1vBBMDE9zpKhx3p7Y8CgjHvJOPMa5RMZS1STqeM7XXx+fjCHAEOAJ/EgLcAOQGoFb6LlWgzlu8EBrwAo1K58W0Ls7ycReXACICgH4XhCNhAD8DAljFDBIp/170vr4wfLAXXwJM8Oaytcq1XV++F70bybNYIx88ZEbij+fPEXbwIEzLlJFl755wtsJ/FSPYOF1LdMWEKhMS3O/TqtUQExbGEkG+XhZi/0hUEURLB/nx6hWCli5D9oEDYFpSyEAmWeu1Fms84x0PkyFaqhdGVxIM0fp76iMoMoh9rpe/HlbUX4Fzr8/BOpM1HHI6sMSOQ88PYaP3RpTKXgpnX5+FoZ4h3Jq74X7gfex8shMDyg6AS2EXLLmzBJsfCvGB97rdw6U3lzDq4ijks8gHUwNTRgFjZWKFyx3l2dhaPXwNO9ecfx7vQgW+R/fRtWGf01LDEXhzjgBHgCPAEUgpBLgByA1ArXRJqkDnX0RgpJsnqhXOht39JcTH/9YH3t0FOu4EigsUKyThp8/AMLs1zCpWlF0LWeYI61BvfP9siFenlb181PBTXlvkMoyBdZ8+iA4OQvDKVQp7yDV5EgLnzhMMjaZ5sKGsYGAR+TGRIEfFRDHDytzIXKEfxQ9G+Sker2YfPAg5hsuPcTUBa9b1WdjzdI9Sl2JWxbCvxT6WwTvvlrBOEjLO1jdcLzvKpVi9FgdbIOR7iMIYdWzqYFUDxT1Tg4PPDmK6x3TW1qeHDx6HPFY6FiZj8FSbU5psI8XaFpoo5yu0NDHE9ckNYGEihARw4QhwBDgCHIHURYAbgNwA1ErjpArk+yka7dZdR/5smXBlfH35uLu7AE+OAU0XA5UTrj177Xkwim6rgBx6YYiNBnz35wHi9Ng4ntntoYc4lAt+keR6C+3dg48LF7GkDfe5zbEhTDA86Kj0fPvzGHNxDG59uIUjrY4gp5ncyPTr2AmRnp4K4xd/+IAd5yZHxNJr8fvWylcLVKKu3p56jCOQMnfJGIyKjVJouqLeCoUYQvHmDpcdKJujrNKSKMN38Z3FqJK7CuoVqIeQyBDU3VNXoV0RqyI40OJAcrajdR+pAUiD/derMuqqOMrXeiI+AEeAI8AR4AgkiQA3ALkBmKSSJNZAqkBfYo1QY/55GOrr4ensJtDXF4w3nJwI3FwrjwtUMeCbT9/gtPA0fE0FHsDY3OXw8t/3+PlV8BDNrNIT1T48hLP/7STXS0kcVGc4JjwckdbmmH5tuixzdpPzJvQ504eNMaHyBHQt2VU2HsUkUmyiKHlmz0LWtm3Z128/v2HH4x2geLqESq3FX1iX413gHeyN8jnLg8ibRaFKHdOrTWd8fmSAUvm27ie7szJtUqH1Lbi9QGm/F9pfSDJZhGEYF4tyW4W4RlEq5KyALU22JImhLhrYTz6B6Fg5Mfew+vYY46yclKOLufmYHAGOAEeAI6CIADcAuQGo1W9CqkCZzC1QZMpJNt7dqU6wtjARxr67BTg6HChcD+h+SOV87o8CMW/bYZwzGYdvyASzuiPxbt5ahL82g4G1NSK2HMCrFWtQ6oycTFrVQNK6vNL7ZGCREUaJICKP3lCHoRhQTl7Nw69TZ0TeFww144IFYXdaflS68v5KbPDeAEtjS3h08lALs0b7GiHgawD+1+h/2PJwC959eYfnoc9hbWrNuPkoPo88eeTRO/riKJbdXYbQH6FKnsD4k3l395aVq0tqIWW2lFFoktDxcVLjpMT9ktNP4VuUvOpK6/L5sLSD6uzqlJiPj8ER4AhwBDgCCSPADUBuAGr1+4ivQBVmncWnr1E4NdIRxXP/4pp7ewfY2ACwyAWMfapyvkP33+Hc3jVYabwKfqYlUKjDIsT82xwRbzLBNHsMTKfdwOczt/HB1VVl/ywtWyJzUxeY2NuzkmzxReTPy2aaDZ++f5LdvtrxKrKYZGHfpaXfKBPYKJ+cb7Dv6b64+eEma0dxekS8nJgQtUzF7RVZrCHF3FHsXXBkMDv21YMeRlYcyXj7nAs6Y3HdxbKhqF/ZrYrHu4PKDcKxl8fwJuKNLI5R3Yc27NwwXHx7Uda8aeGmmO84X93uKdYuOiYWRaeeBDkAHfJnheebUFS1zQa3AZJY0RSbjQ/EEeAIcAQ4AkkhwA1AbgAmpSOJ3o+vQM5LL+Fp4Bds71MVtYr84rT7Hg7Mzy+MM/ENYKpMQrzh8gvgzDT0NzyOb+V6wazlEuDoMOD+dtn832pvw+vBQhZvr4aT4Gj8Fb2PC7QvUa3ao+w81wQ9YzOuz8C+p/uU9lIocyGMrzwejjaOEOlcqFGJJ48V2vY70w833t9g15oVboZ5jvLkDVUABX0LQv299Zmxd7vrbUa/QsYdxeSRAUpHsfc+3kO3kt3Y/FKRZgbT9dtdbiPgSwDLAKZqIiKFjDoPLuxHGKv/u/zeclx9dzXV6wA/C4zAzxgqhheHpiuugpI//u1RCR033EBBazNcGldPnW3wNhwBjgBHgCOQwghwA5AbgFqpVHwF6vzvDXi8CMGyDg6KFTsW2gHfgoEBl4E8inFptIA6iy7ANfxv1DPwApotAyr1AmJjgZmKpdvuf22MUV+d4JdZ8PKdPDSW/f9UwSqoumYxatipJlIWj3CpLRll7Yu1h5uv/Dh5W5NtsDlwE0HLlsHY1hZ2J08o4OJywIV54Egc8zlijZMyvYvY4UvUF1x5dwXjL49H4SyFcbjVYdlYQ84NweW3chqWKVWnoGPxjgpzScmeK+euzI6QtZUfMT/w8dtH5Lf8ZYhrO6Aa/X/GxII8whHfozGgdmGsv/wSjkWyY27rMnBceIGNMLy+PXrWtEU2c2M1RuRNOAIcAY4ARyClEOAGIDcAtdKl+Ao0fNd9HPEKUK7du9EJeHsbKNII6LgDMDCSzXvH7xParruOk8YTUEL/DdB1P2D/i4jZVTielcqQqOE4HluNXZp68z/UfP8AQ+uOQuPWtTGuUXGV+6EEjvm3hKNPyoTd6bITlXdUlrWl2MBRZYYyahrzalVhmCOH7B4ZT9V2VEN0nEAoXS5HOVZ5Q5XExMaw+r8it5+LrQsW1JYnchCn37Rr02Rd9zXfp1SdpMOxDngU8oi1aVyoMRbVWaTVM0qrzs8/RsBpiSLn4PAGRUDJHxQPSJ5BknrFcmBzrypptUw+L0eAI8AR+CMR4AYgNwC1Uvz4CjTz6CP879or5vGZ5FJCPvbBgYDXLuF7/WlAbcFzRzLloA923PTHfZP+sNL7Agy+AeT81ZeOgA//qhLyq71bdF1MiO7PvhnExsDqRwSCM2XF9GYl0buWrcr9uL92Z0kXJFQWbXr16Qq8eVXzVMVG540q+z4MfoiOx+VeOtsstoxCRpXEp14h442MOFHix/h5dfeCPpXJk0jv071x+4OQjZwUebVWD0/HnU/6vMegHfcUZtnSuwrqFM0Bl+VX8Oh9uOye33w5P6SOl8WH5whwBDgCHAHi4g0PR5YsWRAWFobMmf/M+vB6cfRW5pIsBOIr0JqLz7HwlC/+qpAPS9pLMjyDfIHVEi8PGYGlWgPWduiw/jq8Xr3HE9NewhomvAYySUqFxfMCvojNgwZRi1kSQe4spjjsGcC6jW5YFORhUiUUC1drdy12a2KViSyWjh77ivsrsNFnI/Ka58XptpI6xpJBKHaQYgilCSQdinVgZdviH6n6fvJF26MCdQyJqoxdaWYuETbHl2o7q+Hrz6/s8ogKI9C3TMLcicl6aKnUabn7Myx1V0z68frbGVkyGWHsXi/su/uWrcTYQB9P5zTBrVefYGKoj3L5eZm4VHpEfBqOAEfgD0aAG4DcA6iV+sdXoD133mD8Pm/ULpoDW3vLDb57/p+x7fx9LPVrrTBf6PggOMw8i0J673HRZAxgZAZMDgD0fnEIUuvL/wDXVgBtNwE72iIahtjb+A46VRO8fX8ffoAt11+jby1bTG0mL8VG9z5GfEe/rXfRsXJ+vMZOXA+4jv8a/wcrUyG2UPTYSZM14gOy5O4SRh1DpdouvBFi10ha2bfCrJqzZN/P+5/HiAsjFLqrMvDWea3Das/VMkM0/nxzb87FrieCt1TVEbFWDywVOp/weY/wyJ+49DQIJx98kM1om90cF8YKxNSUBdx14018+RHNeCOvTayPqnPPsXs+rs6wNJWHCKTCkvkUHAGOAEfgj0OAG4DcANRK6eMr0IUnH9Hrv9somSczToxwlI0tVoHwM+2sMF9/2zM48zgYFfV8sd9kBmBlC4xQJERmHSghBHHAnNxATBQwwhuwKshurb7wHItO+6J9JRssbKuYYDLn+CP8e+UVa6fqmJG8gNV3VWcet8MtDyOfZT7s8d2D3Oa5GeUKydhLY3Ha7zQGlxuMNV7y5I/4x8aD3AexTFtRpladig7FOyjhS9QwL0JfgErC6UkN3V8tQ7+H4k7gHdTNXxeG+hmrVFrE958o43qG7YQMOyJ+7lWzENwfB8K1eSk0KJFLhkdsbByqzTuHjxE/ZEkidNPc2AD9a9uxLPK1F1+weNJC2RXL9mmltLwzR4AjwBHgCPAjYEoK5UfAyf8lxDcAfd6Gofmqq8hpaYJbU5wQ8uUHDA30UXRfopYAACAASURBVG6GYBQ8N+kKQz0y5gSp+H0t+hmeQHE9f9SlDOB8lYB+gidIpaysBIQ8A7odAuwECpFtN15j2qEHaFQqF9Z3q8SOdkXDavrhB9h6/TVr92KuCwzE6iSSwdsfbY/Hnx5jZf2V7P9rPAUj7+RfJ2FjaYPOxzvDJ9gHS+sulcUR0n2ikGlbtC2rEtKlZBe0PtyaZdqKoglhc/KfQOr0jIyKAR3vtyqfD3Y5LBKc9PLTIHT/3y2F+3emOiG7SAoer6cY/5nULsY1KoYh9eyTasbvcwQ4AhwBjoCaCHAPIDcA1VQV1c3iK9CHsO/Mq0OG1rUJ9UG8gET+S0d9JA56zzHecDdqGAhZroFxWZFLL1Q+eNHGQOdEqn24dQUeH1VIJDns+Q4jdnuiemFrLG5fDn+t8WDewHaV8svoRmiCK+PrIX82M6WNiB6+EtlKMANQFKJfIRqWOm51GHffnmZ74BHggQPPDsA/wj9R3EwNTBn/3+8iopeV9lM6X2bsHVADmYzlNZLJ6H7+8QtOPfiAxWflcX85LE1we8qvjG4VYNAxcY94BmNCmL2a56J2BZTfBXe+D44AR4AjoCsEuAHIDUCtdCu+ApEh0HDpZWYMJCZXTYbDRi9YuYlDF6BVwhx7uPUvcGIsUMgRqDEceHgQHsUmovPWB8iXNRNcyuSWHfk2LpUbpx7KY9BWdS6PZmWVq4SsuLcC//r8q7SWxXUWI4dZDlanl0SsGhIVE8WqfCQk5kbmmF1zNpwKJmz4aAV6GnSedMAHu27JjV63/tVQtbC1bCUU9zc4XsYv3YwfCxp/6VHRQoUQUYwM9NCgeC6F5ybeezCjESxMDOEX/BW7bvujXrGcqCZZQxrAwqfkCHAEOAIZFgFuAHIDUCvlVaVA/5z2xaoLzxMd97jxJJTSF45mFaTGMMB5dsJ9Ax8Ca2sAplmA72GsXbRDN5S52wyRP2NQpVA23PITSr1R0sGrYCGblkQpM/nXdSqzNunKJKU5KYZv9k35WqRHulJi6Pgd1T36pRg4CgFUFQeo1UPRQWc6YqejdlEWtCmDDpULyL533HAdN17KS+yJN4joebRzsURXdN//M1qvEeornx5ZG8VyW2L+ySdYd+mFQj9KFCEjf8C2Ozj9MJDd4/QxOnjYfEiOAEfgj0CAG4DcANRK0VUpkNttf0zYr0xvIk5Ex7MtvQahpsFD5bkr9gKaL0t4TT+/A3PzAHHyOEJqPL/Aeqx7apnoXuInpoiN6XiXjnlJqGQblXrb/2w/OhbriN2+u2VjSjN6vYO80eVEF5Xzqcr8jd+QqmQ0XXEFdES6o69Aap2eZciOezju8162xEF17TChsZx0e9IBb+y6JVRKkcqxYbVQOp8ymbe0TVjkT1mM6NPZTWBsqM8oYogqRiqHhtTE3jtvGGekKI9mNoKZccZKlEnPz5mvjSPAEfhzEOAGIDcAtdJ2VQrk8TwYnTfeZOMS8e9RrwAZ5xtVfWjpkA+WB7qggcF9+dzlOgtE0X3OAPmTqAqx3AH4LGT2ivK24F+o5Svn31O1KSszI9yf7qxyv2KJNqrckdciL+MGjC9Swy44Mhj19ghJKN/8BsKs0DpZc3UMQKqRS0flJERfM6phUZibpF9DRvTwVSiQFff8Q1HT3lrBcB2y8x6Oe8sNxL/K50P5AlnRrXohtfTL+20oM/yK5xbISKU6lNgA8Y+i1ZqMN+IIcAQ4AhwBngXMs4C1+xWoMgDp2LXePxfZwN6uzshsaoSLvh9haWqIigWzgTKF966dhplGW+STTw0CYqMBY+UkDaUVHhoCeCqXYrP9vh1xUKyqQX1Xd64AMlBIHs9srJC8II5NcX3E41cpdyVG+SKWjRPvUwawNKZPWtEjwnc6THK4wzibB6rmcMJGl6VJgur1JhQtV1+TtWtTwYYlsKRXoWSep4FfWB3fyQd9QMnUlNxhbWGCrz+iUepvRRLtI0NroqxN8gmdKTaw3frrjDSaMosTkx19q6Kmveoa0OkVz7Ra1/efMSw+NymvbFqtj8/LEeAIpB4C3APIPYBaaZsqBSLjaOqhB8hqZqSyNi/FvhF5c/Owbajitx7QNwKmq0gISWhlIS+AlRWU7p6zn4w+D0orXK9cyAp7BlRH6b9P42tUDM6PqYPCidCYUGfy7lFM4I33N9hYWU2y4krHK0rzHfD2wdh9d1Aoiy0sTOPw6PNtLG3RDs3Lqi5HJx1AFV0KEWdT0kRaCz0fOu6lSis5M5uCvpebeQYR36NxcoQjM6ZfBn1FniymODu6Dv5ac40Zh1K5OqEebKzUMObV2KzIIZlQ0/rFc+J/PeV1ndUY8o9t0m3TTVx5FoxtfarAsUja69of+yD4xjkC6QABbgByA1ArNdRagYKeCmXfLHJqto545eFY5xLNgQ7bsfDUE6y5KCQQtCiXFys6lUejpZfhGxgBMhY29aikVuIFxQYuvbsUHYt3RCnrUkrrE6lRWjrkReg3ofLForZlGf1MUkLH4sN2SY7AfxEgP5wprxuc1BjJuU/G3GGvd6hQwAoFrc2Zcfc1Klqh8sYWDz/8fUSIz+xUJT86Vi7AvJVE0Oz5tzOr4HHzlXLCB7XvUb0gM/z61S6cnOWp7NNy1VV4vRUSfuj5WZsb48yjQFDsIAkl/uwZWD3F5vvdBiKcyEgnby2V2yPpWq0AZrcq87ttle+HI8AR0AABrd/fGsyVXptyImgtnkyaKdC9bYC3m0AHc3GusINsdsDwe9h23Q/TDgsGzIDahTHJpQTG7PHC/ntC7dnlHR1YHKK2MmGfN9zuvMEop6J4EfQFR7yEmsSU+FDA2gyH7r9Dy3L5kMVMuazZjpuvMeXgA6UliEkQ2q4tof4H7r3F6D1esvq7g3fcxbnHH3FuTB2Zx67Oogt4HfJNaQiK39zcqwrj7SNjV5WcHVUbRXIlnoyj6d6I9oU8ypQx/U+7csiV2ZQNIU0U4bGACaMqNejFVkSXtKZLwlRGmj6jjNyejsXJM1rV1hpjGyWesZ6R98nXzhGIj0Cavb/T0aPgBqAWDyNdKJDPPmB/H2EXNUfCPe8g9N12l32d3qwketeyhViiTtzqf70qo24xDb2OAGJi4xAdGwsTQwN0/vcGPF6EYEn7crjvHyqjSSGi5OCIKHwI/45s5sa4OK4uTA0NWJKDKFRVY+EpX7RyyIuA0O8y6hpdx7ON2H0fhz0FQ5WIlW0nnWCfRzQowhJR6Pi+/KyzzKMZXwbWscPEJsXh+yECjZYJCSwklA386esPBEX8wNIODmp5V7VQOVlXenEXn3aKfe/naIspTRXrQKfEHL/DGK5HHuI/Dz+FrWS3MMaS9g4omssSubMIBvWfKiKRvPibyAi0TH/qs+L7TlkE0sX7O2W3pPFo3ADUGDJ5h3SjQBvqAgHCkWpk87UosVegHqGkhc5VBb66s48C0W/rHfaZ4tvcBmh2bEgGR4f11xEY/gPb+1aF05JLbCyKMbzz+hMz6BKSorkscGpEbej/KkU37+RjrL/0En1q2WJas5IYvccTB+69w5B6dirjJrV4RApd6diZjp9JKCmH4vpI6Kh33l9lFTCKP6f0ePt9WCTmHH+MVg754FRSXt83pdap7jh77rzB+H3eaj9PqlRin9OC/fcnCJVirDH/PH5EK9ImiXunij1UIvFPlj2332D8fm8GASU2ETUTF47An4BAunl/pyHY3ADUAvx0o0D7+wI+e4Wd1BiOxeiK0w8/wK1/dViZG8t2uMz9KZa5P2Mk0RfG1lV759eeB6PLL2qb+J1uTW4AEyMDdszs/lggKFYlNyY1kHlbRE+cWONWPBJ2LJId2/pUVXtdmjYcuO2uyiobNM7iduUwJh73nnT8g4NroHwBK02n1Gn7Jx/C0XjZFRaf6OPaSGZgq5pU/AOAPLF01P4niDp0On86mfbaiy+w4NQTpg77BlZHpULZ/gTV4HvkCHAaGE4Do92vIN0YgC8vAltbCpsp2wH4a4PKjT3/GAGnJZeR2dQQ3q6N1N68NLFE2kn0nNE1/5BvqL3oArvds0YhVoVEGitHpegotq5j5fxouuIqOyIWj3wfvAtDs5VXmSHjMbGByrhBtRebSENKBiAeP1VSsaAV7r7+rHTLtXlJBH+Jwhjnoql2vKvuXqNjYlHG9QyrAuM+ujbsc8rjD4lKRnrsPm6vF/beFeJAn8xqDFMjeS1jdefLaO32332rZNSTjlFGvCh/eo1l6RG5uklcGU0P+Ho5AqoQSDfv7zR8PNwDqAX46UqBTk8Brq8CcpUGBsk59qTbC/0WBYeZZ9kl39mNWSyfOiIe0Urb1qWkiJ6VZUYRVfeoNNudZafenSpw5Em9C2JfIkimmEE6fnvg2ojxElI2bpPlV1imMh1PU+aymOygzvrUbVNt7jlmeKqSTEYGzJCyy2GOyS4l2HE5ZfNOalJC3eHTpF3btR648/ozi8X8q4INW8P0ww+w+/YbHB5SEyXyZMa3qGg0XHIZ70Ij2X160betaCN7dhT7+DvEfr359A10zF3dzpp5o6Nj4pTKMjYonhPnnnyUPSsfV2eFLPA0eYhpOKnUK67rEIw03CafmiOghEC6en+n0fPhBqAWwKcrBYoIBBYXJacuMOEVkEn5uJJe9EWnnsTPmDiItWXV2T5Rn1x9rshVSBmpZERIhV7AlChSKLu57LLU8yRtWyCbGS6PF6qJkEiP64jqhOKRxJhBddaYVBsyUGnvcXGKLSm5Q1p3d3iDIhjdsCgzZMlTmt4No5lHH+F/114xr6tri1KM6FiMz5xChmztwjjp8x6Ddghk4FKpVNAKdjkscO5JIA4Oron82VKGuzCpZ6Gr+1XnurMY1fhClVuuPQ9hl9d0qYDBEixSkrNRV/vS5bhEcUTE7CRNy+ZhxPFS+RD2nWWhEwWRGE+sy/XwsTkCqYVAunp/p9am483DDUAtgE93CrSiPPDpJdDtIGBXX+XOqs87h/dh36FJTBsZFGRYrO1SQWZIuI+uo1YywXL3Z1jq/lRpLTXsrLGzn2Id4NnHHmHjVaHM3YnhjiiZVyiNlhJCxqnjQuGIWiqzWpXGtENySpqZLUuhu5ol3FJiXdqOQXQ7I908QWXqDgyuifNPAtH7PyHZZ6RTEfSoXohlNiclIs1NUu3S8/2ESLPpmZKHt3AOc1aZRyxDSHsh2qLYuDjc9vuM7tULwshAnq3+OuQrvN+GoVnZPOn+D4HkPhepV7xU3sw4PtxRNhR55qkiDYVGkMf++Zwmvy0OycWP90s+Au6PAnHtRTDoD1VDye8u+SNq1jPdvb81W36KtOYGoBYwpjsF+q8Z4HcFaLMJKKO6NnCnDTdw/WUI45SL78FLCIoyf59GxI9okNH3NDCC0aSo6w1QFYdF87SvZIOFbZXLv4l1dyk7mLKEtZH1l16AMmV39asGv5BvaL/+usJwlPhBFT3E2s10k2IVm5XNq820qdqXOBgbLL4EUyN9PJrRmPEDilmdZNAUy20p41wkPDf9MrDjLzK7hQnuTHVKcu1ffkTDzMggRb2zSU6qZoOEDMAN3SrCuVRuNgp5wUX6n/jDrutaEY1LC+1IyrieZpniGU0n1IQLFENabNop5rUnIc/73WkN2eePEd/htPgSwn9lytO1i2PrKnj31Z2Ht+MIxEeAdM5uskDDRV55lzJ5Uh2kdPf+TnUEeCUQrSBPdwq0uwvw5BjQdAlQ+Rc3YLwdikHf/WsXZrFuSYm01u2DGY1gYWKYVBeF+zdfhqDDBqGsnFTEDOD410WP4V/l82FJBweN5orfWDQI6Hi0im02haM/aksZoOHff6Ks6xlZVzIWKYYsowj9Q1py+ilGdUIvaCpjt+i0QMkjxluKeyEPjs+7MDz7+IXRx0iFGHqIEiWxI+/rL0IYaTDhObVZ+uIdJGPGfspJlY8tfm3mK8+C0G3TLaW2xPNIIQGiiPpDHsBV8Y5GM4p+iOskw3fWsccoksuCeTSpKgp52KvPOy/bCpGNP5/jwrx922+8Zke/UqHYXKouxIUjoC0Cd19/Qpu1wh/k0vhlbcfVpH+6e39rsvgUass9gFoAme4U6NBgwHMH0OBvwHG0yp2JlCvqHvm9DPqC+osvsQzd5JRqo8SDmvPlLxlxUfsH1QBl3v6fvauAlqpqoxuQEEnp7u4G6Q4bEUVCQUAFE+luJBQEBFEMlBB+SqS7u7u70wfS9a99z5yZM/fNzJuZO/PevMf51nLJmzn53TP3fveLvc3CsEBLG14hsfropZPeG18vlXyA09tI+rfOM/cYc8aLExtvlcho94CyeOXqfyJ3zB8j19d1Bbr9K6PWYO+5mwamIkPdZuBjzidZYeTckspPXcumrtU9Ft9UHbbSqO6m7O9bGwnj+fYyEOh9q+MRm1E1ZtTvCFVEXmdV2v9vl+EtVUWliLv/6DHydBdA2+SoJld1dJbtp2+g/pj1xhbypElsFFw1L58Vv607aWD/8fwzP3bxV5UMgOzxa46j/7wDTlt299IWnfUSXdZOA56c4yxSi4pwaaD1pLJBPRc7Fv74sDReypEy0NN4HC/knt+RunsxmTYALSg95A7Qwi7AxjFAha+AGr1d7mzlocv44LctyJs2MRZ+Wcllmx2nbxg5f/SakfXi3sMnRqh0Q5fqPmuLNy7Sr9GQfK1oBvSbu9/IHVz4RUWXNzLzg1z1Svg6uWoA5kqdGAPmH8CbxTIYjB1Ohs/xa0ZuY9OyWQxGkOgm3y05jJHLjnhctjlnU7KxqJ0mflgGFXK5vwkX77cE128/MLr8+WFpVMyVyuWcLBzoNWcvWlbMjlKRhCsnoYRcLYieTXq1VFEpE/OnS4L9F25CfSli/l/loSuNLvx+/heO3Ljodj64Xvm7d7V28klvPungty6cMamR++hKnhUIoVC6xhK+i2tqUyUHOtbJG0rL82st3yw46FR8x0EiG4g85J7ffmnSWidtAFrQX8gdoBWDgFXfACVbAK8Md7mzAxduGpArpGnbbsv3URsSP47Vsq4kEKC5DClTXnATSnaVo0W+4S9q5LIviQ/71Injh/PqqGtWqdLeKZkJqZPEx6jlR41E/76vFwy3vegMhcLwJ3EUD1685fK6DX6rEN4pJRhhpKgUYPIzSR3oahAWBOTsNh+2dDGDFk8Nl6p9CEPzx4ZTxkfHB9aLlHzBtUeuoskvm4w56cmbuPG0fUmuzi0fqrWGrza8X0yF+OKvnYZ3ZdnXAiB9/bGreO9nMR7THggXE+oV4Z5uZe5ycdmnfvEMBhOPK+n1an4DT1Jyd494pyjeKGadS9zTWvV3zhow848H4j4c1TpuO2m7ka6iSqB46r3dW8g9v71deADbaQPQgjJD7gBtGAMs6gIUfAto8KvLndGDQ08OxRUW4OjlRzBscfiq3XqF0mJM4xIWtOV9V3MyP0PBu3uJB/C+82EGkHTaJAmwsat7j+Slm/dQZuAy+6R1C6bFgr0Xg0435/0uA9uyzz/7jHCeFIJ0T9l8xviTrC9kf1GFRuO41ceNFwEW9rBvo9KZMah+oQjPDRt4Og9fTd2JWTuEQbHs68oG1EywZe7u8/h08g7Da016QnmG4saJhSMDXNO9kUklXZLnce/RY/tZkWDIZoOJLxGDGxQO9jaCNj6hjuh1cSXkwv7ehQc5/nOxMbttecSOFcvOf63SSwZtsXpgJw3IFA9+SEf28UEvR3sNSWQJdSPmNJVgbzLknt/B3rCL8bUBaEHpIXeAdkwC/m4D5KwJNJkudnYvDLhzHXhRVNSqWIBmDDR31FmsFu5UJ2+k8YTS+zJ+zQnDWJOJwr+8XxLrj10zQI2lYePpTfjQxVv2h5Z6ibvUzYuPlER/C5c/pLr+tPoYBs53POCnti5rL76JiO1CegNLZU2O/338kst9qWEoNmDVMUM2iRPEDde+5YStdlrAiMLKgVKiLFqolT8NfmpW0qA3IxA5z031fJ75ms1e5yKZkiF+nNhOYVGuMzp7Xph64a4CnIgAFOZFSmHeJEHa5fWtNXyVkYMmsSUDdd30OBFroGT/JQYbESUmpCNICkvzziWUVcQaCUyLkHt+B2ZbPo2iDUCf1OXcOOQO0IG5wNTGQIYSQKvlwP45wLSmYtFtNgGpRe5IpSErcPr6HfzYpDjqFEyHszfuoOGPG3A+TLBk1MiXBiMbFQVBhukx/KFxcSd8NAsq87lrtWErcdxWeGDuzKpWdwnRG49fw7suqo9jqgdDzWmTRs/8PRcM7Lu8aT3jKe4/fxP1Rq4x1EsoGELCmOXn1ceNHMqsKRIaQOIs7pncqozLxO1XR601qo0pQxoURsOSmXy+7r52kEUtEl6IRt2V/+4jdWLn4g93474zbgM2nXDkwblqF5Eh7euaI7P951N2YM6u8y6npMeUnlM1jG42drvP3mOE1T+vlhPtauWJzKXH+Ll4jyUGaoOSGZ1+T1O3nDYwGKdtdRQrmQH0o6NyJqw/iV5z9rlcuqtoRbD2GHLP72Bt1MO42gC0oPSQO0DndwI/VQYSpgQ6HgN6J3XsrlJHoFo34+9us/Zg0iaRI0VGEHOVLitvWSUbCkJKtiX7L7lcCnMYGcJ0Ja5y3NgupmK63bj9wGAAYdHFj019C9Wr+ZLUUauK2dDtZQfMi2oYEFqGYMrkef6mfiG8W9o5t5D9Sw1Yiiu3RFW1OX8zWGdqwLz9+HnNCXgLb2Reh5oaoX5Hw4iQKZRdvWoh6fPhPZ7B2lMgxv1n13kD34/5r8T/ZCUvQ7v/23rWqASmbOhSDemSPm9EB1gZTezIwhmTOU0vPaqScSYQa3tWx2CeNZmJZB70oAUHMG7VcUMd0vDmbzJfz4XhmIuSJ4yLHT1rRVvVqfcaniXeJ17KmcI4d6QIJRMNGWkiQ0Lu+R0ZmzbNoQ1AC0oPuQN0/xYwyGa4fbQGGKdULpZtC9QZaOxW9fiUy57CeDCo4gtNnAX1edXVnNumdlr+dWVkd5NfNmrZEXy7JHwu46SWZVA+Z+TCDXi10QA04oOFOW/+FCuY8y739altf0CpbC68adNQmLDhlFEEwmIQVcyUe0wfIG80Kdqav5Q1aAUhknLQClRJr7/3GvtShXBFH07YYoCfL/qykmEcRRdRK5nlmuX5n7L5NLrM3GN87E2hjqwaf6t4RnzbMDyAe3TRSVSvk78dojBsPXkdS9pVRvpkz0Oly+TvidEZevrUnE165QnVE50YWYgG8Pa49ahXMB262DBn+TLPl3rKuKYlUNsG0C7zhjvWyYM2VXJGymUKued3pOzaeRJtAFpQekgeINXrp+4tZw2gyQz7J+bKMn5ByixiMRGmJVTEFR6ZXNvMNi8Z+H6uRN5Us6RIiFPX7tibbOteAylchDhDZb9RtY4VBy+j+e9b7NNPaFEalXOngvrGTty4Hi/nN3AG+87dj+p5U+OXD0o5LdmM+0gYHwKwsHq43+sF0DTANHsMc9M7dfv+Y+MBaSXkzIczAbUHzDuAPzeeQplsL+Kv1mWNqnlWWEudRNU18nXeebsvoO1kZw5oifP37x3hMS6WOTl+blYywqHNOZYRdtANwMp5M5/5zjP/4o0f1hnaKZopGfiCMWj+ATsFpju18bdIrzsl1DA43a1ZNWylZ1MFGFfhmYYvOWwUIkXmC0ZIPr8j+XejDUALCg/JAzSuEnDBkcxt317STMBXDmT/TtN3Y+pWUSVKCVW2A1cPsXzpkoBwNr81L4WqeVK7vIKSUo4eKAn4myHZ80bIW4trDahgwb1fzW/A7BAPkjiDFHJB1y2Uzu5BJqD2lu41nMKizFl6a+x6I4/w1r2HhkEl5eVC6Yx80kCK2XPJ4pcy2a0xudAQJMUew6IM033w22asPHQFruB0ArmXQI/13eJDGLn8qNOwO3rURHJb2oQvHmOZUlE2O43icoFeaowbj7+D1n9sxTulMtlx+xbsuWDnUpcbZqHbxbD7mLHdGZTcrJCva+bGiGVHDNo+QvM0L2+NJjMyFP766LXYZcOTJMg80yfGrDhqnEmiFAyq76iqZ34q81Tp4VzfuZpHQPpArT0kn9+B2pyX42gD0EtFuWoWkgfo0X2gv2IUkRZuno0VpMtZIL4IYZnBg1d1qIIsKZyhQiyoJmBdGSpp8KODw5feCiYRrz161YnPmBWODGsRoJgPbuY10htFnsk2k4QXxJXHKmALjSEDMRl9/NoTSJkonr3yUG5tc7fqRlEFDaQqw1YanlUyZJApQwo9ctQ3GVfoPdx3/qb9OwnREihVsSI8f89FTsNFxGbiz9xdZu42Ks+/rJELX9aIHKBwYl32+HuvUXVb0k8wbdL2rTly1b5lpgcc6lfXrzD8ikOX0TwCAHl/dBsT+9Dzl93Gc8v9/e/jcuDL50suGJGY08d8S+ndc6eP6R+XQ6cZu3HsimDiMSM4hKIeKwxejrM37tqXRjxJvnRQPq2aE+1rO4qJyLxTbdgq457tC0+9lX2H5PPbyob86KsNQD+UJruE7AH6sSJwcTeQ52Wg0WRgWG7gv0tAtR5ApfbG8idvOo2us0QOEN+6iPAfN05sC9oITlcaGz+tPm7g2ElKOFYn/7ruhIFbx5yZet+vMW4clM+r5zJuLnl7LDDCjoSzKG3DA3y9aHp8/26x4Cw0hoyqVhOrWyI+IPUtRQK5dq2XF60r5TAgV+iVJYsEKcTo7aOoYK+sSF5uA1q2oq5dZ/7FJxO3IcnzccOBXwejUlfmQJq9Flb2EFFf+fB8Pm4cHOhXJ6Lm9u+J78iqeRocxfouwYPHDg+sJ/afiCYgxWDFIStA2i7SJSaIGyeiLs/s9+4QCFSFEHSdIc+wuw8NnT568tSgayQ2pyr93iiIJAmew+tFM2Dh3ov4eOI24+v+bxRExVwpjVxBf3J+g3lxWJCWMH4cFOi5yNiXK2GE4QOTF1O+fLJ9ZIS5Q/b5H1oFfwAAIABJREFUHcyLYxpbG4AWlB2yB+jiXuDMJqBIIyBeQmBpH2Dtd0DK3MCnIs9r+cFLaPG7SMaNbtACcu3ZU76A91/K6gQpwCIF/kcPFbHqDvStg2a/bjY8IZ5yBi0cgxjVVXp6zJta07EqMr2Y0P4xqefoRaZR3b5WHsM4oBTJmNQI+7Qonw0pEsXD0EWH7H0I6L2nd21L+jr/712XnhRWg/OhWM9meFqaxNSZcBydZuzBSzlSYHKrsoEcOtxYrDjuOH0XTip5q0cG1PX65az3nH1GjiZp7VYcEjljUsxeF182whexUgOWGXmWEjbGl/7PUluV59a8b3rBmpXNYhRF1B+zzh4iZTvmm45afgTrjoqiPBrx9PSpBp6ZQYO/s56vOir2o1rPfBEnzBjvzUcu/2csh3nA5JlWZVSjYni1SHqnz9R7z/hmJVEjv2f8Tqt7Ddnnt9WN+dBfG4A+KMvcNNocoNtXgaE5xPJrDwJKNse+Kw8MRg1KhZwpMbFlGQuaiNyuhA4g1AhR8T+rFp7FoMcr+Q3O4VypExmVdjfvPcTlm/dDqrglcjXm/WyuALRdVdYu3ncRrf8U3ghV6LG6+/CxEbpk/uVPa44beZoNx4kwvlUu2T82nETPv50xxIKRW6juSfIM80G2rJ37ynPvtey+pTmnkS3Nxrenecz9+XLHqlLKrx+URLW8/j9UZS4kx2I4f0Lz0gZYtBZnDQxddBA/rDjmUi1q5XyL37dg+cHL9nZL21UyWHOydZlvfGaGY+JnM7efNbjVVdnVsxaSJox8eCIWEhHvk88PGqk0/pr/ttkADJfC80emma8VkHG+mC/+sjIyp3C8UMr2pQcsxeVb9yEjC8E8W9Hm+R1EJcRIA/DkyZPo168fli9fjosXLyJ9+vRo0qQJunXrhnjxHLhxu3fvRtu2bbFlyxakSpUKn332GTp27Oi1uqPVAfo2L3DLxr1Y5D1cqzkCJfovNfbatGwWMNQQXYTeiGL9lhjQHCpOm3n9oVrYEsp6ZkiqSJ/F9iUyR2lr95pGmoAqp6/dQaWhwuvnSkY2KobXbG/4vF55ui80wpFWcpfczenqQRloHcuE9mDiSP53/xEK9nLOaeQ+prQqi3I5vCtsMRuAaljRKryT9C5K3X7XsAjqFw8NvNBAX28r4zHisNpWsWseR62EV6tk2W5371oGxmaP2XvBamG+lJtxJ5lfSG+7THlhv6jyyLKameuU56Bo38XGPVkVVi/zXiDvKaykL531RbcvDrIaODKoF6PV89vKgfTQN0YagAsXLsTUqVPRqFEj5MyZE3v37kWrVq3QtGlTDBs2zFAHL37u3LlRo0YNdOnSBXv27EGLFi0wYsQItG7d2it1R6sDJHmCubPYcfG0wxFk67Pe2GdkgfV6pVQvG73943psOXnDqTVzYtSk98jElPJy2SHfzEyLxqKbmi5CMeZEd/PGzA+llwYtM5hmrFDDubrmnHfAmwXRuEyWoOr2syk7QFDl7i/nQ8uK2YMyl/Q0mgf3BZhdNQBZpf3PZxXslIhW8yPNDA4aFDr8MTh+5T9U+3aV8cWQtwrj2NX/8OvaEwZ7DkX1wqoA0DJdxZt8viELD2LMSoeHMTLOv7rTuw8eY9Xhy/h4oiiuI1zSHx+WNl7yzMIoAIs6SCW5+cQNo/rX0x5ltTnHnPpRcKvNo9XzOyh3HCBGGoCudDV06FCMHTsWx4+LJFv+mx5BegilV7Bz586YPXs2Dh50TZpuHjdaHaAnT4A904C57YCHt4EGv6LQ/xLh1v1HmPtZBRTMoLCGBOmwBXLYdlN3YuaOc/YhyUpBBPlCvR3eq5+alrAXjgRy7pg+VpmBSw3gZgqLaAgH40oqDlmOM9dF8c27pTLhry0CVogPs3WdqjnhLb42ei122yAhVneo6jL8E5FeVeOGhhiLTSiRAdA8cP4BoxgpfdIEqJI3NZjELwshCM3BimfJ7OBpH0xfIG0dC2rMoNJm9pqMyZ83qijb1cxtFDdFJGbjnRAjHWrnxcpDlw1YHqu/cXq16N2Swkpv4tj5IvQwj1h62EgLUKvHfRkjlNuq11BijvK6/LjqOLaduo5RjYrbvV+SXpH7IV7pqg5Vvdoai6Bet2EJskNkG+LMUVXp6ejl+6RKDpfUm76ubdPxawaHOSknV3qpD6+U5qJRtHp++7vJCPo9MwZg9+7dQc/g1q2i8KFZs2aGF5AGn5QVK1agWrVquH79OpInDw8wfP/+ffA/KeyfKVMmhIWFIUkSz3yrQbp+vg+7uDuwfhRQtDHOVfkWF8PuokSWF30fJ4p7mPNsZJ5UoV6LDKOWQvgFUqNp8U0Du8/+a+T2EJTVU7UnvR3M7WlZITtKZk2OjtN3G+DRVfOmNqq2VXl55BonSBhfCxLocczbQ4SRmfPX5/UCqDpspWHYMC/PDLjr244jbk2YIeaVSqFx1vvVAkaiOvHe1h29imVfV0HapJ65h4mRSIw4Fsv8/WkFp4lpGI1YesT4LHXi+AYdI6uraVx/85YDM83dagklQoB3KRK2J+LdedfCnB6QKnF8bOlWw7vOgAEBwupm5nhRPL1ceD1oiDWUXtJ6hdJiTGPPlIyqsciw6LSPvfd4jVt1DKNXHMWte49QK38a/OQFmLe/quJvj+c/a8oXDFafXN0WOA1FeCHp4VS/KJQhKX75oKTXfNzse/LqbaOAj7nErAR25S1kRTpDzYUyOpwWBG7n513q5vW6KlobgM+IB/Do0aMoUaKEEf5lKJhSq1YtZMuWDePGjbOf2f3796NAgQLg//Plyxfu99K7d2/06dMn3OfRygA8tBCY8g6QpiDwiUCkj47CHzxzZaQcHVAXz8WJjZrfrbJXn0nWg+i4v5i2ZonLqO4rouIGVgV2n7UXw98pChpcxFHjw+Zgv7pGTiIrgslrGxnMLgv3XrCHvNQ9zPm0PF4bLX5HH1XOjk6182Lx/ktGbqqZp9rsodvTu5YB7Dt6+VE0K5cVQxcfMsLMTMloVSkb5u+5iPb/22XAffz5YcRFWjREOTeFrD4cM9CSq9t8p4e9L0U99HyqVeG+5DYGeh/BGk/msL1XJjMGvlnI4zQMi9b4brXRpmHJjBjSwDeKPUmrRuilOaaXiUDuT760cMy/25a3ex9ZdT94wUH7C7c6p7+sOSrzED3M9H6bqTuL91sCcndz/lcLpwfRBSTuoi/RLG0ARjMDkCHawYMHezzbBw4cQN68Dn7Sc+fOoXLlyqhSpQrGjx9v7+uPARgjPIDXTwAjiwJx4gNdzwNxngvkvSLSxlq07yI+slWhMiy3vkt1Y+4m4zcZINGUYIACR9oGY9hEr45aa3gVVYnIAJAh3xQvxMPvzUvj1dFrkTZJAmzsKq51ZIrZ+yXnZrXzgPkiFE1Yi3zpEmPIQgF9Y6a+u33/EQooRR6TW5XBjG3n7CwQsoJaQmCsP3YV7/28CcRPnPVJ+QgrPaWR/WOT4qhTUOAwBlpYfLDvXBjI3Xr7wWMkSxgXs9qUxwvx4oAeQU/5XR/9uRWL9gkDlfLDe8WNtI3oLITF4T2HnLYtKmSzFzt44+Gm8Z/DBhjNIjwW4/kiMmeU3uLN3WoYHlZ/ucDdzXv40i3UGi6MVAoreolfKD3YKrUbv1/2dWXDi8cQv79eeXMhE3NX9567aaA4PHryxCnNh1A5ZISSa4zonqLuUxuA0cwAvHLlCq5dExhJ7iR79uz2nL7z588bhl/ZsmXx+++/I3ZsB9CxPyFg85zR8gA9eQwMzAA8ugukygvU6g/kqunLfSck2l6+eQ8VhqwwbnoLvqgI0sNRCBC8YO9F49++eCdCYlMxeBH7zoehy8w9BhzPxZv3jJ164u01e8t++6CUwVVcMEMSzP2sYpRoShayqJPXyJcGSw8Io6ZU1uTYcfpfO/gtDdet3WvYjSIJpiz700iYv/cCjtvYHeTnK9pXMULo5qpnFhU0LJXJ5d75e5CA5/QsJk4QXFiQ2sNX49ClW05reb9cFvR53T2awMd/bsPCfeK3SQkGN3RkH4zus/dg4sbTxrQsOpPGv7fFQgytbj91A982LOIzuDaNz5I2JAe5b09nxB/dmOGeCCZOXmwZdlZxOesXz4DvGhb1ZxqnPmq+ML8gdM6Pq46BXtVGpTIbL4KqsGJY0pq6gqxyt6Bo+fy2rF3nAWJsDiA9f1WrVjVCvxMnTkScOM54VbII5NKlS4gbV9wsu3btipkzZ8bMIhD1uo95CbisYKn1dvbMBPiMBW04wmbwjTf+c45r227aTszcLopDJAF50BagB/ZZAyp922fVcuLrWg46KHWwy7fuofSAZfaP+GDrOEPkGDK8FBXSePxGO0jv9+8WxRd/7YxwGSrFInMrZbiYHenxS50kvkGpp4pMZ+DLTaHei5z4lF2d6YePn9jzslzlFka4SD8auIM68fTSRcae/Rcc1ID0Jn1VM3Ko9fzYolddGoxdj62nBBoBDXrm5VG8LdzxahI3jZibl7/XQtx76GB7CfR977d1J9DnH0fuq1xKs3JZ0Pf1ggYtpMQtDBQep5rvq9LHsap9WMMiBmcwhbzUG49fD6cdle/ak361ARjNPIDe/lho/NHzlyVLFkyYMMHJ+EubNq0xDPP28uTJY+QCdurUyYCKIQzM8OHDYyYMjKq8KY2AQwJs1JBe/wq49hgg6hu5NgBD84ISFqPv3P0ec9tYMfnWWAcHtNxJoLwM/miGOVuvjlqHpuWyGHl6LGi4dvtBuKHeLJYBBNSmsaPCfrAa94PfthgsCezHsLIrUc9tr7/3YsKGU/Zm8jtyZJNmq2imZLgQds8oiKGwOpmhyGCLvIbmeX55vySq53MNNk0sOO65doE0Rig4uuGPmvfKEG6xvotx854oOmNVs8T/Iyd5xVwOjuxgXQ9WA7MqWBUWX7StmhN1CopnnZQ5u84jbuxYqOuBLYd5t6Q+pHc+d5rERuETvZSJ4z/nlOunetpkyDaQ2H37z99EvZFrjFxf6plCY7BtlZwYvvQw3i6RER3r5DUIAcxiZnziC9KyA5dRKXdKJIznSHnSBmAMNQAZ7m3evLnL3xzfWKSoQNApU6Y0gKBpDHor0fYA/d0W2DHRsU2GgluvAuJ6rmD0Vi9R2U7lstUGYFReCfdzH7vyH6p/uwp8o2cVqSsWgy/+2oG/d54PNwiBjUmjFVXCh4nkzFaZMdT1MC+Qlb4Md/Z6NT+a2zhPZ+04i6+m7jKYE3KkesHJsEsYLw7uPHhsDKOeW3MIjt+RgaFo3yVGW+ZAsTKa8DIUq1h/3uqVD+Vf1h7HwPnOkFnuihnU5H4az3yI1y2YFmObeK6UJWf5v3cfoE2VnN4uLdLa0aCS3ihOKjl9aeD+2KSE19WoVhasRjzM4+zsWRPJEgrigwthd1Fu0HLj32bmEBYeSWie8WtPGG0KpE+CeZ9XRNNfNhnYqszVnLfbRiQAQAVEn7HtLMjQM6ZJCeM8BkIu3byHMjYOd1fjSQNUglGrbX5vXgpV8qS2fySN2DoFeN6K269LtH1+B0LBtjFibAg4gDpyO1S0PUD/fAFs+915Xx8uATJFTWgtkNeKD2hitrFy0grtVSDXpMdy1gBfwup+v8bIJSKX8PCGRZ0Sxs3FEmrvyOAI9fZ6qd5mtQ/BrtccuYJxq4+jefmshjeGVYss6GDeFvdM7xArfCmsFmZBBMGmaTCqHKksumBxhyrta+XGsMWHwy0zT5rEWPRVJW+XH5B2NGpZyFIgQxKMW3Xc2AvhXejhJESPZJCR+Y+s2uZDmDzkzCdb+KX79aqV/jIvMiCLDsAgKuCzebiprcuiTHbvmFusLmXH6RvoMH032lTJYXheWYVMLmjKjE/K2SG+5u4+j08ni9DppJZl7JW1t+49dCqqUNdDGCGZhsG0CyeIIQ/4oFb3xP7qC4Or8WQBkTmvlG3pvaQXXr6oqUUlrMxmLiEl2j6/A6Fg2xjaALSgzGh7gMLOAlPeBfK/DizvLzTw7hQgbz0L2tBdtQa81wA9Wx9N3GaQxJsT5s3FEnJUb6A1vF+B9ZYSHNo8EnP4CIrdffZeVMub2uDiPXrZwY9KaizC2tQfI5h4imVOZlTSuhIay73m7MMfShjY3crVanjru/NthEePn6DkgKUGPhv3w2IY9XoxZN3gxw3I9OLzmPRhWTuNoLtQqasiIOJLhorQ6yX5bavnTY1lCqfv4f51jXBlVMl7P2/E+mPXDCYSFg0xp67O96vtHL2SIYmMHkxL+GSSYPRwJykTxcPGLtWR04b/R8/94QF1g7693N0XGEV+rmRpu8pGVbBKT8gsJhngI4UeIWFYcPb2j86pJNLDHm2f3wHUvDYALSgzRhygSQ2BI4uAV0cCJd63oA3dVWvANw2ouHCSO5jVrIMXHrJDo6gPVys8wr6tzLvWkrWAtFWbTohk9BHvFMUbxTIYuWAqa4Y6Ig0EFsPIMK43oMFmkGdXK0wU/zns7VPbu8UHoZUMF6pDy4ctw4dtJ29HySzJDYovCX/izgsYduchivR1sPrQw9WkbBakD1CI0er2VRYPhlrbTNpuGF0tK2RD91fyWx3eUv+ef+81XhhaV8qOrvXy4QRhWWw5ohyYoffMLyY0PNTeSO40ibD4q8pQYZm29Qg+cgTz+2RqA+koiXtIUc8MAbEHLRBpCDXypcbSA5edtkRP4CyFMUoFL48Rz29vLqCHNtoAtKDAGHGAZrcBdk4CqvcEKn5tQRu6q9aAbxpQMcb4QGLo5t2fNtoHYUiToUVZ1R3VnhVXuyO8TY5UibDh2DUD55CVoMQ/O3XtNioPFYUZqqger9dHrzW8g5NalkX+9J6ZhFxBfpjHJlxG57oODFTfrob11qo3Ro4mDcAB8/bj5zUnjOT9oW8XAfe+62yY4Qld26lauMllnqj5i8iAuPGkCaaYMNePvLfMvZQ5qUQk4DXPny5JpOT+eVrj/7aeMcLCxTMnw8w25WHOI/X1SkuaOmkAEqKIIflgi1rgwherL6eKqvtB9QsZVIoUvjASXJwG4pX/7qPbLAc5gLo+wkcRS1AbgM5XTRuAFk5xjDAAF/cA1o8EyrYFiJN4ehNQujWQszqQUNOoWTgeumsEGmBoSiL4S95btQvZNL6skQuD5h8UGGC2m350UKwKzcL1kh+Z3oj+bxSy58UxbEoKrefjOUNUudsfwZdVbwax2CTzB5PvCcLribov2Hobv+a4nZ9ZzkWPZMK4cVD125UG3M2YxsVRr1A6SEicNEniY1NXZzo55ksSNHrLSQGvogqZKIpkShbsrbgc/9p/91H9u1VGbpn0TNHgpuEdSiLxI2moUv/0Vn675LBhJDE31Qwbo66drBosoGBhiBRZrf3dksMYtfwICLZcNhJyHBuO24DNNs/6rl617CDbhGB6vWiGcCr3lDfIopyPJ24z+kioohjx/LZ48LQBaEGBMeIArRsJLOkBFGoI7Jnm0MZzCYAGvwLZKgPxE7nX0qEFwL0woMi7FjSpuz6rGnDn6aE+gs1xGmydEybm7I27xjRDGxTG2yVdgzh7u449Z8OcQHDpCSG4NkWtNvZ2vEC3o+FRf+w6VM+bxg7MyzlovLOalyFqsvO8EP85XAy7h7KDlhnG8JH+dZ2KgNTiGvOLwbimJQzWjaiQ6dvO2gt35PyhyDfO/Mli/ZYY+Zh8MWAhEYXUacTAUCk05T4kwDNfsgho3m6aKFAiuHe7WnnAnDqOS09nsEHG5Zq+WXDQAICm0JMsPZCeaOZYQMYimPTJEhgV91JYmCSJA2QqSYx4flv8IWgD0IICY8QB2vUXMOsjIGNp4KyDSN6ulizlgZvngOq9gHyvArevAkls9E0P7gDfZAKePALq/wwUbujQ5vGVAL2LdQcDmcoK76IWrQGTBpjknafHAnvytvq1txy4oapU1SOh4gH6u96zN+6gwuAVRndCqVTMndJeSDLjk5dA7tSoFhoJpIPL1mVeuGvaqmI2dHtZ5MfRQ8okfybtky2FFcNS6o9Zh+2nBbadmvvFv1lccahfnSgJs6r0k1yLP/y9kXV9Gv64AZtPOoMkH+hbx/A2m6nWuKYNXaph7q4LeKd0JoNfmwZg1hQJ0aF21KUU8PczYukRvFI4HQpmSAqGtvedv2lgXXpDM6fukwakZPKZ3ba8gZ8ZI57fFg+UNgAtKDBGHCAaan+8DtDj90hQdLmVtIWAi3uAaj2ASu2Bs1uB8TZe1mJNgNd/EF1JN9dXCR/HiQc0/APIE/zKMQuXU3eNIg2UHrAUl204duoSorsHkHsZuewImCc4+r3idlgKf9VMY7lwn0VGCO9Q/zq4ff8xivcTeIChRnvoysjY37e2ExBvyf5LcPW/B0a1Jh/wUr78awdm2zAgaTQS6HqugkEXVZAwf+8858T+sq9PbcObGYrSbdYeTNokKOooqtfMfG2isno8mLrrMnM3pmw+g6p5UuG35qUhKeYkWHmMeH5bVKA2AC0oMEYcoCuHgB9c4P9V7Q6ssEHEmHUUPwnQ/jCwawow9yvxbd5XgHcniX+f2w78XNW5V7oiwAfzgP8uAwmSAS9EDk6Whcuru0aSBtRkb8KmEKaCbATta+cxCiy0ODRAirzYsWLZPWasDiaIdKmsoZWvO23LGXSeuRs2EgdjA2Zg9jfHrDPgYmReoNwl8//IFMLEfXo26SVkOFDi25nbR9b5YBi76ywRcpd0fZE1t6/zzN5xzl40oRY+cBxiAjIMzJSEtUeu4pu3CqFwxqjJq/R1X760pwfxf9vO4pVC6ZD8hXho/ttmrDh0BYPfKoR3SmXWHkDEUCYQXw6JlbYxwgBk/t43oqLKSVosAia8BjwWDAPhhMDR+2YDG21evywVgObzgIf3gAGuqaDsYyTJAHy5V4eFrRy+GNRX5dh9q3hGfNuwSAza3bO7FRZzkEt21PKjkFAiqjZkUUunOnnxSRVHIYVM/lfZJtiv0/TdRm4h4T6Yi8bwZGSGvWWRC4t5hr9TNKQvLHUvvcOpE8fH5m7OhTYyVB/Smwjw4jr8b5dhEEoWkRjx/LaoI+0BtKDAGHGA+Ho9MD3w0JmQHl8fAljgcWIVsG9WeC3VGwYwfHxwru27WEAZ5hKWAmZ8GLFWv9oPJA1fyRVxR90ipmmgzaRtmL/norEtMyh0TNvrs7YfUsZN23oG5XOkROYUCZ22T9aK75cdgcohe//RYwNihUJGlQq5Utr7qNh78sPIpHukV5oUdo3LZMaANwuF/KWUoV7y+O6JQnzIUFHU0EUH8cOKYwZn8x8tSmsPoPYAWjuaMcIApApGFgOum0BBe95weOjmfA5snyCUFTehMBYLvwtcOQBccFRaudQmeYavOPOFGu2azQGyV7Z2AXTvGKGBgxdvYsC8A0ay99slMnmV4B0jNv6Mb2L+ngsGgDILO/b2ro2neApSezFMRzHnBi7cewEfT3RmrYhMA1Ayv0iA5VC/fNIAjBsnFo4M0CxPRy7dQs3hq43LRvDu2I/uIWnSpAgLC0OSJJ5xOEP9Wvu7Pu0B9FdzMYlL8JdawJlNzproHeb4e8svwLx24u+SHwJbfxF5fE+fAPdvutdghhJA84XAsFzAPVHV5ySafs7C6dNdtQaitwZUcGsaVYSEGbtSwH5QtnSrYQD3Stl7LgyvjFrrtOljA+vZcRWDrQ1ZWEFsyi9r5A72dJbHN1fBWh4wBgxQtO9iAx5n8VeVkPb5p9oAfMpkAC1+aSDGeAAjMgDPbQN+tqH1v/8PMK0ZcDc8SKuTEos1BSq2A17MLvIC6SkknuDW34AtPzuaqoamX1dBd9Ia0BqIrhrI2XU+Hj15ivI5UxgQH3w4U1xRxIXdfWgHA5b7/a15KVTNE54j+Py/d42iEYI0v/hCvICoR+YsdquXD60qZQ/ImMEcRBuA4bVb47tVBi/35JZlUDB1PG0AagPQ/59gjDEAf6oKnFdCK+W/BGr2cShGLexosxFY0kvwB1OSZBSewFsO5Hikyge0dVB6OWl4wxhgURfHR51OAs9HPX6Z/6dA99Qa0BrwVwPrjl5F4/GbkCt1ItBou/3gsTFU+1q58Wm1XOGGLdl/Keg5lCJZKswNq3+7Eseu3Aaryn/9oJTx9Z8bTuLHVcfB4pJimX2/57T+Y6vBvDLgzYJoXCaLv1uOtH7lv1lugEATz29lBxMqQ6StIrQmavTTRmw4fg1kE8mVLA4KZEunQ8ChdYmiz2pijAE46W3giI14vdMpIEFSIFYs5wtBz13YWaBad2D1MAdETM4awJs/AWe3AFPeEX3iJwW6ODConAZiYckUhTWk6Wzg2DIgWRagdKvoc/H1SrUGtAYsa+Do5Vuo8d1qJEnwHO4+fGxQ41HcMZs0+3UzVh8WOYIUd2DhqveL+IPETpRVsS3KZ0PPVwUgtS+iGg+uqMh8GSsy2pJlZ9SyI/i0Wk7kTJ04MqYM+Tk+m7LDoLnrWi8vBs/ZiePfNtAGYMhftRBdYIwxAK8eFWHd8l8ARWxGnCedH5wH/PWeaME+NfuKf4+vKdhEijYB3rDBw5jHYSh4XCXHpynzAFcPib97XAPihCawaogeQb0srYForQFXYV1uaEiDwmjogjpPVnLKTWd+MSFWd3T2bpGnt9SApXa9sLKczA8NftxgfFa/eAZ819B3GJdqw1bi+NXbBhduuRwaxzQ6Hry+/+zHr+tO4OXC6fDPlmM4M6KhNgCj44UMhTXHGAPQV2VeOwaMKi56NfwTyP+a+DcxBbf/ARR5zz3QM1lCJjcEjjpu0Pbpv9gFJM/q62p0e60BrYFoqgGmoOfrudDw0KkytnFx1C1ko5xUvrh88x7e/Xkjrty8j1v3HyF2LOBAvzqI/1wce6spm0/bOZL5YaPSmVA624t2bljmG45vVsqoPmbhiTfCdRbotQh3HjxGVDGReLNO3cazBsasPIqpKHdMAAAgAElEQVQhCw+B2IgXr97QBqDOAfT/J/PMGoA04gakEyDR7Y8CiVL5rkTViJS9VWPS9xF1D60BrYFoqIE6I1bj4MVbTisnThvx2lzJo8fCWCw9cBkIeDzjk3IokcXBhPL5lB2Ys+s84sWJjQePn+CNoumRPVUifLfkcLjhlnxVCbnSuA6PMlRIbxFp/BLFf85egCI5daOhqp/5JROTsuP03YYenty/ow1AbQD6/5t4Zg1Aquzf08CjB0DKnP4pkMXng7MIr6EqxA0kC8nzMY+ayD9F6V5aAzFbA1/8tQN/27h/5U5ZpflSTgcItCsNEDNw4b6LdmYH2UYWgDDMN2/3BZTO+iIOX75lrzA2j7W2U1VkTO4MUs02ah5hhZwpsfboVSR9Pi529aoVsy9IDN7dikOX0fy3LdoAtF1jjQNo4bA/0wagBb3Zu/5SGzjjolo436vAOxMDMYMeQ2tAayDENSDDcuoyzSwgrrZAmrk+/+y3MzuwzZ0Hj4xQrUFw9GYhO3evJxV8XTM3PqvuXHHMcfL3tCEdKJ1JQzf+fVFVrCX6aUDFktQeQM0FbOkEawPQkvqAlYOBlQNdD6LxAS0qV3fXGogeGlh24BI+nLDVabFkakiW0DN+3/7zN1Fv5Bq8EC+O4ZV7Lk5s7Dh9A2+OWY+UieLjxybF7YUfnjRRu0AajGta0qnJqsNX8P6vm8N1+7tteRTJpKMT0eNkhV/lpZv3UGbgMuMLbQBqA9DSOdYGoCX1Acwl3DkJOLvVQTUnh+z1b3goGovT6e5aA1oDoaeBszfuoMLgFcbCPngpqwFbQgMuIiHPcO7uC8D/b+paHWmSJMDEjafQffZeVM6dCj1eyQ8C/0qplT8Nrt1+gG2nnEHsMyZ/Hms7CaD7J0+eYsKGk5i06bQBGGyWowPqGoamluipAeaP5uy2QBuAtsunQ8AWzrE2AC0oT+16aj3wW13nwbpeAOKFz8sJ0Ix6GK0BrYEQ0QArbLN1mW+sZnbb8gZki7dCuBfCvkje4I7Td2Ha1rP4pEoOtKmSA4V6C3xT5u7t6FHTMACXH7yEirlSYcHei+g3d79RCXy4f13j/z+sOIqhi2ywVKZFfFQpO7rUy+ft0nS7ENWAzO3UHkDtAbR0RLUBaEl9js6PHwF/NRIQMFvGC2aRrw8BidMGaAI9jNaA1kAoa2DXmX9x7fZ9VMubxqdl1v1+DQ5cuInfm5dClTypUWnICpy+fgeSIm7f+TCE3XmIvOmShKOEe/j4ieFBZL7gyEbFMGfnOWw9dcOpWISGJdlKWlTIhrja8+fTtQnVxtoAdFwZ7QG0cEq1AWhBee66fpNZVAa33QKkCn3C9SBoQA+pNaA14KUGmv6yCWuOXMWwt4uget7UKNZvidFzT+9aSJwgboSjlOi3xPAKuhJ6BI8NrBfhGLpB9NLA90uPYPjSw/ikXHp0fqO4BoKOXpcvdFarDcAgXIvhhYCw00DLZUBG58TsIMymh9Qa0BqIxhpoN3UnZu44h2wpX8Dgtwqj4bgNRv7g1u41vNqVKwxC2dFfyjivJtaNokwDzBml1zh9wqdI8WJybQBG2ZWI5hNrAzAIF3BseeDSXqDJTCBn9SBMoIfUGtAaiCkaGLTgAMatOu60ncIZk2LOpxW82qL0IKqNyS9cLW9qNCmbRYd9vdJi9Gykn986B9DSydUHyJL6XHf+tS5wej3w9u9AgTeDMIEeUmtAayCmaGDm9rNoN22X03aypkiIlR2c+YHd7ZdFIL+sPeH09fhmJVEjv2+5iDFFn8/SPvTzWxuAls67PkCW1Oe68x9vAMcFJAQ0FmAQFKyH1BqIORo4dPEWao9Y7bShl3KkwORWZb3a5L2HjzF6+VGMXnHU3n5jl+pImzSBV/11o+irAf381gagpdOrD5Al9bnuPOdzBybgF7tEZbAWrQGtAa0BFxpgPtcbP6zDnnNhaFI2swEJ07luPiMn0Bf5efVxDJh/wOhyYlA9xIoVy5fuum001IB+fmsD0NKx1QfIkvpcd759DRiaXXxXdwhQ5qMgTKKH1BrQGtAacNbA+qNXkTpJAuRMnUir5hnQgH5+awPQ0jHXB8iS+tx3Xj0MWN4PyP860PCPIE2ih9Ua0BrQGtAaeFY1oJ/f2gC0dPb1AbKkPvedJTNI4nTA1weDNIkeVmtAa0BrQGvgWdWAfn5rA9DS2dcHyJL63He+cx0Ykk1833gGsO03oN4wIEm6IE2oh9Ua0BrQGtAaeJY0oJ/f2gC0dN71AbKkPvedyc00IC3w6J6jTZ6XgUaTgzShHlZrQGtAa0Br4FnSgH5+awPQ0nnXB8iS+jx3HlkMuK4AvCbLAny5O4gT6qG1BrQGtAa0Bp4VDejntzYALZ11fYAsqc9z599fAU6ucbRJlBZofyiIE+qhtQa0BrQGYogGrhwGVg0GKnUAUueNIZsK7Db081sbgJZOlD5AltTnufPM1sDuqY42CZIBnU8FcUI9tNaA1oDWQAzRgKTUTJgS6HgshmwqsNvQz29tAFo6UfoAWVKf585LewNrhzvaxI4L9LgC3DwPJEgKxNdYXUHUvh5aa0BrIDproHcyAE/FDjSjkssrqZ/f2gC09BPXB8iS+jx33vwzML+9c5sGvwL0DGYsDbRYEMTJ9dBaA1oDWgPRWAODswJ3b2gD0MMl1M9vbQBa+oXrA2RJfZ47H5wH/PWe+za9/gU0XVMQL4AeWmtAayDaauD7osCNE2L5Pa4BcZ6LtlsJ1sL181sbgJbOlj5AltTnufP5HcBPVdy36XQKeJ5hDi1aA1oDWgPPoAYu7QPmtQeqdgGyVXJWwJhywOX94rMOx4AXUj6DCvK8Zf381gagpR+FPkCW1Oe588N7wIA07tu03QykyhPEBeihtQa0BrQGQlgDo0sBVw+LBZrz/IYXBMLOiO+KNQF2TATKfALU/SaENxS5S9PPb20AWjpx+gBZUl/EnUeXBq4eAup8Ayzs7Ny+ek+g4tcRj6FbaA1oDWgNxEQN9E7q2JXZAByYEXhwK/yuO50Enk8eE7Xh857081sbgD4fGrWDPkCW1Bdx59vXgKNLgUINgL4vhm/f6C8gT13X4xxbDhxeDNToBcR9PuK5dAutAa0BrYHopAF3BuDjh0A/NyHfNhuB1Pmi0y6Dtlb9/NYGoKXDpQ+QJfX51nnPdGDd90CSDMBhWwVw5pdcVwM/vCuo5Cg1+wHlP/dtLt1aa0BrQGsg1DXgzgC8uBf4sbzr1TedBeSoFuo7i5T16ee3NgAtHTR9gCypz7/Ox1cBf7zm6Fu5s0iCVoWev8lvi0+yVgQ+mOvfXLqX1oDWgNZAKGpg11RgVmvHyrpddEQ6xlUCLuxyvWpiqHY+HYo7ivQ16ee3NgAtHTp9gCypz//OG8c65wT2vAHEju0YT/0+XmJxw1O/939m3VNrQGtAayBqNXD1CDC6pPMavtgFJM8KqNEPd6us2h3YNxN4+Vsgy0ve7YVFedeOAGkKxhj4Lf381gagd4ffTSt9gCypz1rnDWOARTbP36dbgZS5HOPN7wBs/snxt/l7azPr3loDWgNaA1GngdXDgOX9nOdvsRjIXAYIOwcMzx9+be9Odo2r+t40IHdt4MBcURyS1U3oeM5nwPY/gJc+A2r1j7q9B3Bm/fzWBqCl46QPkCX1We/8c3Xg3FagwW9AwfqO8Sa+JYpHpNQfDxS2hYStz6pH0BrQGtAaiDoNzO8IbB4H5H0FuHUBOLcNeHsCQM/gzkkCAPqFVECRd4H1o4CiTYA3fgAWdQM2jHZed9m2QLk2wPAC4nNzNIWfPbgNDEzv6BdDgKX18/sZMADv37+PMmXKYNeuXdixYweKFi1qP8i7d+9G27ZtsWXLFqRKlQqfffYZOnbs6PUPWx8gr1UVnIZTmwIH5gD1hgGlWznmkDkwDIncOAnkeRloNDkwa7j/H7BpLFCwAfBitsCMqUfRGtAa0BqISANnNgO3rwB7Z4j/ag8ETm8U98BUeYErBx0jpMwDfLQaOLlWePWIhEAv39TGzrMUqA+UawuMry4+b3cQSJLOuc2p9cBvCtpCDMFg1c/vZ8AA/OKLL3DkyBEsWLDAyQDkxc+dOzdq1KiBLl26YM+ePWjRogVGjBiB1q2V5FoPP0p9gCK6YwX5exmWYE5L5Q6OySQNUvH3ge0TxOetVwLpi1lfkMpR3PM6EDuO9TH1CFoDWgNaAxFpQFb9Js0kQJ7r/wwcWwHscvFym6ks8OEi5xFvXwWG5hCfvTIcmPtV+BlbLAIyl3X+fOtvwNwvHZ+Rk73gWxGtNuS/18/vGG4A0uhr164dZsyYgQIFCjgZgGPHjkW3bt1w8eJFxIsXzzisnTt3xuzZs3HwoPImpQ3A0P0hL+4BrB8JMIxRZ6BjnUNyAHeuAs0XON5cCRpN8GirsqCz8ABSPtkApHGRb2N1Dt1fa0BrQGtA1cD9W8CgjM46aTITCDsL/OMC5ipPPaDRlPA6PLcdiBMXuHUJmOTCiKNRWbihc7+FXYGNPzg+q9EbqODCeIxmV0wbgDHYALx06RJKlChhGHQpU6ZEtmzZnAzAZs2agQeA30tZsWIFqlWrhuvXryN58ojR0vUBiuJf/JrvgGV9gKKNgTfGOBbTLxXw+AHw1T6AsDF/twFcvRH7s/yFXYCNtrkazwBy1fBnFN1Ha0BrQGvAew1cPQqMLuHc/qM1QOr8wMk1wJ9vOH9nvieaZyJMDFNlzFKxPVC9h/OnUxoBh+YDhJC5FwaU/gioN8T7tYdoS/38jqEG4NOnT1GvXj2UL18e3bt3x8mTJ8MZgLVq1TI+GzdunP147t+/3/AU8v/58oVHS2c+If+TwgOUKVMmhIWFIUmSJCF6zGPwsrb+KsIYao6fyiFM+JfLB4FfawmIBEIlWJXZbYGdE8Uor44ESrxvdUTdX2tAa0BrwLMG+qYEnjx0bqPSupnz+yKiyrx5HvjODSNIpjLAa6OBVLnFfD9VAc7vALJXBY6vAPK9BrzzZ7S/YtoAjGYGIEO0gwcP9njwDhw4gMWLF2PatGlYtWoV4sSJEzADsHfv3ujTp0+4+bUBGEX3gr0zgenNgSzlgebzxSL+uwwMIyRMLIA5etePizfn+EmALjZydCvL/asxcNAGLO0KhDqiscloQiG9nRatAa0BrYGINPD4EdAvhXOrukOBMqZc9UcPgGPLhJeu0Nue85PZtn8q9zMXeBN4+3fx/bf5gFvnRdh37XAgY2mg5ZKIVh3y32sDMJoZgFeuXMG1a9c8Hqzs2bOjYcOG+OeffxArVix728ePHxvGYOPGjTFhwgT4EwLWHsAQ+02T7/fPN4HUBYA268XiZKhEGnx3rgNDbNW63a8Az4l8T79lwqvAidWie/FmwGujvB9KzePRpOze60231Bp4ljXgylvXO8y6RlQqOfNoMmLy5IkwFJ88Ahr+AUxrBryQGmh/ONoDQmsDMJoZgN6e+NOnTxv5fVLOnz+P2rVrY/r06QYkTMaMGSGLQJgrGDduXKNp165dMXPmTF0E4q2io7rdpf3A2HJAfNIbnRI3JCY5/1wVSJIRaLcP4A2Mb89PnwBfHwIS2ziCfV07Q8s7/gTmt3f0zFkDaDLDu5H4Vr5qiAOH6/1/gGwucnC8G0230hrQGngWNEBP3cJOANNdpBRrAryuFGX4qwezAfjWL0Cs2CKqEisO0PMawMrhYTlFRIUpNd/lBx7cApovBLKU83fmkOinDcAYagCaT5erHECGbfPkyQPmAnbq1Al79+41YGCGDx+uYWBC4ufpxSJolA1MZzPuDgOJ0wA7JgJ/twXSFAI+WSsGkVXBn6wH0tgAT+Xw9BAmSBYxVZwcV10WE7DbbPBioRBr4hiqxBBAVe8UoFtpDWgN+KyB9aOBxd1Et3RFhOFHjD+rkQyOZzYAWVSSMjcwII2Yj5iAxBhc0BFIlEZ4/f73AbBvFhADKoG1AfgMG4A83yoQNCuFCQRNY9Bb0QfIW00FsZ3E/Ht/LpAqDzCqBHD/JlCtO1DJhg04ujRw9RDQbA6QvbJjMRd2i0q43HUAUiV54gte0hNY973zRmg40vPojbgKt7Q/AiRK7U1v3UZrQGvgWdTAlPeAQ/PEzn2JOHijK/M9iR4+VvoOSAc8vOM8QvYqQLO/gZWDgZUDgUB5Ib1ZZ5Da6Of3M2IABun8GGHmpEmT6irgYCnYm3GZA8hcwDfGCrR7vqEmTAF8uQeI94IYYfK7wOEFwiCkYUg5uU7Qxa39TvwtuTRdzXn7GjA0u+vVtF4lQFkZKinZ3HWbfbOB/7moFuaauY4yHwHpCnuzW91Ga0BrIBQ18PSpYOegl4685AzdBsJLJ2nfuOe6Q8S9IlCiUsPxJfi9qWJkVy+rElaGRWwzPgQylgJaKnSbgVpTJI6jn9/aALR03PQBsqS+wHSe3sJGizQIeHQXWNYXKPwOUP8nx/gbxgCLuoi/P9sOXDsKTDaBnb4+BihmokmSI5g5NAs1BPZME9/yRnh2i/g3cQeTmsBa+fnwQkDYaff7ZXiF4RZPHsjAaEuPojWgNeCvBmjk3b0BJHwRuPsvED+xo9J22wQByJwsM0CAZkKnFGkEvDzM39lEv1kfA7umBAd7j/nRRElIkcO5oMOVASijJ5cPAGNsTCGtVgAZilvbXxT21s9vbQBaOn76AFlSX2A6z20HbP0FqNwJYLUcCzXM8Cw3LwDf5RXzvfwdQPiYU7b8QLkK9q/aVfzFt3c8BZ6LL/6Wc/DffAtn9S/zYrb/4bwHd3Rzv9QCzmwSbWmA/lITuGOqZu94QjxYtGgNaA2EpgbkfeDV7wG+FOao5sDDG1MOuLxfrDtDSeDcVvHvnjf8e7E7uxUg1znhVyics8QHkaMX1QBMWxj4YB6QQMG5nfAacGKVYFYiw1I0Ff381gagpaOrD5Al9QWmMz1+a74Vb8gXdgpD681xQJF3ncdf0gtYNwLIUAI4ty383IXfBeqPA/iWP/EtQaL+zkQgdy1gzucOTuFe/4q3ZULBEBJGFb7557SRqqufSyDVcp8CtQcAfV4Enj527vvpNiAlq+20aA1oDRjV/DNbiWKDfKbfWVSpx5VnjHAsRqVsLlGMRkmWBfjXlhvcZhOQ2vby6WrdG34QaSBv/+Z44bx2DKBB+dhBOoC3JwAFTGwfwdKD3GeKnAC9fKrxxzlXDQVW9Bez1xsGlG4VrJUEddyb1y4hacq0z3QKV6ynpM3Q4pcGtAHol9oC22ndSGBJD1HIcWSJMKy+2A0kz+I8j8xdUT9NmFLctO9eF1VuZAq5cgj4yVYokrWi4NOkQUjDkt7DUh+KEdjuh9Lh99L9suNGLr+VQKoyZKI+SIi3deOk5xzEwGpMj6Y1ENoaYGjyh1IiVYNCeJJcNUWBQmQLXy5p8BD4+McK4Wdv9BcwxfSyqbYimDJBld2JvBcwBYX7o9E1pkz41izAYCFGZMjpTQKuii+rDGmbRQLwy88DgUkYGftS53j6FDeHFkXSTru1ARjZuo8p82kDMASupMy9IW4VjT/eQD9z4eG7/x8wqjjw3yWxaBmufXRfUCIxJMs8Fxp6KwaINqnyCeL0i7vF3wRCzf+6+DdzgQZnDa+AD5cAmUoDHJfYWbHjAOQm5traHQCSpAf+rC8Q+7NUENV257cD5b8AavYNAYWG+BJIeUVYjPrjgUylQnyxenl+aeD3VwS/rSoq3aNfg/rZSRpoaQsBF/f4PkjNfkD5z133U2krU+QCrh1xP7679BLfV2S9Bz2UvJdK6XoBiJfQ+riROcKhBbj5+ztI+s0tbQBGpt5j0lzaAAyBq7n/b4FOLyX/G0DDCa4XNq89sOVn8Z0M5fLf42sCZzdHvJkP5gNZy4t2dJz3SRa+T6OpwlsxrjJwPwxoMktQ0cWOC3S/JAxC0tXtnAQUbQL88Zojd6jbRVHJrMW9BuQDmWwEHTw8MLUOo6cGHtwR2J6upMdV8UIWWUJPZN/k3s9Wti2w0QTQXLo1UG+o6zGunwBGFvVu/PZHgUQeqNu8GyVwrZgi8/vLYrxPt4rK5+giOyYBf7fBzftPtQGoQ8D+n1ptAPqvu4D1PL5KGFFSKnUEqtmAU82TMFeHeUUMybCQQ8rEBsBRL7gtP98BvKjAwYwoBPxrqu5lTkyagsBvdcTotfoDi7sDL+YAPt8efttqODiU3vIDdoECPJCqr+gYegqwOnwajl5wpjfwfLp7SfJpwCA0vnoEGF3S9cCJ0wNf7AyfYhGEZRhD/nsGGFHQu9HLfCLuK7/Wcm6fqzbQ2IYYYB6JuX+/1/Nu/FA86z+UAa4cBJrOEgUx0UX6pgSePNQGIGNU2gD0/9RqA9B/3QWsp/kmzXyhQg18G35GS2DP/yLuY67ou3EKWNpbFJXIpG+GdQmtIKv3slcFjq8AclQHms4MP8f6UcJApBDlnwCrWsJr4OJe8eBXjYNQfCiG8rU7OB/4q5FYoQT9DbX1Hl0GTKzvflVttwCpcgsPPEXhew/4VtwZaMQSzVkTYDUsvfyUGn1EGgeLN64ccCzluQQAXxyZ+mGW3f8DZrb0vOykmYCq3YCitusW8E1aGHDS28CRxYHHJ7SwJK+6DsttpAJpD6A2AL06L+4aaQPQkvoC05kPgm+yOG7EhFkhrpUvMu9rYMv4iHu4MzgY0mXIVxp9rkYq+SHwig10Wv2ekDN/vA6cXg+89DlQq1/E63jWWpBHmXR+Tx467/xZNAAf3BZ8rf6kCpBPdu5XQodNZwM5qobeSdr2O/DPF87r4u9i11/A7csiT5cc2qzAf3gX+HCxA4sv0Lsh5RmB5VVRObxl/jG/l8gDhJxiRKJAfRFV4Muhu0rZtSOApb3Cr1pWEbMAg4D2oSqrhwHL+wF5XwHenRT1q2R+8MpBAuw/T1336xlbAbi0RxuA2gNo7cxqA9Ca/gLW+5fawJmNYjg1t8/bCZb1A9aYAFvTFRWwMhR69Sq19/zApCH6Y0XjxuJSPCWDS6BqT/mL3u4lprU7sxm4tNdhuKj7i+ycsKjW7eNHwMhiwuvFF504z/m2IhXQPH4SoMPRyAunertS9bfIQp/MZQB6wfiSROy5N38SUEtDbS95NJBcVap6O5+7dqq3VG3T9byDYej0RuDX2uJbVyDwa74DlvURxWQfrwmfv6iyfMg5iPdHIPudk4FctYBkmazuJHj9z2wBfqkBRGU+Ls80walJ5Sk5jD2F3f+7AnybxyjKu9lwFpIWqK6LQIJ3QmL2yNoADJHryzDwnM8EV+ZLn/q+KAklI3tWbC+qdM/v8M2oJKbXIhuY9MvfAvQsSlEriM0r5Jvr1MYCo7DVct/Xb6UHPZCsaE5sI4C3Mlag+nI9TNQm7tnwAu5HZRiuyfRAzRr64zDl4HsbZeBHqwXtmCd5/BCY104YSKRBJJwR6Q+l1Brg3+8lmJqa2RrYPRWo3guo2M4x08yPgN1/iX3kew0YV1F89/FagBW6gRTm9TK/VwoNCnryslZwzp3kSx89k7wOafKHXwHvSzTY6bl+bxqQ22YsypZ/NQYOznXu13I5kLFEIHcTvLHu3QS+sRmoUZFSoBbi1fkGWNhZ7DV9MYHyYBbe60gIYAPhv9lyC5JmyqMNwOCdkJg9sjYAY8j1VUM5zOVhyIlhHAlF4W2okUn24yoBD/4THhpW+N2+IpTk6YF9Ybd4oL2QSnhlIkuePLaFnzeI0JqscI6s+c3zsAKU3MyrbVWTqfM7KqTdrYkcpSy0eRZYVOgNJYsM5ZXhQMkWnq+UfLFgK3rKfqoK3Lnq6BOKfK6/1hXpEOZcXgnkztXX/1kUc1GCgY8nPXdSU2QWouHJCn5fcw4ZQmYomRBPzBFUhdeDEFAsXDu9AeB5pyETnSghbfl0xosrX2AjU+5cB4ZkEzPGSyTuuxR6jL/aG34lZFcZ7wDqv/nlSSRN/qI2ACPzmsWkubQBGEOupprszRBTkXeAC7sA4pGR6qjCl95vlDlaxg3pBWBUSQe2V5ezgjvUlahv0h2OAS+k9H4+Ky1VCJ3UBUSYig+5qJL5HYDNCoezt+so1RKgxzWmy/45wLSmYpfe7HnWJ8CuyaJ9+S8FEw7xMttsFEDLFHrNSTEWCmwbxM4ktiaxMVssFuFfKcTgcwXE3OBXoOBbgbvyMqypjmiF7WLlNyIvjZBPbygQMfReDckuQOg/WgOks3l2A7eTyBlJYjay2IXMSYTAiiy5tB8YWy78bLGfA3i/5f8lbBBfdhklIvyWTW62O4OkSZNqAzCyrldMm0cbgDHkivLm0NfGw9tiEZDZRnZOHDArb+NbfhEhOEJE1P3Gs7IkpAJzWfLa8LWCrV5yjR6Y45jFG69SsNbEcOXgbMCDW+5nqD0QCDsHpMojbuSSXzlRWsGSULMPQHYX6akh0O7sTwRh/UufBWvlkTfupp+ABR3EfO6qytXV2JLdnRbIAgMy3qgYlvSedDwe9fmA5NbmQ5rGxNeHgOdNOJuz2zg9wI198brSGCajTiBEgrSrY1mBZ5KFJMwp/miVY1QWjpE+jgU9zCv0p6gnEPu1OoYNU88+zJd7Iy9v8dgK4E839HhxXwCeTy5IAeImAGSetVxoqVa4WbGnNgA1DIz/vwBtAPqvu5DryRwfvlEWt3lYArFAGpAsCklTKGJDkg8+PgCZf1i9RyBm9zyG6oEguwm9gemLA61XBH9uVzOoeVek3KPhrAo9fHzQS1k+AFg9xMVIsQQt4Ht/AZt/Bua3F228DeNHze69m3VpHxEipyTPJjDx3AmN30EZgCePnFtkKiMqZ+l9suVCGQ3enQLk9RKTzrvVem7F3wbDqWpIVRapEKPztVHh+4edFV71R3fDf+epyCqi9XIt9/4VrcaWF9X8DCOGnQFYLMP8Nl9Dv3JOCVNFz2uXM44CEolfSlxRwsREV2FhUr8UjtWnLXN4dG4AACAASURBVCwiCZEhu6YCs1o7z0R9EoZLCr3dqfMBKn5oobcNyK2bd+5rA1AbgP6fVG0A+q873dOkAYkHSPgIEsMHWySdU5z4wiAgQHCCZEBnG4l9sOc3j39qgwDPpieHHioVH7Hcp4KXVBU+tBlac2kEAuhxDZj9sQPfsdsl4QmIzqJ6wGhQkFnGHTOGO4gRFlC88ydwdpvwpj2+D+yY6D5xPlj6mvyuqLJvu8nB8Tv9Q2DvdJHT6c5ja8rjclqemmbhi/d+xUBg1WDnnX6yXoTL6UWyWiD1XX7g5jmg+QIgy0tinq2/AXO/BDxVrAZL94EeV33R4thJMgJlPwl+gdG674ElPUXVdJXOwP1bolhHQh1xLRLuSDUAWy4DMpaEfn5rHEBLPwV9gCypT3dWNXBwHvDXe6KiMGtFIGEK5yrIQGvLPl9RoPl8YKANqLbTSfHQi2zZMx2Y8SGQpbxYDz2Ul/YBVw8Jjx5zKs1ybDnw55uuV/rFboAA35LijzluhNmRIOE0gFnkU/jd6GMYcq/csxQzM42qid9eBk6tFdW0a751JMibcwdvXRSwGOStpvGfIGlwrjwT9nmu6EkjVh6rMSmNZwC5agCkRRv7ksj/8wTmfvsaMFRh41FXyxcHvkDQKNjyK1B3MFCssef97JwiXhTMEsjfwS+1RLqCigQgPdju8EGDcxWCN6pakMFZEqcDXhsN7J8tgKKDwRUsq6j5ssCXBsqJ1QIjUgrxGWkg9iP7h80b3vGEUTSmn9/aALT0g9AHyJL6dGdVA64Smr8+bN374E7LMt9KeiDs1XwrRM5cZIt8my/UEHjLxtcc0RrObQd+toEZ80G69RdHDwL2MsdRhvbkNzIU/McbgqGF9F1v/x7RTKHxPVkmLu93rCVuQpErlyCJ4zNWlG8cA+yaIj6jJ4swMIMyir/LfCwMI1VGFBZMNqT0IgQPwZiLvw8cXwkw71Id3x9NGN7dukC5tsKTqxpdxPpLmRP4qYpjZJVz2zwfXwwIFcNiK2LkbfrR0YIFLSwkkdX7ceIBX+13zaFLSBAyjsi26jzUK/Py/A37mtc8+R3g8EJBB0nvPv/P8DylWg+BMRrdxcyNzgIMaXCx+plV0L7KiTVCb0UaAWlNlHwqTqPqMWaO8HAFkoeoDjQA7S8c0+2FKvr5rQ1AX4+kU3t9gCypT3dWNeAuZ4vhCj7ADy0QN8Ln4gVGbxLqosh7wJtjgfE1gLNbgIZ/AvkVbuXAzOZ+FIb0WADCEBwNsipdRDjHGyETBL1GzNdiJev05o5ezJG7cSL8KKTzu7jL2eCI7PxAGikH/hH8qd7C1xAiZ2C68PthdS+LX6RIHD35twTLZr4Uwc5ZqckiGlUkxl7ZtsBGpVKVbUq3BurZYHncXZNN44BD8wHmbppZeEjh92N5R08WWREvUxYf1egt6BRV8YXN5/JBYIxSLWxeIw3Z10aGXznxEImL6EoCHZaV+nU11xtjgaLveXPaQ7+NGmZVV8uIxgcmvMOIdqNen+dfBDqZfssSQofj8CWi8NtiRIb++yoRjLJtBCsIvYKmvFn9/NYGYETH0OP3+gBZUp/ubNYAmUQu7nb+lCG7a0eFN8Yb6A9vtSoT7mX4ZGoTYZTUHQqUMSVWezumr+3MgLusiGRY09eKTt70Ge5UQz/u1tLhuMA+lIwt9FTQSAqUt8cbHUjd+wJkrWLTMSdyw2gxE/OtiHkm1/9zNZEHZXyXAWineAzdrW3fbOB/77v+NkVOUUnpTlTDlIw5zec5t5zeAtg7w31/9uG1U6XrBd9ChqNLAVcPO4/BFwnmiFLMBiW9VYOzAKQYlELsz/U2Q/HDpUAmG0yON9czojYLOgObxrpu5QogOqLxQvV7dwYgmVDa2pia1LUT/opg+QXrh6duk/iJsr35JW3a+yK8TGkyU7DDSGHqCMH9CRzOlyxS1bGojMwqjR2c7/r5rQ1ASz8lfYAsqU93NmtgbjtHGLNYE5GczwpilV4uUN6qWR+LMCE9MBW+AiQtFf/Nz9wJH2an1gEfzLMeGjRTYVnhFL19VcBqPH3ivPIPl4iQKOE4KKwKJJ6cWh3b5RwQP1HknUf1Qent9ZRV4lwlC1qY6zTZ5vWQqQJm7wfBvbNXjnhfty4B3+Z23Y5GefsjDmxKel1Z2UrD8MpB4bmVD2KGNj/f7jzO7LbAzokRr0Ft4a1OZJ+BGZ3hg7g2Xmfm1B5ZDFTtBlTu6Jjh6lFgtAm0mEbiwi5AylzhC458W3341hIL0PwNPfqsdnZXyGN13sjuz32uHy2YTx7dc569sSP0av+CuanLbKFhnmmG7CXsltkA7H7FOfrBQg9yW1NcscHI9BB6DxkCpgFuKibTz29tAFr6iegDZEl9urNZA8xf+bWOeNgSD9DIW4kF4KmjpT9cx640Pelt8XBkojahb1QPkzvQahXyQRqO5rEZ3rtyCHhlhGvoG3qMiHlGQ21QJuChDTib41gFxGVhB3OGJB2fyggwurQoKKFRNLmh8wNKFg9E1on01gCkp4r/8aEoMRtVUOLvi4ow9/tzgWwVgeX9HSwqnc94b6AbHrGs4fMlicfHB7kEW6aBSaPqMKtZKwhPowrJQsgUQp2oohqu6ufmFxsrBqCqTxrzNFpZdCANDBpabyq5girwu5y3++Xg4SCq10XOx3zFJh48o5F1FgM9DzFV+VLA/9Q8wHiJga5nnWdb0Mk5h1OmG1w57AAqlz0+3SqMcyky1cGdl5tpFgMJg/QQSJlH/PZ5TyrpSBPRz29tAFo6/voAWVKf7uxKA8yH442TIT3ykTJMqoonRhFPGr37rwBNJU4XcbBYKUkaKon/tv1PYI6NR5lUW4Ubhh+Nht0PpR2fs6qWxhw5ZV9I4Zx/QyYHJukTYqN0K1HdfHiRML4IisvQl9nr5Kvnx9V+VSaH7FWBZrYwkayKzV1XGDAUUu+Rqi8yaazMXjp3e6ZR9mttgB43AhHz2tHrp+Y7TWoIHFkkcu9IC/d9EVHMkSgN0N4UEo3o18YXD9KRSeH1IfMIvXdVuorq6VFeFAd1u+gMaky4F6lvOTarQvkwd1fB7es52D0NmPUR8MaPgsVHiqwsz/wS0MJ2zfmdyoDDv5NmBr7aE5GG/P9exW+Uo5i5jv0fPfR6ssCGKQoZSwIbx4r8UIr5urp6Oeh0CuD1lIDnL6QGbl8OH+ad0kiMazLqnJRBWk4yOklh1IJ8zjbRz29tAFr68egDZEl9unNEGnCVPO5Lgrw6vmQkMM/JEGmm0s7QHO6q9pjLxZwus9D4IIvIzfPAd/nEt+Ro3TJe5BUytNPjCjCvPbDFVuFLSIxpzZxH8vXB70p/5GOWFZbZKgGsBqbMaAXsmeboQeOPUBXMuXzvf0DuWhFdjcB8L4GBOVr8pEAXk4EvZ7HDs0DQ3DFXiqKG0mQuIZlmyn8udM+XBwIXu4LN8bQDNQ+wVCvg5WEOrzBDaDT0WR0ckRB+J3kW0Uot0GCl5uLu4nN6FBmm5QOaQoOVIVrukbA89cdFNEv47+lZNkONqJiBqodPMvTkqSd4v1mIYy6M8X0F7nsQ9maKDfdQtjIbyoGcL5TGknij0jvMgiG+WLw7EWCYl7nNqvDFg5zXLFhiAQ/vKUeXAK+OBEooeaqSgs4TZNCcz4HtExyjM5UhUWr73/r5rQ1ASz8VfYAsqU93jkgDki5KbaeCyUbUX/1+9TBgeb/wPVSDkg/4f74QXkJ6ncy8wMzXYVjNLDL5X4I58/vXxwALOjrw52jcseqS1X3uJBAGIMeWLBcqxIY5DJc6P5AkvViPDIP7ok9/26r0VQxVErDaFd3g6U3Ary6MUhuIrTH9tgnAP58LWjhWAjO30R/vn9yLDKVW7Q5U7uDwlGUoIeBVLu0VNG3m/C5VF5yfxh49yGpoloUVv9QQLWlwk51hhA3agxXc9ORwfIbrAlXpTkibITmAp4/FvJJfeNUQYMUAoFhT4HVbMY2/19OXflIflTsDVbv40jP6tmVu7tAcYv0NfnOu1He1KzK6MFzL/Geew5tnxYtH5U5A1a6OHtK75yq3ULYyU8WZ7i/6+a0NQEs/LH2ALKlPd/ZGA7wRMjmdKPfMBXx7AlDADf+lu/EIsjuyqOtvGXKRnKv0VIwuKYw2hunKfOTchzRZfEiTTYIwHvTisEKZVX6kkCOW4P2brudhkjfhQNjelRCuoY6tatMbvXhqQ8oweh6JDSiNCerx77aOXgwLErJkx5/hiwSszu+pv5k1wQZKG64Lw2AzW4Uf6dNtAjePIg1uhjBpyPzxGpAqr2DX8EcYPqeXlNhp9KaxmpIwOwSHJivG3esCV5CeOoaLaRjKimPzfG23OOdxdTgmrgm9coRlMXK0bLA21boDlWwcx/6s21MfNbe14FvC+yhDjxEVPAV6LX2ZJvEIUPnGAz1HqI3HcHD/VN6visVvfPE18pNHASxQWtEfKNoEeOMHEamg9573Kea/RqRL8ovz3LJavt0+p3Xo57c2AL0/mC5a6gNkSX26sy8aYLiUuUt1BgNlXTAXeBrr70+FoUOhYUfPnBRzUYkkTc9YCmi5VOT1MR/xyBJH1Sk9KUnSAXy7JxAzb8j0ttEb5atkqwzU6CW8jsGshjQzBNDDeWghsOoboERz4NURvq7cv/bmymcaVGkKhB9rxSCxNrO0P+oANlbZF5gMT7oxc76bf6sUvVxhD9Jg5XU/uRogbeHFPSKMR6NbDbHzgUvvjbtzxs+lR4zpA0wjCIYwp5YsEBR6Spl6QOYTvuREpueX8zOcSZ5aJQ8tGFsOuTEHpBMML66EXlh5b+L3vO/w5cBIzZgmgMmZ38koQ+mWImxMvnRWAMsXEle/HzkXX2JYbMKXjMxlnVagn9/aALT0W9EHyJL6dGdfNLC4h8Ap8waY1zzuz9WBc1uBjKUFH6lK3m4Ou8oiCnqVGk0BxlcX+IN86BNXK1NZMQbDljLnj96hiu0cFaie9pW+mBhD4qIVbAA0UBg8fNGJL21ZwTzXFt5mbhF5gWXIm+PUHgSUa+PLiP61/bM+cGyZoy9ZSMhG4u6aqZ8zIZ7MH2rIuHcy5yrxPC8DjSb7tzZXvb4r4DDkPGEmmvOtzGO5Cu+zCIRJ+sQZDCb94Mm1wO8vixUxH/XxAyBeIoDGbKDCzYHTeMwbyR0+IM89w8L7Zgqg+z3/E3mxTD2hcUdUABrw46uJ1Ib/LoXXjb9FcbTHb95E0qRJERYWhiRJFDadmHcF3O4o1tOnLDfT4o8G9AHyR2u6j18akCFMeszen+PbEKNKAteOCOw+eh8khAIf6D2vOY914xTwPb1x8YF8r4QH8VWx5fim3t+WVM0wIYF12e/xfceYGUoK41NKnW+EJ+YHG9BuIEO/vmlFeDUnNXD0ClQOoqd1yMruF7MLbxArbKt0cu6hFtPIb5gvyEIGs5fUHFJmCO11E5uHr3pR2xM0WybqewKW3vgjsNC0DzmOGYdPfk7IED7gaYwHU1TuYTkPPc4frwnmrHpsqQGzAUhvHA0+5u9JJhzeSwakdcbxpHFHuKhvMrvWJQHjCeHkp+jnt/YA+nl0RDd9gCypT3f2RQPSM8c34czlBPiut95AyfMrcfbIo8qiCKLk56rpvArCjvBGTJEQDGoL5nIRp1CKGYSX3jVZedd2swgPD8nmaE/IFeapDUwvPiMWGjHRokLUSlvOT/5XWT1L2BxWLroq0PB3raT7M3T7VIDSEirDlQdUVqmq87Bi+euD4Wfm+zuZMGjgUySzi79rNPdTsdpYMVvLRSER+9DDuna4YGSQ/Mz83F2IO1Dr82YcpjHwRYWYcFJMrBDeDKPb+KkBWbEru7t70ZK4lmyXMCXQ8ZjoMTSngGsyC6u4GaXwU/TzWxuAfh4d0U0fIEvq05190QC9a67ehAnjwqpMQq6wktIVt2z/NKKNCtHhae5BmYH7Ck2W2tacMygLQ2QbYgjGTyzCNazupDDUumqogHFgsj9zClcOFvk9tQcG1sjyRadsq3onpLFCvMMxZYFCDf2DJHG3hkv7gbHlRFEFMev+Isl9IcFkoMqsT4BdkwHJBsPv0hQEPlnnemSVFsufHFFPOlOrx8mj7I1BTI/hX41FEVH1nr5ekeC0J0bijZOOsSO7Ajg4u4oeo9IDO/dLAdJu/Obc3FtUQ1HmILO9ahiqO7ZIjamf39oAtPQD0gfIkvp0Z181MCwP8N9F517JsgjwX4qrYgY1TKtW/HqaW4aMXbUx37z/eAM4vsLR0hMsg6/7jYz2F3YD4yqKmd6ZCOR71RkzMJBhYQlAzOpZGsoEVn7ueeF5VA2rsRUE/d87k4CpjcXa6Ent4KaCWgXx/mofkDRj4DTHQhNyLOepKxLpvRWGdoNZ1OPtOmQ785nmi4gv+/F1Pt3eWQP0EK8bDjCFhbijrmT6h8De6eIbNSdXsviY+1iE09HPb20AWvqZ6gNkSX26s68a4IOY1azuhCwX7/3l/O1/V4BhNtiQntfDY/u5Gks16ojLxfyzxd1EpW+l9s49VHBnftN4BpArikK6vupTtpcPnpp9AYJgq/sPpAG4tLcIkxZtLIBtCYPCggTVM3v7mmBIIVzIl3sdWHkJkgGdbYa+eZ8MAxM4l0ai9Lr6q4uY2m92G2DnJMfuJH1eTN1vdNyXilagUhmar53cm0qL6Md+9fNbG4B+HBtHF32ALKlPd/ZVA2ZjS+aRyXGY09d0lvOokr7NFU+ru/nVG7HMG2QelavwHz1ExCk8uUZ4fBhG9ZWFwlc9BLr98gHA6iHCeHr1e0ANa3sb9vRmTQRqJmzKmz8JyrIfygJXDjize6z7XtD0kTrvo9XAseWiaOeNseHzNb2ZU7cRGrh8AGDBDPNX0xcH8tTRmgk1DUioK65LffHiSxH5vVk1PEWh+vMHE1XZs35+awPQ0k9AHyBL6tOdfdWAWvFZo7fIHyO7hhRir321V+TYSZGI+a7I2N3NP7ut4ICl9LjqfSjPnZHo6z4ju/3OKcDsj4GsFYEP5gJDcwn+UUqnk75DlNAoJmsKPX2ZbNXORiFCKuHZkx4/+cBjHmQ5G0j1yGKiOpgguMVNVHmRrRc9n9ZAZGpAMtsQEoi/O7OYebSbzgZyVPV7hfr5rQ1Avw8PO+oDZEl9urOvGmByPWE5KKTWogFIIyJpBkGdxHBim01A6ryOkX8oA1w5KCi8urvA0XK1hvWjHLytgQyB+rrfyGp/fgfwUxWARjJhJYZmd8z8+Q6AkC2+iEpyL/WnUmJ1vyLw5yQ9XZH3BLsHIXhkBbU/hqcva9RttQZCTQPMEyTfeJZyQDI30C9q0Za3RW1u9qmf39oAtPQT0AfIkvp0Z181QDq4MaQwyw7w7Vf19E14DTixykGaTiy50xsF6wchFGgwSm9URPMSCmbVYIAwC+4StiMaIzp9T88C2SGk109de8vl/2/vXKBtqvc9/qV9qcvxunkc17a3LRKGQyU9qTinlNE7qQ4q7JJ0yfVKpDw2mwqlZPS6dU6pvFJencojaqAhNzuPiKiLi5J7a5ebxx2/uVp7L7sdc6251lxrz/X5j2Ek6//8/L9r/r9r/uf8/aV650Q3muf+LH2zOlQmbAD3FISOwvvnf5EGbQt9tvbl0LFkJZOZ9WF7jp/f6HpAbggEk0A4jmb4MQoPo2T9xgB6kA93AD3Bo3BsBOyBf/tT8nm8WT1DkfTD24kWhmPTO8VtxPvt0Nh6n7qlSvIK9zSWt5pfvFra8WtoFzOANl/LJ0hLxki1mkn3fhSqfet7x2/hh9ss5dzS1AVHzyDgIwELHWWPWNg53h4TBhAD6ElCCMgTPgrHk8Db/xaKtxc+daFk9H07RSKjYjxbDFZdkQGPI0dm4VpadI5urCXfIt4wT3qja6gOOwWl6+zQ38NxAUvWHn4BJLpWyQ0BCERBgPUbAxiFXH6bFQF5wkfheBJYPCx0soSFMblkwG+DRqfDs3xeeIb5WR2dX5YKZodOW4klsPLfO0tbFod68+Buaf6AUGBnS3aQffvhob/baSPjs37ba+4AeplJykLAFQHWbwygK6H8XiYE5AkfheNJYMnY0HN7Fh2/RRfp+YhYfBiKk5Ne96o0t3con5nld/pLn7wgtRscOr3E0skCG+/7InTaxOpnQ9u7lvqtlyzMzGe/xmcc9t/FZ9/a1vDjTaX/3XV8/yKPwTp5z8kBAQjEQID1GwMYg2yKiyAgT/goHE8CK6dI/xgu/elWKesiad59Us6lkkXLt5MhqmXGs7Xg1XX0SOg5PWPX4BLp/VGh4MqnNw69RGPPHlmyc5i7vFr6kXvhbfdyp0jHjoTy37U49LavxUksbTv54DehrWB7+zfrQmnVs1LHfOLUBU9hjCjFCLB+YwA9SRIBecJH4XgSWPO8NP+B0FFmdjycbQe36S11HBfPVtKnro+nhoLPlpbO+LP011+PrAp/bkefjTr9t7ltDlY9E/r3OxZI2RelD0NGCoEUJsD6jQH0JE8E5AkfheNJ4D9fl+bkSpVqSZVrh86S7TRJOvfOeLaSPnVFbgmXHLXd4bPze//p1OJPbOt38p9OzGfQ9tLvHKYPVUYKgZQhwPqNAfQkRgTkCR+F40lg4zvS67cfX+Odi0JBVUnRE9i2THr5mt8vV/Is2ZL57Vxe2zoOJztT+aL7o+8HJSAAgYQQYP3GAHoSFgLyhI/C8STw5RLpleuOr5E7TrETtuDQY+tKh38qvQ57OeSyiC3i8Ba85TZzaKey/O2G4rL3rJTqNI+9P5SEAATiSoD1GwPoSVAIyBM+CseTwNdrjn/z1+om9Is3wl+tkF7qJOlYcT2N/iJtebf43ODwJ3N6h0K92BvDlz8UOtZtcovQpzWbSH1WeesLpSEAgbgSYP3GAHoSFALyhI/C8STwf4XS2D/+ajjOkq4YI53RPp4tpGddZuTKnyLNvls69D9S+4elv98o/aGuNGBjMZOnzpP2b5Zue1Nq/Bcp8uD6m/9Dalbi7mx60mTUEEgZAqzfGEBPYkRAnvBRON4EvtsmffGudO5dUkaFeNdOfUbAjqHKbxBicXZ3KbON1PI2aXy29PP3Up81Us3Goc+X5Em71kq3/I1TWFAPBFKMAOs3BtCTJBGQJ3wUhkDZJDDmj9IvhcV97zpHesWe9zsm/ftWqXLNsjkueg2BNCLA+o0B9CR3BOQJH4UhUDYJvN5V2jivuO+XDpWW5oX+f/j+k58YUjZHTa8hECgCrN8BNoDz58/Xo48+qs8++0ynnnqq2rVrp7lz5xYJeOfOnerdu7eWLFmiypUrq3v37srLy1NGRoZrkSMg16jICIHgECgZ9Nm2gu0kjwp/kB78JjjjZCQQCDAB1u+AGsBZs2apV69eGjt2rC6//HIdPnxYBQUF6ty5syPnI0eOqGXLlqpTp44mTJig3bt3q1u3bkVl3GoeAbklRT4IBIzA5oXSa11Cg/rXc6X/+kSqWl/qvz5gA2U4EAgmAdbvABpAM3vZ2dl65JFH1KNHj1KVu3DhQnXq1Em7du1S7dq1nTzTpk3T4MGDtW/fPlWo4O4BegQUzAsDo4KAKwL2ZvBnM4qz1mkh3fOhq6JkggAEkkuA9TuABnD16tVq06aNXnjhBU2ZMkV79uxx7vbZnb7mzUOBWEeMGKF58+Zp3bp1RQrcvn27cnJytHbtWrVq1cqVMhGQK0xkgkAwCWxeJL12S/HYGrSTukc8GxjMUTMqCASCAOt3AA3gjBkzdOutt6p+/fp6/PHHnbuBjz32mN5991198cUXqlGjhnJzc7Vjxw4tXry4SMiFhYWqVKmSFixYoI4dO5Yq8EOHDsn+hJMJKDMzUwcPHlSVKlUC8aVgEBCAgEsC+7dKT51TnPm8XOmqCS4Lkw0CEEgmAQxgGTKAQ4YM0fjx40+ol40bNzp38G6//XY9++yzjtGzZKatXr16Gj16tO6+++6YDeDIkSOdreWSCQOYzK8xbUMgSQRKvgwSDgKdpO7QLAQg4J4ABrAMGUB7Nu/bb7894ezaFu7KlSudFz8+/PBDXXzxxUX5bVu4Q4cOGjNmTMxbwNwBdP/lIicE0oLAyKqhYVrw7U5PpMWQGSQEgkAAA1iGDKBbwdmk1qpVS1OnTi16CeSXX35x7gCOGjXKufsXfgnE3v61vJamT5+ugQMHau/evapYsaKr5hCQK0xkgkBwCezfIn27VTqz9MdGgjtwRgaBsk2A9TuABtAk2a9fP82cOdN5ESQrK8t5AeTtt9/Wpk2bVL169aIwMHXr1lV+fr7zokjXrl3Vs2dPJ3SM24SA3JIiHwQgAAEIQCB1CLB+B9QA2h2/oUOH6pVXXtFPP/3kvBU8adIkNWvWrEh99hKIBYJeunSp8/KHBYIeN24cgaBT5/tJTyAAAQhAAAIJIYABDKgBTIhaSqkUAflFmnYgAAEIQAAC8SPA+o0B9KQmBOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CQ8BOQJH4UhAAEIQAACSSHA+o0B9CS8gwcPqlq1avr6669VpUoVT3VRGAIQgAAEIAABfwiYAczMzNT333+vqlWr+tNoirVS7tixY8dSrE9lpjvbtm1Tw4YNy0x/6SgEIAABCEAAAsUEvvzyS+Xk5KQlEgygh2m3Xw7Vq1fXzp07Y/oF0bp1a61ZsyamHlA2Omzwcs8r/Ms41jvbsbKOtZyNHc1RJwAAC1BJREFULFllk9l2ssbspd1k8SqLmk4Wq7LabrT9th28+vXr68CBA85OXjomDKCHWff6DEHTpk21YcOGmHpA2eiwwcs9r2TpuizOkVEti/1OVp+TxassajpZrMpqu9H226sm3F9RUzcnBtDD3HgV0NSpU9WnT5+YekDZ6LDByz2vZOm6LM6RUS2L/U5Wn5PFqyxqOlmsymq70fbbqybcX1FTNycG0MPcICAP8CiasgTQdcpODR2LkQCajhFcgIuhCd4C9iTvQ4cOKS8vT0OHDlXFihU91UVhCKQKAXSdKjNBP+JFAE3Hi2Rw6kETGMDgqJmRQAACEIAABCAAAZcE2AJ2CYpsEIAABCAAAQhAICgEMIBBmck0HEe5cuU0Z84cXXfddWk4eoYcVALoOqgzm77jQtOpOfcYwNScl7Ts1R133OFEZZ87d66r8XNRcYWJTEkmgK6TPAE0H3cCaDruSJNSIQYwKdhptDQCXFTQRRAJoOsgzmp6jwlNB2P+MYAnmMdoRR4MSSRvFJG8s7Oz1a9fP+dPOLVs2dLZ7h05cqTzT9wBjH6u0HT0zLyWQNdeCZ68PLo+OaN45kDT8aSZvLowgBjA5KmvRMtcVBI/FSyUiWdcsgV0nXjm6DrxjCNbQNP+8k5UaxhAlwZw0aJFGj16tAoKCnTKKafoggsu0OTJk9WwYUOnhq+++koNGjTQrFmz9OSTT2rVqlVq1KiRpk2b5uQlnZwAF5WTM/KaI5IxmvZK0115dO2Ok5dc6NoLvejLounomaViCQygSwNoxs62HFu0aKEffvhBI0aMcEzfunXrVL58+SID2KRJE02cONExf8OGDdOaNWu0detWZWRkpOL8p1SfuKgkfjoiGaPpxPO2FtB14jmj68Qz5g6gv4z9aA0D6NIAlsy2f/9+1axZU+vXr1fz5s2LDOBzzz2nHj16ONk3bNigZs2aaePGjTJjSDoxgciLeE5Ojvr27av+/fsXFTKWN998M88AehDSibbK0LQHsC6vI+g68Yy5VieG8e8ZQDSdeN6JagED6PLCvWXLFueun23t2kJ59OhR/fjjj5o/f76uuuqqIgO4evVqtW7d2qn1wIEDqlGjhpYtW6a2bdsmag4DU2+kOWnTpo3atWun/Px8Z3x2bmOdOnU0aNAgDKCHGY9kjKY9gIyiKLqOAlaMWdF1jOBiLIamYwSXYsUwgC4NoN3By8rKcgxI3bp1HQNod/7CgYjDzwB++umnsrdVLVlMu+rVq2vJkiW69NJLU2zqU687kRcVO1/5pZde0htvvKFq1ao55vu9997TgAEDMIAepi6SMZr2ADKKoug6ClgxZkXXMYKLsRiajhFcihXDALowgM8//7xOP/10LV++XJdccolTYsWKFc7fMYDxU3S3bt1UWFiomTNnOnf8cnNztXDhQlWtWlWjRo3SE088QRgYj7jDF2407RFkFMXRdRSwYsyKrmMEF2MxNB0juBQrhgF0YQBnz56tWrVqqWPHjnr44Ye1c+dODRkyxHnBAwMYP0VfeeWVOuOMM/TUU0/Fr1JqOo5AeKFE0/4JA10nnjW6TjzjyBbQtL+8E9UaBvAEZCN/5dj24/33369t27bpzDPP1JQpU5xtXQygd2nas5IrV67UTTfdpBkzZnC2r3ekv1sDmk4g3BJVo2v/WKNrf1ijaX84+9UKBvAEpPmV448Mr7/+euduavfu3Z1YixZuh5QYAmg6MVxLqxVd+8caXfvDGk37w9mvVjCApZDmV45f8qMdvwigab9I046fBNC1n7RpK2gEMIClzCi/coImc8aDptFAEAmg6yDOKmPyiwAG0C/StAMBCEAAAhCAAARShAAGMEUmgm5AAAIQgAAEIAABvwhgAP0iTTsQgAAEIAABCEAgRQikvQHMy8uTxUTbtGmTTjvtNF144YUaP368E+olnH7++WfnBAoLUXLo0CFdccUVevrpp1W7du2iPBYbsHfv3s6pH5UrV3beaLW6MzIyivIsXbpUDzzwgD7//HNlZmbqoYcecg6KJ0EgngT80vTu3bud78Unn3yirVu3OmGSJk2aFM+hUBcEHAJ+adrWgmeeeUbr1q1zrvV2/vjIkSOdaz4JAkEjkPYG0MIHdOnSxTm/9/Dhw3rwwQdVUFCgDRs2qFKlSs58m7GzM3/taDI7leK+++5T+fLlndh1lo4cOeIc/2Zn1U6YMEG2MFpcql69emns2LFOnu3btztHx91zzz3q2bOn3n//ffXr18+pl4tL0L5WyR2PX5q24w/tdJZzzjnH+a+d3YwBTO7cB7V1vzRt12Q76vOyyy5zjqB88cUXNXHiROcM+FatWgUVL+NKUwJpbwBLzvu+ffucUz+WLVumtm3b6uDBg6pZs6ZeffVVJ1CxJbtbeNZZZ+njjz/W+eef7xxX1qlTJ+3atavoruC0adM0ePBgWX0VKlRw/m5mz8xlOJnxtPOCFy1alKbyY9h+EEiUpiP7bkHR7UcQBtCPGaUNPzQdpmx3AW+55RbnPHISBIJEAANYYjZtK6tRo0Zav369c8fugw8+UPv27WXxpuwXYThlZWU5d/D69+/vXBjmzZvnbBuEk93xy8nJ0dq1a51fjmYmzz777OMWSPt1aXWYySRBIFEEEqVpDGCiZox6T0bAD01bH44ePars7GwNGjTI2fkhQSBIBDCAEbNpX/ZrrrnGuSu3YsUK5xO783fnnXc6z4NEpvPOO8/ZJrDnBXNzc7Vjxw4tXry4KEthYaGzhbxgwQLnDOHGjRs79QwdOrQoj3129dVXy/La84ckCMSbQCI1jQGM92xRnxsCfmna+pKfn69x48Y5uz62M0SCQJAIYAAjZtOe9bPtXDN/9erVwwAGSelpOpZEahoDmKaiSvKw/dK0/fi357jfeustdejQIcmjpnkIxJ8ABvBXpnZ7377oy5cvV4MGDYpIswUcf9FRoz8EEq1pDKA/80grxQT80rRFfLjrrrv05ptvOrs0JAgEkUDaG8Bjx46pb9++mjNnjixMiz3/F5nCL4G89tpruvHGG52PNm/erCZNmvzmJRB7+ze8TTB9+nQNHDhQe/fuVcWKFZ2XQGzL154tDKfbbrtN3333HS+BBPGblcQx+aVpDGASJznNmvZT03atN/NnJvDaa69NM9IMN50IpL0BvPfee53n/OzuX2TsPwv3En4uz7YczLxZGJgqVao4htHSRx995Pw3HAbGwgfYMyN79uxR165dnXAvJcPA9OnTx7m42J1Fi5tGGJh0+rr5M1a/NG2jCb/4ZFq374/96LG33ps2berPYGklLQj4pWlbCyyG6+TJk3XDDTcUsbW1wNYEEgSCRCDtDWC5cuVKnU97QzccpDkcCNp+GUYGgra4f+FkL4GYUbS7iPbyh11E7OHhkoGg7a1hizFozxgOHz6cQNBB+jalyFj81HRpbdkb8hYjkASBeBHwS9MWzshCgJVMdj23GwAkCASJQNobwCBNJmOBAAQgAAEIQAACbghgAN1QIg8EIAABCEAAAhAIEAEMYIAmk6FAAAIQgAAEIAABNwQwgG4okQcCEIAABCAAAQgEiAAGMECTyVAgAAEIQAACEICAGwIYQDeUyAMBCEAAAhCAAAQCRAADGKDJZCgQgAAEIAABCEDADQEMoBtK5IEABCAAAQhAAAIBIoABDNBkMhQIQAACEIAABCDghgAG0A0l8kAAAhCAAAQgAIEAEcAABmgyGQoEIAABCEAAAhBwQwAD6IYSeSAAAQhAAAIQgECACGAAAzSZDAUCEIAABCAAAQi4IYABdEOJPBCAAAQgAAEIQCBABDCAAZpMhgIBCEAAAhCAAATcEMAAuqFEHghAAAIQgAAEIBAgAv8PYIaTlehotF4AAAAASUVORK5CYII=" width="640">





    <Axes: >



# 导入数据


```python
df.to_csv('')
```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    Cell In[83], line 1
    ----> 1 df.to_csv('')
    

    File E:\pythonProject4\venv\lib\site-packages\pandas\core\generic.py:3772, in NDFrame.to_csv(self, path_or_buf, sep, na_rep, float_format, columns, header, index, index_label, mode, encoding, compression, quoting, quotechar, lineterminator, chunksize, date_format, doublequote, escapechar, decimal, errors, storage_options)
       3761 df = self if isinstance(self, ABCDataFrame) else self.to_frame()
       3763 formatter = DataFrameFormatter(
       3764     frame=df,
       3765     header=header,
       (...)
       3769     decimal=decimal,
       3770 )
    -> 3772 return DataFrameRenderer(formatter).to_csv(
       3773     path_or_buf,
       3774     lineterminator=lineterminator,
       3775     sep=sep,
       3776     encoding=encoding,
       3777     errors=errors,
       3778     compression=compression,
       3779     quoting=quoting,
       3780     columns=columns,
       3781     index_label=index_label,
       3782     mode=mode,
       3783     chunksize=chunksize,
       3784     quotechar=quotechar,
       3785     date_format=date_format,
       3786     doublequote=doublequote,
       3787     escapechar=escapechar,
       3788     storage_options=storage_options,
       3789 )
    

    File E:\pythonProject4\venv\lib\site-packages\pandas\io\formats\format.py:1186, in DataFrameRenderer.to_csv(self, path_or_buf, encoding, sep, columns, index_label, mode, compression, quoting, quotechar, lineterminator, chunksize, date_format, doublequote, escapechar, errors, storage_options)
       1165     created_buffer = False
       1167 csv_formatter = CSVFormatter(
       1168     path_or_buf=path_or_buf,
       1169     lineterminator=lineterminator,
       (...)
       1184     formatter=self.fmt,
       1185 )
    -> 1186 csv_formatter.save()
       1188 if created_buffer:
       1189     assert isinstance(path_or_buf, StringIO)
    

    File E:\pythonProject4\venv\lib\site-packages\pandas\io\formats\csvs.py:240, in CSVFormatter.save(self)
        236 """
        237 Create the writer & save.
        238 """
        239 # apply compression and byte/text conversion
    --> 240 with get_handle(
        241     self.filepath_or_buffer,
        242     self.mode,
        243     encoding=self.encoding,
        244     errors=self.errors,
        245     compression=self.compression,
        246     storage_options=self.storage_options,
        247 ) as handles:
        248     # Note: self.encoding is irrelevant here
        249     self.writer = csvlib.writer(
        250         handles.handle,
        251         lineterminator=self.lineterminator,
       (...)
        256         quotechar=self.quotechar,
        257     )
        259     self._save()
    

    File E:\pythonProject4\venv\lib\site-packages\pandas\io\common.py:859, in get_handle(path_or_buf, mode, encoding, compression, memory_map, is_text, errors, storage_options)
        854 elif isinstance(handle, str):
        855     # Check whether the filename is to be opened in binary mode.
        856     # Binary mode does not support 'encoding' and 'newline'.
        857     if ioargs.encoding and "b" not in ioargs.mode:
        858         # Encoding
    --> 859         handle = open(
        860             handle,
        861             ioargs.mode,
        862             encoding=ioargs.encoding,
        863             errors=errors,
        864             newline="",
        865         )
        866     else:
        867         # Binary mode
        868         handle = open(handle, ioargs.mode)
    

    FileNotFoundError: [Errno 2] No such file or directory: ''

