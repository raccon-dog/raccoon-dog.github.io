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


