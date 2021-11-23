---
layout : single
title : "파이썬 - Pandas 실습 - 4 "
categories: Coding_Training
tag : [Python,Pandas]
author_profile: false
sidebar:
    nav: "docs"
---
# Statistics from Stock Data

구글, 애플, 아마존의 주식을 분석할 것입니다. 구글은 GOOG.csv 애플은 AAPL.csv 아마존은 AMZN.csv 파일에 주식 정보가 있습니다.

다음 7개의 컬럼이 있습니다

**Date Open High Low Close Adj_Close Volume**

csv 파일을 읽어서 DataFrame 으로 처리할 것입니다.


```python
# 판다스를 임포트 하세요.
import pandas as pd 

# GOOG.csv 파일을 판다스로 읽어서 저장하세요.
df = pd.read_csv('GOOG.csv')

# 데이터의 처음 5줄을 화면에 출력하세요.
```


```python
df.head(5)
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.676899</td>
      <td>51.693783</td>
      <td>47.669952</td>
      <td>49.845802</td>
      <td>49.845802</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.178635</td>
      <td>54.187561</td>
      <td>49.925285</td>
      <td>53.805050</td>
      <td>53.805050</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.017166</td>
      <td>56.373344</td>
      <td>54.172661</td>
      <td>54.346527</td>
      <td>54.346527</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.260582</td>
      <td>55.439419</td>
      <td>51.450363</td>
      <td>52.096165</td>
      <td>52.096165</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.140873</td>
      <td>53.651051</td>
      <td>51.604362</td>
      <td>52.657513</td>
      <td>52.657513</td>
      <td>9257400</td>
    </tr>
  </tbody>
</table>
</div>





# To Do

우리는, 각 date 에 해당되는 adj close 값만 관심이 있습니다. 따라서 컬럼은 두개만 사용하며, 이 두개 컬럼의 인덱스는 date로 만듭니다. 

hints:

* Use the `index_col` keyword to indicate which column you want to use as an index. For example `index_col = ['Open']`

* Set the `parse_dates` keyword equal to `True` to convert the Dates into real dates of the form year/month/day

* Use the `usecols` keyword to select which columns you want to load into the DataFrame. For example `usecols = ['Open', 'High']`

Fill in the code below:


```python
pd.read_csv("GOOG.csv",usecols=['Date','Adj Close'],index_col = ['Date'],parse_dates=True).head()
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
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We load the Google stock data into a DataFrame
google_stock = pd.read_csv("GOOG.csv",usecols=['Date','Adj Close'],index_col = ['Date'],parse_dates=True)
```


```python
# We load the Apple stock data into a DataFrame
apple_stock = pd.read_csv("AAPL.csv",usecols=['Date','Adj Close'],index_col = ['Date'],parse_dates=True)


```


```python
# We load the Amazon stock data into a DataFrame
amazon_stock = pd.read_csv("AMZN.csv",usecols=['Date','Adj Close'],index_col = ['Date'],parse_dates=True)


```

데이터 6개까지 출력해 봅니다.


```python
apple_stock.head(6)
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
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>3.596616</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>3.293384</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>3.341579</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>3.052405</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>3.196992</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>3.140763</td>
    </tr>
  </tbody>
</table>
</div>




```python
amazon_stock.head(6)
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
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>69.7500</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>65.5625</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>69.5625</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>69.1875</td>
    </tr>
  </tbody>
</table>
</div>



`2000-01-01`  부터  `2016-12-31`년 까지의 데이터를 처리할것인데  `pd.date_range()` 함수를 이용해서 dates 변수를 만드세요. 그리고 나서 위의  dates 를 인덱스로 하여, 새로 all_stocks 란 데이터프레임을 만드세요


```python
# We create calendar dates between '2000-01-01' and  '2016-12-31'
dates = pd.date_range('2000-01-01','2016-12-31') 

```


```python
dates
```




    DatetimeIndex(['2000-01-01', '2000-01-02', '2000-01-03', '2000-01-04',
                   '2000-01-05', '2000-01-06', '2000-01-07', '2000-01-08',
                   '2000-01-09', '2000-01-10',
                   ...
                   '2016-12-22', '2016-12-23', '2016-12-24', '2016-12-25',
                   '2016-12-26', '2016-12-27', '2016-12-28', '2016-12-29',
                   '2016-12-30', '2016-12-31'],
                  dtype='datetime64[ns]', length=6210, freq='D')




```python
pd.DataFrame(index= dates).head(5)
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-01</th>
    </tr>
    <tr>
      <th>2000-01-02</th>
    </tr>
    <tr>
      <th>2000-01-03</th>
    </tr>
    <tr>
      <th>2000-01-04</th>
    </tr>
    <tr>
      <th>2000-01-05</th>
    </tr>
  </tbody>
</table>
</div>




```python
# We create and empty DataFrame that uses the above dates as indices
all_stocks = pd.DataFrame(index= dates)
```


```python
all_stocks
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-01</th>
    </tr>
    <tr>
      <th>2000-01-02</th>
    </tr>
    <tr>
      <th>2000-01-03</th>
    </tr>
    <tr>
      <th>2000-01-04</th>
    </tr>
    <tr>
      <th>2000-01-05</th>
    </tr>
    <tr>
      <th>...</th>
    </tr>
    <tr>
      <th>2016-12-27</th>
    </tr>
    <tr>
      <th>2016-12-28</th>
    </tr>
    <tr>
      <th>2016-12-29</th>
    </tr>
    <tr>
      <th>2016-12-30</th>
    </tr>
    <tr>
      <th>2016-12-31</th>
    </tr>
  </tbody>
</table>
<p>6210 rows × 0 columns</p>
</div>



# To Do

각 `google_stock`, `apple_stock`, `amazon_stock`, 을,  `all_stocks` 의 날짜에 매칭하여 수정종가를 나오게 하기 위해, all_stocks와 각각의 데이터프레임을 join 할 것입니다. 그러나 일단은 먼저, 현재의 구글,애플, 아마존의 DataFrame에 있는 컬럼명을, 각각의 수정종가로 표현하기 위해, 각각의 adj close 를 google_stock, apple_stock, amazon_stock 로 바꿔주세요.  `pd.DataFrame.rename()` 함수를 이용하세요.


```python
google_stock.rename(columns={"Adj Close":"google_stock"})
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
      <th>google_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>2017-10-09</th>
      <td>977.000000</td>
    </tr>
    <tr>
      <th>2017-10-10</th>
      <td>972.599976</td>
    </tr>
    <tr>
      <th>2017-10-11</th>
      <td>989.250000</td>
    </tr>
    <tr>
      <th>2017-10-12</th>
      <td>987.830017</td>
    </tr>
    <tr>
      <th>2017-10-13</th>
      <td>989.679993</td>
    </tr>
  </tbody>
</table>
<p>3313 rows × 1 columns</p>
</div>




```python
# Change the Adj Close column label to Google
google_stock = google_stock.rename(columns={"Adj Close":"google_stock"})

# Change the Adj Close column label to Apple
apple_stock = apple_stock.rename(columns={"Adj Close":"apple_stock"})

# Change the Adj Close column label to Amazon
amazon_stock =  amazon_stock.rename(columns={"Adj Close":"amazon_stock"})
```


```python
# We display the google_stock DataFrame
google_stock.head()
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
      <th>google_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We display the apple_stock DataFrame
apple_stock.head()
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
      <th>apple_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>3.596616</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>3.293384</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>3.341579</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>3.052405</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>3.196992</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We display the amazon_stock DataFrame
amazon_stock.head()
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
      <th>amazon_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>69.7500</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>65.5625</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>69.5625</td>
    </tr>
  </tbody>
</table>
</div>



이제 `all_stocks` DataFrame 를 기준으로, 각각의 구글,애플,아마존의 데이터프레임을 합치겠습니다. `dataframe.join()` 함수를 이용하세요. T `dataframe1.join(dataframe2)`  `dataframe1` 을 기준으로 `dataframe2`를 합치는 함수입니다. 


```python
all_stocks.join([google_stock,apple_stock,amazon_stock]).head(5)
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-03</th>
      <td>NaN</td>
      <td>3.596616</td>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>NaN</td>
      <td>3.293384</td>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>NaN</td>
      <td>3.341579</td>
      <td>69.7500</td>
    </tr>
  </tbody>
</table>
</div>



 `all_stocks`  를 앞에서 10줄 출력하여 확인하세요.


```python
all_stocks = all_stocks.join([google_stock,apple_stock,amazon_stock])
```


```python
all_stocks.head(10)
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-03</th>
      <td>NaN</td>
      <td>3.596616</td>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>NaN</td>
      <td>3.293384</td>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>NaN</td>
      <td>3.341579</td>
      <td>69.7500</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>NaN</td>
      <td>3.052405</td>
      <td>65.5625</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>NaN</td>
      <td>3.196992</td>
      <td>69.5625</td>
    </tr>
    <tr>
      <th>2000-01-08</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-09</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>NaN</td>
      <td>3.140763</td>
      <td>69.1875</td>
    </tr>
  </tbody>
</table>
</div>



# To Do

해당 년도의 데이터가 없는 경우도 있을것입니다. 즉, 데이터가 NaN 으로 나오면 해당년도 데이터가 없는것입니다. 그러므로 NaN이 포함되어 있는지 먼저 확인해 봅니다.


```python
# Check if there are any NaN values in the all_stocks dataframe
all_stocks.isna().sum()
```




    google_stock    3095
    apple_stock     1933
    amazon_stock    1933
    dtype: int64



이제 NaN 값을 포함하는 행은 제거합니다.


```python
all_stocks.dropna(inplace=True)
```

 `all_stocks`  에 NaN 이 없어졌는지 체크해 보세요.


```python
# Check if there are any NaN values in the all_stocks dataframe
all_stocks.isna().sum()
```




    google_stock    0
    apple_stock     0
    amazon_stock    0
    dtype: int64



 `all_stocks`  를 화면에 출력하세요.


```python
# We display the all_stocks DataFrame
all_stocks.head()
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
      <td>1.973460</td>
      <td>38.630001</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
      <td>1.979244</td>
      <td>39.509998</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
      <td>1.997236</td>
      <td>39.450001</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
      <td>2.053144</td>
      <td>39.049999</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
      <td>2.123831</td>
      <td>40.299999</td>
    </tr>
  </tbody>
</table>
</div>



이제 아래의 통계데이터를 얻어봅시다. 아래를 각각 채워서 실행해 보세요.


```python
# 각 스톡의 평균을 출력하세요
all_stocks.mean()
```




    google_stock    347.420229
    apple_stock      47.736018
    amazon_stock    216.598177
    dtype: float64




```python
# 각 스톡의 표준편차를 출력하세요.
all_stocks.std()
```




    google_stock    187.671596
    apple_stock      37.421555
    amazon_stock    199.129792
    dtype: float64




```python
all_stocks.head(3)
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
      <td>1.973460</td>
      <td>38.630001</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
      <td>1.979244</td>
      <td>39.509998</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
      <td>1.997236</td>
      <td>39.450001</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 각 스톡의 correlation을 출력하세요. 상관관계

all_stocks.corr()
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>google_stock</th>
      <td>1.000000</td>
      <td>0.900242</td>
      <td>0.952444</td>
    </tr>
    <tr>
      <th>apple_stock</th>
      <td>0.900242</td>
      <td>1.000000</td>
      <td>0.886321</td>
    </tr>
    <tr>
      <th>amazon_stock</th>
      <td>0.952444</td>
      <td>0.886321</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 상관분석의 결과로 나온 수치를 상관계수라고 부른다. (coefficient)
# 상관계수는 -1 ~ 1 사이의 실수
# 0 근처이면, 아무 관련 없다.
# 1로 갈수록, 강한 비례관계가 있다.
# -1로 갈수록, 강한 반비례관계가 있다.
```


```python
from datetime import date
```


```python
# 2007년 부터 2013년 까지의 데이터를 가지고,
#각 주식의 평균,표준변차, 상관관계를 분석해보세요.
```


```python
all_stocks.loc['2007-01-01':'2013-12-31',].head()
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2007-01-03</th>
      <td>232.284210</td>
      <td>10.770167</td>
      <td>38.700001</td>
    </tr>
    <tr>
      <th>2007-01-04</th>
      <td>240.068588</td>
      <td>11.009220</td>
      <td>38.900002</td>
    </tr>
    <tr>
      <th>2007-01-05</th>
      <td>242.020889</td>
      <td>10.930819</td>
      <td>38.369999</td>
    </tr>
    <tr>
      <th>2007-01-08</th>
      <td>240.227554</td>
      <td>10.984798</td>
      <td>37.500000</td>
    </tr>
    <tr>
      <th>2007-01-09</th>
      <td>241.181351</td>
      <td>11.897308</td>
      <td>37.779999</td>
    </tr>
  </tbody>
</table>
</div>




```python
all_stocks.loc['2007-01-01':'2013-12-31',].mean()
```




    google_stock    289.131730
    apple_stock      38.548012
    amazon_stock    154.003332
    dtype: float64




```python
all_stocks.loc['2007-01-01':'2013-12-31',].std()
```




    google_stock    78.582106
    apple_stock     22.089632
    amazon_stock    85.059395
    dtype: float64




```python
all_stocks.loc['2007-01-01':'2013-12-31',].corr()
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
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>google_stock</th>
      <td>1.000000</td>
      <td>0.713646</td>
      <td>0.854917</td>
    </tr>
    <tr>
      <th>apple_stock</th>
      <td>0.713646</td>
      <td>1.000000</td>
      <td>0.899271</td>
    </tr>
    <tr>
      <th>amazon_stock</th>
      <td>0.854917</td>
      <td>0.899271</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>


