---
layout : single
title : "ANN을 이용한 가격 예측 -colab"
categories: Coding_Training
tag : [Python,DeepLearning,Colab]
author_profile: false
toc : true
toc_sticky: true
sidebar:
    nav: "docs"
---
# 자동차 구매 가격 예측



# PROBLEM STATEMENT

다음과 같은 컬럼을 가지고 있는 데이터셋을 읽어서, 어떠한 고객이 있을때, 그 고객이 얼마정도의 차를 구매할 수 있을지를 예측하여, 그 사람에게 맞는 자동차를 보여주려 한다. 

- Customer Name
- Customer e-mail
- Country
- Gender
- Age
- Annual Salary 
- Credit Card Debt 
- Net Worth (순자산)

예측하고자 하는 값 : 
- Car Purchase Amount 

# STEP #0: 라이브러리 임포트 및 코랩 환경 설정

[구글 드라이브 파일 읽기 참고](https://vision-ai.tistory.com/entry/%EC%BD%94%EB%9E%A9%EC%97%90%EC%84%9C-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B8%8C%EC%9D%98-csv-%ED%8C%8C%EC%9D%BC-%EC%9D%BD%EA%B8%B0)



```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

 csv 파일을 읽기 위해, 구글 드라이브 마운트 하시오


```python
from google.colab import drive
drive.mount('/content/drive')
```

    Mounted at /content/drive
    

 working directory 를, 현재의 파일이 속한 폴더로 셋팅하시오.


```python
import os
os.chdir('/content/drive/MyDrive/python/day17')
```

# STEP #1: IMPORT DATASET

Car_Purchasing_Data.csv 파일을 사용한다.  코랩의 경우 구글드라이브의 전체경로를 복사하여 파일 읽는다. 

인코딩은 다음처럼 한다. encoding='ISO-8859-1'


```python
car_df = pd.read_csv('Car_Purchasing_Data.csv', encoding='ISO-8859-1')
```

 컬럼을 확인하고

기본 통계 데이터를 확인해 보자


```python
car_df
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
      <th>Customer Name</th>
      <th>Customer e-mail</th>
      <th>Country</th>
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
      <th>Car Purchase Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Martina Avila</td>
      <td>cubilia.Curae.Phasellus@quisaccumsanconvallis.edu</td>
      <td>Bulgaria</td>
      <td>0</td>
      <td>41.851720</td>
      <td>62812.09301</td>
      <td>11609.380910</td>
      <td>238961.2505</td>
      <td>35321.45877</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harlan Barnes</td>
      <td>eu.dolor@diam.co.uk</td>
      <td>Belize</td>
      <td>0</td>
      <td>40.870623</td>
      <td>66646.89292</td>
      <td>9572.957136</td>
      <td>530973.9078</td>
      <td>45115.52566</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Naomi Rodriquez</td>
      <td>vulputate.mauris.sagittis@ametconsectetueradip...</td>
      <td>Algeria</td>
      <td>1</td>
      <td>43.152897</td>
      <td>53798.55112</td>
      <td>11160.355060</td>
      <td>638467.1773</td>
      <td>42925.70921</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jade Cunningham</td>
      <td>malesuada@dignissim.com</td>
      <td>Cook Islands</td>
      <td>1</td>
      <td>58.271369</td>
      <td>79370.03798</td>
      <td>14426.164850</td>
      <td>548599.0524</td>
      <td>67422.36313</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Cedric Leach</td>
      <td>felis.ullamcorper.viverra@egetmollislectus.net</td>
      <td>Brazil</td>
      <td>1</td>
      <td>57.313749</td>
      <td>59729.15130</td>
      <td>5358.712177</td>
      <td>560304.0671</td>
      <td>55915.46248</td>
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
      <th>495</th>
      <td>Walter</td>
      <td>ligula@Cumsociis.ca</td>
      <td>Nepal</td>
      <td>0</td>
      <td>41.462515</td>
      <td>71942.40291</td>
      <td>6995.902524</td>
      <td>541670.1016</td>
      <td>48901.44342</td>
    </tr>
    <tr>
      <th>496</th>
      <td>Vanna</td>
      <td>Cum.sociis.natoque@Sedmolestie.edu</td>
      <td>Zimbabwe</td>
      <td>1</td>
      <td>37.642000</td>
      <td>56039.49793</td>
      <td>12301.456790</td>
      <td>360419.0988</td>
      <td>31491.41457</td>
    </tr>
    <tr>
      <th>497</th>
      <td>Pearl</td>
      <td>penatibus.et@massanonante.com</td>
      <td>Philippines</td>
      <td>1</td>
      <td>53.943497</td>
      <td>68888.77805</td>
      <td>10611.606860</td>
      <td>764531.3203</td>
      <td>64147.28888</td>
    </tr>
    <tr>
      <th>498</th>
      <td>Nell</td>
      <td>Quisque.varius@arcuVivamussit.net</td>
      <td>Botswana</td>
      <td>1</td>
      <td>59.160509</td>
      <td>49811.99062</td>
      <td>14013.034510</td>
      <td>337826.6382</td>
      <td>45442.15353</td>
    </tr>
    <tr>
      <th>499</th>
      <td>Marla</td>
      <td>Camaron.marla@hotmail.com</td>
      <td>marlal</td>
      <td>1</td>
      <td>46.731152</td>
      <td>61370.67766</td>
      <td>9391.341628</td>
      <td>462946.4924</td>
      <td>45107.22566</td>
    </tr>
  </tbody>
</table>
<p>500 rows × 9 columns</p>
</div>




```python
car_df.isna().sum()
```




    Customer Name          0
    Customer e-mail        0
    Country                0
    Gender                 0
    Age                    0
    Annual Salary          0
    Credit Card Debt       0
    Net Worth              0
    Car Purchase Amount    0
    dtype: int64



 연봉이 가장 높은 사람은 누구인가


```python
car_df[car_df['Annual Salary'] ==car_df['Annual Salary'].max()]
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
      <th>Customer Name</th>
      <th>Customer e-mail</th>
      <th>Country</th>
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
      <th>Car Purchase Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28</th>
      <td>Gemma Hendrix</td>
      <td>lobortis@non.co.uk</td>
      <td>Denmark</td>
      <td>1</td>
      <td>46.124036</td>
      <td>100000.0</td>
      <td>17452.92179</td>
      <td>188032.0778</td>
      <td>58350.31809</td>
    </tr>
  </tbody>
</table>
</div>



 나이가 가장 어린 고객은, 연봉이 얼마인가


```python
car_df[car_df['Age'] == car_df['Age'].min()]
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
      <th>Customer Name</th>
      <th>Customer e-mail</th>
      <th>Country</th>
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
      <th>Car Purchase Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>444</th>
      <td>Camden</td>
      <td>Aliquam.adipiscing.lobortis@loremut.net</td>
      <td>Congo (Brazzaville)</td>
      <td>1</td>
      <td>20.0</td>
      <td>70467.29492</td>
      <td>100.0</td>
      <td>494606.6334</td>
      <td>28645.39425</td>
    </tr>
  </tbody>
</table>
</div>



# STEP #2: VISUALIZE DATASET

 상관관계를 분석하기 위해, pairplot 을 그려보자.


```python
sns.pairplot(car_df)

```




    <seaborn.axisgrid.PairGrid at 0x7f0265add490>




    
![png](/images/ANN/output_19_1.png)
    



```python
car_df.corr()
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
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
      <th>Car Purchase Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gender</th>
      <td>1.000000</td>
      <td>-0.064481</td>
      <td>-0.036499</td>
      <td>0.024193</td>
      <td>-0.008395</td>
      <td>-0.066408</td>
    </tr>
    <tr>
      <th>Age</th>
      <td>-0.064481</td>
      <td>1.000000</td>
      <td>0.000130</td>
      <td>0.034721</td>
      <td>0.020356</td>
      <td>0.632865</td>
    </tr>
    <tr>
      <th>Annual Salary</th>
      <td>-0.036499</td>
      <td>0.000130</td>
      <td>1.000000</td>
      <td>0.049599</td>
      <td>0.014767</td>
      <td>0.617862</td>
    </tr>
    <tr>
      <th>Credit Card Debt</th>
      <td>0.024193</td>
      <td>0.034721</td>
      <td>0.049599</td>
      <td>1.000000</td>
      <td>-0.049378</td>
      <td>0.028882</td>
    </tr>
    <tr>
      <th>Net Worth</th>
      <td>-0.008395</td>
      <td>0.020356</td>
      <td>0.014767</td>
      <td>-0.049378</td>
      <td>1.000000</td>
      <td>0.488580</td>
    </tr>
    <tr>
      <th>Car Purchase Amount</th>
      <td>-0.066408</td>
      <td>0.632865</td>
      <td>0.617862</td>
      <td>0.028882</td>
      <td>0.488580</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



# STEP #3: CREATE TESTING AND TRAINING DATASET/DATA CLEANING




NaN 값이 있으면, 이를 해결하시오.


```python
car_df.isna().sum()
```




    Customer Name          0
    Customer e-mail        0
    Country                0
    Gender                 0
    Age                    0
    Annual Salary          0
    Credit Card Debt       0
    Net Worth              0
    Car Purchase Amount    0
    dtype: int64



학습을 위해 'Customer Name', 'Customer e-mail', 'Country', 'Car Purchase Amount' 컬럼을 제외한 컬럼만, X로 만드시오.


```python
car_df.head()
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
      <th>Customer Name</th>
      <th>Customer e-mail</th>
      <th>Country</th>
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
      <th>Car Purchase Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Martina Avila</td>
      <td>cubilia.Curae.Phasellus@quisaccumsanconvallis.edu</td>
      <td>Bulgaria</td>
      <td>0</td>
      <td>41.851720</td>
      <td>62812.09301</td>
      <td>11609.380910</td>
      <td>238961.2505</td>
      <td>35321.45877</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harlan Barnes</td>
      <td>eu.dolor@diam.co.uk</td>
      <td>Belize</td>
      <td>0</td>
      <td>40.870623</td>
      <td>66646.89292</td>
      <td>9572.957136</td>
      <td>530973.9078</td>
      <td>45115.52566</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Naomi Rodriquez</td>
      <td>vulputate.mauris.sagittis@ametconsectetueradip...</td>
      <td>Algeria</td>
      <td>1</td>
      <td>43.152897</td>
      <td>53798.55112</td>
      <td>11160.355060</td>
      <td>638467.1773</td>
      <td>42925.70921</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jade Cunningham</td>
      <td>malesuada@dignissim.com</td>
      <td>Cook Islands</td>
      <td>1</td>
      <td>58.271369</td>
      <td>79370.03798</td>
      <td>14426.164850</td>
      <td>548599.0524</td>
      <td>67422.36313</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Cedric Leach</td>
      <td>felis.ullamcorper.viverra@egetmollislectus.net</td>
      <td>Brazil</td>
      <td>1</td>
      <td>57.313749</td>
      <td>59729.15130</td>
      <td>5358.712177</td>
      <td>560304.0671</td>
      <td>55915.46248</td>
    </tr>
  </tbody>
</table>
</div>




```python
X = car_df.iloc[:,3:-1]
```


```python
X
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
      <th>Gender</th>
      <th>Age</th>
      <th>Annual Salary</th>
      <th>Credit Card Debt</th>
      <th>Net Worth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>41.851720</td>
      <td>62812.09301</td>
      <td>11609.380910</td>
      <td>238961.2505</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>40.870623</td>
      <td>66646.89292</td>
      <td>9572.957136</td>
      <td>530973.9078</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>43.152897</td>
      <td>53798.55112</td>
      <td>11160.355060</td>
      <td>638467.1773</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>58.271369</td>
      <td>79370.03798</td>
      <td>14426.164850</td>
      <td>548599.0524</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>57.313749</td>
      <td>59729.15130</td>
      <td>5358.712177</td>
      <td>560304.0671</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>495</th>
      <td>0</td>
      <td>41.462515</td>
      <td>71942.40291</td>
      <td>6995.902524</td>
      <td>541670.1016</td>
    </tr>
    <tr>
      <th>496</th>
      <td>1</td>
      <td>37.642000</td>
      <td>56039.49793</td>
      <td>12301.456790</td>
      <td>360419.0988</td>
    </tr>
    <tr>
      <th>497</th>
      <td>1</td>
      <td>53.943497</td>
      <td>68888.77805</td>
      <td>10611.606860</td>
      <td>764531.3203</td>
    </tr>
    <tr>
      <th>498</th>
      <td>1</td>
      <td>59.160509</td>
      <td>49811.99062</td>
      <td>14013.034510</td>
      <td>337826.6382</td>
    </tr>
    <tr>
      <th>499</th>
      <td>1</td>
      <td>46.731152</td>
      <td>61370.67766</td>
      <td>9391.341628</td>
      <td>462946.4924</td>
    </tr>
  </tbody>
</table>
<p>500 rows × 5 columns</p>
</div>



 y 값은 'Car Purchase Amount' 컬럼으로 셋팅하시오.


```python
y = car_df['Car Purchase Amount']
```

 피처 스케일링 하겠습니다. 정규화(normalization)를 사용합니다. MinMaxScaler 를 이용하시오.


```python
from sklearn.preprocessing import MinMaxScaler
```


```python
scaler_X = MinMaxScaler()
```


```python
X = scaler_X.fit_transform(X)
```


```python
X
```




    array([[0.        , 0.4370344 , 0.53515116, 0.57836085, 0.22342985],
           [0.        , 0.41741247, 0.58308616, 0.476028  , 0.52140195],
           [1.        , 0.46305795, 0.42248189, 0.55579674, 0.63108896],
           ...,
           [1.        , 0.67886994, 0.61110973, 0.52822145, 0.75972584],
           [1.        , 0.78321017, 0.37264988, 0.69914746, 0.3243129 ],
           [1.        , 0.53462305, 0.51713347, 0.46690159, 0.45198622]])



 학습을 위해서, y 의 shape 을 변경하시오.


```python
y = y.reshape(500,1)
```




 y 도 피처 스케일링 하겠습니다. X 처럼 y도 노멀라이징 하시오.


```python
scaler_y = MinMaxScaler()
```


```python
y = scaler_y.fit_transform(y)
```

# STEP#4: TRAINING THE MODEL

 트레이닝셋과 테스트셋으로 분리하시오. (테스트 사이즈는 25%로 하며, 동일 결과를 위해 랜덤스테이트는 50 으로 셋팅하시오.)


```python
from sklearn.model_selection import train_test_split
```


```python
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.25,random_state=50)
```

 아래 라이브러리를 임포트 하시오


```python
import tensorflow.keras
from keras.models import Sequential
from keras.layers import Dense
from sklearn.preprocessing import MinMaxScaler
```

 딥러닝을 이용한 모델링을 하시오.


```python
model = Sequential()
```


```python
model.add( Dense(units=6,activation='relu',input_dim=5) )
```


```python
model.add( Dense(units=10,activation='relu') )
```


```python
model.add( Dense(units=6,activation='relu') )
```


```python
# 리그레션 문제의 액티베이션 펑션은 linear 사용
model.add(Dense(units=1,activation='linear'))
```


```python
model.summary()
```

    Model: "sequential_5"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_18 (Dense)            (None, 6)                 36        
                                                                     
     dense_19 (Dense)            (None, 10)                70        
                                                                     
     dense_20 (Dense)            (None, 6)                 66        
                                                                     
     dense_21 (Dense)            (None, 1)                 7         
                                                                     
    =================================================================
    Total params: 179
    Trainable params: 179
    Non-trainable params: 0
    _________________________________________________________________
    

옵티마이저는 'adam' 으로 하고, 로스펑션은 'mean_squared_error' 로 셋팅하여 컴파일 하시오


```python
model.compile(optimizer='adam',loss='mean_squared_error')
```

학습을 진행하시오.


```python
epoch_history = model.fit(X_train,y_train, batch_size=20,epochs=29)
```

    Epoch 1/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0347
    Epoch 2/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0256
    Epoch 3/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0193
    Epoch 4/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0147
    Epoch 5/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0113
    Epoch 6/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0093
    Epoch 7/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0083
    Epoch 8/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0079
    Epoch 9/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0075
    Epoch 10/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0071
    Epoch 11/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0066
    Epoch 12/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0063
    Epoch 13/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0058
    Epoch 14/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0054
    Epoch 15/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0052
    Epoch 16/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0047
    Epoch 17/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0044
    Epoch 18/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0039
    Epoch 19/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0036
    Epoch 20/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0032
    Epoch 21/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0028
    Epoch 22/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0026
    Epoch 23/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0023
    Epoch 24/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0020
    Epoch 25/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0017
    Epoch 26/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0014
    Epoch 27/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0013
    Epoch 28/29
    19/19 [==============================] - 0s 2ms/step - loss: 0.0010
    Epoch 29/29
    19/19 [==============================] - 0s 2ms/step - loss: 8.6643e-04
    

# STEP#5: EVALUATING THE MODEL 


```python
y_pred = model.predict(X_test)
```


```python
# MSE : 오차를 구하고 제곱한 후 평균을 구한다
# Mean Squared Error
((y_test - y_pred)**2).mean()
```




    0.0011123861375233498



실제값과 예측값을 plot 으로 나타내시오.


```python
plt.plot(y_test)
plt.plot(y_pred)
plt.legend(['real','pred'])
plt.show()
```


    
![png](/images/ANN/output_61_0.png)
    


 새로운 고객 데이터가 있습니다. 이 사람은 차량을 얼마정도 구매 가능한지 예측하시오.

여자이고, 나이는 38, 연봉은 90000,  카드빚은 2000, 순자산은 500000 일때, 어느정도의 차량을 구매할 수 있을지 예측하시오.


```python
new_data = np.array([1,38,90000,2000,50000])
```


```python
new_data = new_data.reshape(1,5)
```


```python
new_data = scaler_X.transform(new_data)
```


```python
y_pred = model.predict(new_data)
```


```python
scaler_y.inverse_transform(y_pred)
```




    array([[3.7154422e+09]], dtype=float32)


