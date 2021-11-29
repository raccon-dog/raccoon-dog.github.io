---
layout : single
title : "Linear_regression 실습"
categories: Coding_Training
tag : [Python,MachineLearning]
author_profile: false
sidebar:
    nav: "docs"
---

# 예측 모델 실습

## auto-mpg.csv 데이터를 통해,  mpg (mile per gallern, 자동차 연비)  를 예측하는 모델을 만드세요.

컬럼 정보 :

MPG (miles per gallon),

cylinders,

engine displacement (cu. inches),

horsepower,

vehicle weight (lbs.),

time to accelerate from O to 60 mph (sec.),

model year (modulo 100),

origin of car (1. American, 2. European,3. Japanese).

Also provided are the car labels (types)

Missing data values are marked by series of question marks.


```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

```


```python
df = pd.read_csv('auto-mpg.csv')
```
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
      <th>mpg</th>
      <th>cyl</th>
      <th>displ</th>
      <th>hp</th>
      <th>weight</th>
      <th>accel</th>
      <th>yr</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>1</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>1</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>1</td>
      <td>ford torino</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>387</th>
      <td>27.0</td>
      <td>4</td>
      <td>140.0</td>
      <td>86</td>
      <td>2790</td>
      <td>15.6</td>
      <td>82</td>
      <td>1</td>
      <td>ford mustang gl</td>
    </tr>
    <tr>
      <th>388</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52</td>
      <td>2130</td>
      <td>24.6</td>
      <td>82</td>
      <td>2</td>
      <td>vw pickup</td>
    </tr>
    <tr>
      <th>389</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84</td>
      <td>2295</td>
      <td>11.6</td>
      <td>82</td>
      <td>1</td>
      <td>dodge rampage</td>
    </tr>
    <tr>
      <th>390</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79</td>
      <td>2625</td>
      <td>18.6</td>
      <td>82</td>
      <td>1</td>
      <td>ford ranger</td>
    </tr>
    <tr>
      <th>391</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82</td>
      <td>2720</td>
      <td>19.4</td>
      <td>82</td>
      <td>1</td>
      <td>chevy s-10</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 9 columns</p>
</div>


```python
df.drop('name',axis=1,inplace=True)
```


```python
# 데이터에 Nan 값 찾기.
df.isna().sum()
```




    mpg       0
    cyl       0
    displ     0
    hp        0
    weight    0
    accel     0
    yr        0
    origin    0
    dtype: int64




```python
# 데이터 X와 y로 나누기
```
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
      <th>mpg</th>
      <th>cyl</th>
      <th>displ</th>
      <th>hp</th>
      <th>weight</th>
      <th>accel</th>
      <th>yr</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>

```python
X = df.iloc[:,1:]
```


```python
y = df['mpg']
```


```python
# origin 은 카테고리컬 데이터이므로 갯수 확인 후 원핫 인코딩.
```


```python
sorted(X['origin'].unique())
```




    [1, 2, 3]




```python
X = pd.get_dummies(X,columns=['origin'])
```


```python
# 학습용과 테스트 용으로 분리
```


```python
from sklearn.model_selection import train_test_split
```


```python
X_train,X_test,y_train,y_test = train_test_split(X,y,test_size = 0.2,random_state=10)
```


```python
## 리니어 리그레이션으로 모델링
```


```python
from sklearn.linear_model import LinearRegression
```


```python
regressor = LinearRegression()
```


```python
# 인공지능 학습
```


```python
regressor.fit(X_train,y_train)
```




    LinearRegression()




```python
# 인공지능 테스트
```


```python
y_pred = regressor.predict(X_test)
```


```python
error = y_test - y_pred
```


```python
# MSE 구하기
(error**2).mean()
```




    12.782792965646852




```python
# 차트로 그리기
```


```python
plt.plot(y_test.values)
plt.plot(y_pred)
plt.legend(['Real','Pred'])

plt.show()
```


    
![12](/images/26.png)
    



```python
# 방정식의 계수
regressor.coef_
```




    array([-0.83960353,  0.03032018, -0.03061675, -0.00644172,  0.00434557,
            0.75847227, -1.83056491,  0.54183524,  1.28872967])




```python
# 방정식의 상수항
regressor.intercept_
```




    -12.3134923524076


