---
layout : single
title : "파이썬 - MachineLearning"
categories: Coding_Class
tag : [Python,MachineLearning]
author_profile: false
toc : true
toc_sticky: true
sidebar:
    nav: "docs"
---
# 머신러닝으로 할 수 있는 것

- 편지봉투에 손으로 쓴 우편번호 숫자 자동 판별
- 의료 영상 이미지에 기반한, 종양 판단
- 의심되는 신용카드 거래 감지
- 블로그 글의 주제 분류
- 고객들을 취향이 비슷한 그룹으로 묶기

# 문제와 데이터 이해하기

- 가지고 이는 데이터가 내가 원하는 문제의 답을 가지고 있는가?
- 내 문제를 가장 잘 해결할 수 있는 머신러닝 방법은 무엇인가
- 문제를 풀기에 충분한 데이터를 모았는가?
- 머신러닝의 성과를 어떻게 측정할 것인가

## 용어 및 설명

레퍼런스 : https://www.youtube.com/watch?v=KDrys0OnVho

![12](/images/MachineLearning/1.png)



# 머신러닝 : Supervised , Unsupervised

![123](/images/MachineLearning/2.png)

# Supervised Learning

우리는 Iris꽃의 꽃잎의 길이와 넓이, 꽃받침의 길이와 넓이 데이터를 가지고 있다. 이 데이터들을 가지고, Iris 꽃 (붓꽃) 의 품종을 분류할 수 있는 분류기를 만든다.

따라서, 새로운 꽃잎의 길이와 넓이, 꽃받침의 길이와 넓이에 대한 데이터를 입력하면, 이 붓꽃이 어떤 품종인지 분석이 가능하다.

이렇게 분류할 수 있는 분류기(classifier) 를 만들기 위해서는 데이터가 필요하며, 

학습을 하기 위해서는, 데이터 뿐만 아니라, 품종이라는 결과를 학습 시키기 위해서, 데이터와 매핑된 품종 데이터도 함께 필요하다.

즉, 품종에 대한 데이터를 Lable 이라고 한다. 즉 이러한 레이블이 있는 데이터를 학습시키는 것이 지도학습이다.

### 레이블을 가지고 학습시키는 방법을 지도 학습 (Supervised Learning) 라고 한다. 

## Regression(회귀) 과 Classification(분류)

### Regression 

- 예 ) 어떤 사람의 교육수준, 나이, 주거지를 바탕으로 연간 소득을 예측하는 것
- 예 ) 옥수수 농장에서 전년도 수확량과 날씨, 고용 인원수 등으로 올해 수확량을 예측하는 것

### Classifiation
- 예) 웹사이트가 어떤 언어로 되어있는가
- 예) 사진을 보고, 고양이 인지 강아지 인지, 소인지 분류

## Training 과 Test

훈련이란, 데이터를 입력하고, 그 결과인 레이블이 나오도록 만드는 과정.

즉, 데이터와 레이블을 통해 학습을 시키는 과정

테스트란, 학습이 완료된 분류기에, 학습에 사용하지 않은 데이터를 넣어서, 정답을 맞추는지 확인하는 작업

![1243](/images/MachineLearning/3.png)

## Generalization (일반화)

모델이 처음 보는 데이터에 대해 정확하게 예측할 수 있으면 이를 훈련 세트에서 테스트 세트로 일반화되었다고 함.

## Overfiting (과대적합)  / Underfitting (과소적합)

오버핏팅이란 학습한 결과과, 학습에 사용된 데이터와 거의 일치하여, 새로운 데이터가 들어왔을 때, 예측이 틀려 버리는 상태

새로운 데이터에 일반화되기 어렵다.

언더핏팅은, 그 반대다.

![13243](/images/MachineLearning/4.png)

## 성능 측정

![12443](/images/MachineLearning/5.png)
# sklearn 설치

아나콘다에 설치되어 있으며, 만약 설치가 안되었으면 다음으로 설치함

$ conda install -c conda-forge scikit-learn


## import library


```python
# Data Preprocessing Template

# Importing the libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd


```

## import the dataset


```python
df = pd.read_csv('Data.csv')
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
      <th>Country</th>
      <th>Age</th>
      <th>Salary</th>
      <th>Purchased</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>France</td>
      <td>44.0</td>
      <td>72000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>27.0</td>
      <td>48000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Germany</td>
      <td>30.0</td>
      <td>54000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spain</td>
      <td>38.0</td>
      <td>61000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Germany</td>
      <td>40.0</td>
      <td>NaN</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>5</th>
      <td>France</td>
      <td>35.0</td>
      <td>58000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Spain</td>
      <td>NaN</td>
      <td>52000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>France</td>
      <td>48.0</td>
      <td>79000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Germany</td>
      <td>50.0</td>
      <td>83000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>9</th>
      <td>France</td>
      <td>37.0</td>
      <td>67000.0</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>
</div>



## NaN 처리 


```python
df.isna().sum()
```




    Country      0
    Age          1
    Salary       1
    Purchased    0
    dtype: int64




```python
# nan  처리전략
# 1. 삭제전략

```


```python
df.dropna()
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
      <th>Country</th>
      <th>Age</th>
      <th>Salary</th>
      <th>Purchased</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>France</td>
      <td>44.0</td>
      <td>72000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>27.0</td>
      <td>48000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Germany</td>
      <td>30.0</td>
      <td>54000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spain</td>
      <td>38.0</td>
      <td>61000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5</th>
      <td>France</td>
      <td>35.0</td>
      <td>58000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>7</th>
      <td>France</td>
      <td>48.0</td>
      <td>79000.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Germany</td>
      <td>50.0</td>
      <td>83000.0</td>
      <td>No</td>
    </tr>
    <tr>
      <th>9</th>
      <td>France</td>
      <td>37.0</td>
      <td>67000.0</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2. 특정값으로 채우기
```


```python
df.fillna(df.mean())
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
      <th>Country</th>
      <th>Age</th>
      <th>Salary</th>
      <th>Purchased</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>France</td>
      <td>44.000000</td>
      <td>72000.000000</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>27.000000</td>
      <td>48000.000000</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Germany</td>
      <td>30.000000</td>
      <td>54000.000000</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spain</td>
      <td>38.000000</td>
      <td>61000.000000</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Germany</td>
      <td>40.000000</td>
      <td>63777.777778</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>5</th>
      <td>France</td>
      <td>35.000000</td>
      <td>58000.000000</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Spain</td>
      <td>38.777778</td>
      <td>52000.000000</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>France</td>
      <td>48.000000</td>
      <td>79000.000000</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Germany</td>
      <td>50.000000</td>
      <td>83000.000000</td>
      <td>No</td>
    </tr>
    <tr>
      <th>9</th>
      <td>France</td>
      <td>37.000000</td>
      <td>67000.000000</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.fillna(df.mean())
```

## X,y 데이터 분리 : 즉 학습할 변수와 레이블링 변수로 분리


```python
# X를 종속변수
# y를 독립변수
```


```python
X = df.iloc[:,:3]
```


```python
y = df['Purchased']
```

## 데이터를 확인해 보니, 컴퓨터가 이해할 수 있도록 바꿔야 한다.

컴퓨터는 숫자로 처리한다.

숫자가 아닌 데이터 중에서, 카테고리로 판단되는 데이터는, 숫자로 바꿔줄 수 있다.

![1233443](/images/MachineLearning/6.jpg)


```python
X['Country'].describe()
```




    count         10
    unique         3
    top       France
    freq           4
    Name: Country, dtype: object




```python
X['Country'].unique()
```




    array(['France', 'Spain', 'Germany'], dtype=object)




```python
# 문자로 되어있는 데이터는, 방정식에 대입할 수가 없다.
# 따라서 문자를 숫자로 바꿔줘야 한다.
# 먼저, 해당 문자열이 카테고리컬 데이터인지 확인한다.
# 카테고리컬 데이터이면 데이터들을 정렬한다.
# 정렬한 후의 문자열들을 앞에서부터 0부터 시작하는 숫자로 변환한다.
# 이 방법을 Label Encoding 라 한다.
```


```python
sorted(X['Country'].unique())
```




    ['France', 'Germany', 'Spain']




```python
# France : 0 , Germany : 1 , Spain : 2
```


```python
# 3개 이상의 카테고리컬 데이터는 레이블 인코딩으로 학습을 시키면
# 학습이 잘 되지 않는것을 발견

#따라서 2개의 카테고리컬 데이터는 레이블 인코딩을 사용해도 되지만,
# 하지만 3개 이상의 카테고리컬 데이터느 One-Hot Encodingdm 사용해야 성능이 좋아진다.
```


```python
# France,Gramany , Spain
#    1     0         0   => 프랑스인 경우는 프랑스만 1로 셋팅
#     0   1          0 = > 독일인 경우는 독일만 1
#    0     0         1 => 스페인인 경우는 스페인만 1로 셋팅

#즉 카테고리컬 데이터를 전부 컬럼으로 만들어서,
# 해당 컬럼의 값만 1로 셋팅하는 것을 원 핫 인코딩이라고 한다.

 
```


```python
from sklearn.preprocessing import LabelEncoder,OneHotEncoder
```


```python
from sklearn.compose import ColumnTransformer
```


```python
# 1. 레이블 인코딩 하는 방법
```


```python
encoder = LabelEncoder()
```


```python
encoder.fit_transform(X['Country'])
```




    array([0, 2, 1, 2, 1, 0, 2, 0, 1, 0])




```python
X['Country'] =  encoder.fit_transform(X['Country'])
```


```python
X.head()
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
      <th>Country</th>
      <th>Age</th>
      <th>Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>44.0</td>
      <td>72000.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>27.0</td>
      <td>48000.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>30.0</td>
      <td>54000.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>38.0</td>
      <td>61000.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>40.0</td>
      <td>63777.777778</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2. 원 핫 인코딩 하는 방법
```


```python
X = df.iloc[:,0:3]
```


```python
# 0 이라고 쓴 이유는? X에서 원핫 인코딩 할 컬럼이 컴퓨터가 매기는 인덱스로 0이기 때문이다.
# 만약에 Salary 컬럼도 원핫 인코딩 한다 가정하면 [0,2] 라고 컴퓨터가 매기는 인덱스를 추가로 적어주면 된다.
ct = ColumnTransformer([('encoder',OneHotEncoder(),[0])],remainder='passthrough')
```


```python
# 원핫 인코딩이 수행된 컬럼은, 항상 행렬의 맨 왼쪽에 나온다.
X = ct.fit_transform(X)
```


```python
X
```




    array([[1.00000000e+00, 0.00000000e+00, 0.00000000e+00, 4.40000000e+01,
            7.20000000e+04],
           [0.00000000e+00, 0.00000000e+00, 1.00000000e+00, 2.70000000e+01,
            4.80000000e+04],
           [0.00000000e+00, 1.00000000e+00, 0.00000000e+00, 3.00000000e+01,
            5.40000000e+04],
           [0.00000000e+00, 0.00000000e+00, 1.00000000e+00, 3.80000000e+01,
            6.10000000e+04],
           [0.00000000e+00, 1.00000000e+00, 0.00000000e+00, 4.00000000e+01,
            6.37777778e+04],
           [1.00000000e+00, 0.00000000e+00, 0.00000000e+00, 3.50000000e+01,
            5.80000000e+04],
           [0.00000000e+00, 0.00000000e+00, 1.00000000e+00, 3.87777778e+01,
            5.20000000e+04],
           [1.00000000e+00, 0.00000000e+00, 0.00000000e+00, 4.80000000e+01,
            7.90000000e+04],
           [0.00000000e+00, 1.00000000e+00, 0.00000000e+00, 5.00000000e+01,
            8.30000000e+04],
           [1.00000000e+00, 0.00000000e+00, 0.00000000e+00, 3.70000000e+01,
            6.70000000e+04]])




```python
y
```




    0     No
    1    Yes
    2     No
    3     No
    4    Yes
    5    Yes
    6     No
    7    Yes
    8     No
    9    Yes
    Name: Purchased, dtype: object




```python
y.describe()
```




    count     10
    unique     2
    top       No
    freq       5
    Name: Purchased, dtype: object




```python
sorted(y.unique())
```




    ['No', 'Yes']




```python
encoder_y = LabelEncoder()
```


```python
y = encoder_y.fit_transform(y)
```

# Dataset을 Training 용과 Test용으로 나눈다.


```python
# 숫자로 다 변환된 X와 y를 
# 학습용 데이터와 테스트용 데이터로 나눈다.
# 그 결과는 총 4개의 데이터가 나온다. 그림참고.

from sklearn.model_selection import train_test_split
```


```python
X_train, X_test, y_train, y_test = train_test_split(X,y,test_size= 0.2,random_state=3)
```


```python
X_train.shape
```




    (8, 5)



## Feature Scaling

### Age 와 Salary 는 같은 스케일이 아니다. 

Age 는 27 ~ 50
Salary 는 40k ~ 90k


```python
# 유클리디언 디스턴스로 오차를 줄여 나가는데, 하나의 변수는 오차가 크고, 하나의 변수는 오차가 작으면, 나중에 오차를 수정할때 편중되게 된다. 
# 따라서 값의 레인지를 맞춰줘야 정확히 트레이닝 된다.
```

![1233443](/images/MachineLearning/7.png)

##  Feature Scaling 2가지 방법

- 표준화 : 평균을 기준으로 얼마나 떨어져 있느냐? 같은 기준으로 만드는 방법, 음수도 존재, 데이터의 최대최소값 모를때 사용.
- 정규화 : 0 ~ 1 사이로 맞추는 것. 데이터의 위치 비교가 가능, 데이터의 최대최소값 알떄 사용

![124gg43](/images/MachineLearning/8.png)

```python
from sklearn.preprocessing import StandardScaler,MinMaxScaler
```


```python
# X는 피쳐 스케일링이 필요하다.
# 따라서 X용 스탠다드 스케일러 만들어서 사용한다.
s_scaler = StandardScaler()
```


```python
X_train_s = s_scaler.fit_transform(X_train)
```


```python
X_test_s = s_scaler.transform(X_test)
```


```python
# y는 피쳐 스케일링 필요??
y
# 이미 0과 1로 구성 되어 있으므로 피쳐 스케일링 불필요.
```




    array([0, 1, 0, 0, 1, 1, 0, 1, 0, 1])




```python
# 노멀리제이션 으로 피쳐 스케일링 한 경우.
m_scaler = MinMaxScaler()
```


```python
X_train_m = m_scaler.fit_transform(X_train)
```


```python
X_test_m = m_scaler.fit(X_test)
```


```python
# 인공지능 학습 전 단계 데이터 가공
```
