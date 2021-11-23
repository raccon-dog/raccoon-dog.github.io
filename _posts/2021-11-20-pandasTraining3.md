winemag-data.csv 파일을 reviews 로 읽는다.


```python
import pandas as pd
import numpy as np
```


```python
reviews = pd.read_csv("winemag-data.csv",index_col = 0)
```


```python
reviews.head(2)
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Italy</td>
      <td>Aromas include tropical fruit, broom, brimston...</td>
      <td>Vulkà Bianco</td>
      <td>87</td>
      <td>NaN</td>
      <td>Sicily &amp; Sardinia</td>
      <td>Etna</td>
      <td>NaN</td>
      <td>Kerin O’Keefe</td>
      <td>@kerinokeefe</td>
      <td>Nicosia 2013 Vulkà Bianco  (Etna)</td>
      <td>White Blend</td>
      <td>Nicosia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Portugal</td>
      <td>This is ripe and fruity, a wine that is smooth...</td>
      <td>Avidagos</td>
      <td>87</td>
      <td>15.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Quinta dos Avidagos 2011 Avidagos Red (Douro)</td>
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
    </tr>
  </tbody>
</table>
</div>



리뷰 데이터프레임에서 points 컬럼의  median 값은?


```python
reviews['points'].median()
```




    88.0



나라를 중복되지 않도록 가져와서 countries 변수에 저장하고, 화면에 출력하시오.


```python
countries = reviews['country'].unique()
```


```python
print(countries)
```

    ['Italy' 'Portugal' 'US' 'Spain' 'France' 'Germany' 'Argentina' 'Chile'
     'Australia' 'Austria' 'South Africa' 'New Zealand' 'Israel' 'Hungary'
     'Greece' 'Romania' 'Mexico' 'Canada' nan 'Turkey' 'Czech Republic'
     'Slovenia' 'Luxembourg' 'Croatia' 'Georgia' 'Uruguay' 'England' 'Lebanon'
     'Serbia' 'Brazil' 'Moldova' 'Morocco' 'Peru' 'India' 'Bulgaria' 'Cyprus'
     'Armenia' 'Switzerland' 'Bosnia and Herzegovina' 'Ukraine' 'Slovakia'
     'Macedonia' 'China' 'Egypt']
    

각 국가별로는 몇개의 리뷰가 있는지, 각국가별 리뷰수를 구하시오.


```python
reviews['country'].value_counts()
```




    US                        54504
    France                    22093
    Italy                     19540
    Spain                      6645
    Portugal                   5691
    Chile                      4472
    Argentina                  3800
    Austria                    3345
    Australia                  2329
    Germany                    2165
    New Zealand                1419
    South Africa               1401
    Israel                      505
    Greece                      466
    Canada                      257
    Hungary                     146
    Bulgaria                    141
    Romania                     120
    Uruguay                     109
    Turkey                       90
    Slovenia                     87
    Georgia                      86
    England                      74
    Croatia                      73
    Mexico                       70
    Moldova                      59
    Brazil                       52
    Lebanon                      35
    Morocco                      28
    Peru                         16
    Ukraine                      14
    Czech Republic               12
    Macedonia                    12
    Serbia                       12
    Cyprus                       11
    India                         9
    Switzerland                   7
    Luxembourg                    6
    Bosnia and Herzegovina        2
    Armenia                       2
    Slovakia                      1
    Egypt                         1
    China                         1
    Name: country, dtype: int64



리뷰 데이터프레임의 price 컬럼 값에서, price의 평균값을 뺀 값을, centered_price 라고 저장하시오.


```python
centered_price = reviews['price'] - reviews['price'].mean()
```


```python
centered_price
```




    0               NaN
    1        -20.363389
    2        -21.363389
    3        -22.363389
    4         29.636611
                ...    
    129966    -7.363389
    129967    39.636611
    129968    -5.363389
    129969    -3.363389
    129970   -14.363389
    Name: price, Length: 129971, dtype: float64



나는 경제적이므로, 가격대비 포인트가 가장 큰 와인을 사려한다. 해당 와인의 title은?


```python
reviews.head(2)
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Italy</td>
      <td>Aromas include tropical fruit, broom, brimston...</td>
      <td>Vulkà Bianco</td>
      <td>87</td>
      <td>NaN</td>
      <td>Sicily &amp; Sardinia</td>
      <td>Etna</td>
      <td>NaN</td>
      <td>Kerin O’Keefe</td>
      <td>@kerinokeefe</td>
      <td>Nicosia 2013 Vulkà Bianco  (Etna)</td>
      <td>White Blend</td>
      <td>Nicosia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Portugal</td>
      <td>This is ripe and fruity, a wine that is smooth...</td>
      <td>Avidagos</td>
      <td>87</td>
      <td>15.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Quinta dos Avidagos 2011 Avidagos Red (Douro)</td>
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 포인트 / 가격 = 가성비
```


```python
price_point = reviews['points']/reviews['price']
```


```python
reviews.loc[price_point == price_point.max(),]
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>64590</th>
      <td>US</td>
      <td>There's a lot going on in this Merlot, which i...</td>
      <td>NaN</td>
      <td>86</td>
      <td>4.0</td>
      <td>California</td>
      <td>California</td>
      <td>California Other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Bandit NV Merlot (California)</td>
      <td>Merlot</td>
      <td>Bandit</td>
    </tr>
    <tr>
      <th>126096</th>
      <td>Romania</td>
      <td>Notes of sun-dried hay and green flower highli...</td>
      <td>UnWineD</td>
      <td>86</td>
      <td>4.0</td>
      <td>Viile Timisului</td>
      <td>NaN</td>
      <td>Unknown</td>
      <td>Anna Lee C. Iijima</td>
      <td>NaN</td>
      <td>Cramele Recas 2011 UnWineD Pinot Grigio (Viile...</td>
      <td>Pinot Grigio</td>
      <td>Cramele Recas</td>
    </tr>
  </tbody>
</table>
</div>



사람들이 어떤와인을 더 많이 거론했는지 보려한다.

"tropical" 이 들어있는 리뷰의 갯수를 세고, "fruity" 라고 들어있는 리뷰의 갯수를 세어서

판다스 시리즈로 descriptor_counts 변수로 만들어 보자.


```python
def A(strings):
    if 'tropical' in strings:
        return 1
    else:
        return 0
```


```python
A('Aromas include tropical fruit, broom, brimston')
```




    1




```python
tropical_counts = reviews['description'].apply(A)
```


```python
tropical_counts.sum()
```




    3607




```python
def B(strings):
    if 'fruity' in strings:
        return 1
    else:
        return 0
```


```python
furity_counts = reviews['description'].apply(B)
```


```python
furity_counts.sum()
```




    9090




```python
descriptor_counts = pd.Series( data = [3607,9090],index = ['tropical','fruity'])
```


```python
descriptor_counts
```




    tropical    3607
    fruity      9090
    dtype: int64




```python
reviews.head(3)
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Italy</td>
      <td>Aromas include tropical fruit, broom, brimston...</td>
      <td>Vulkà Bianco</td>
      <td>87</td>
      <td>NaN</td>
      <td>Sicily &amp; Sardinia</td>
      <td>Etna</td>
      <td>NaN</td>
      <td>Kerin O’Keefe</td>
      <td>@kerinokeefe</td>
      <td>Nicosia 2013 Vulkà Bianco  (Etna)</td>
      <td>White Blend</td>
      <td>Nicosia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Portugal</td>
      <td>This is ripe and fruity, a wine that is smooth...</td>
      <td>Avidagos</td>
      <td>87</td>
      <td>15.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Quinta dos Avidagos 2011 Avidagos Red (Douro)</td>
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Tart and snappy, the flavors of lime flesh and...</td>
      <td>NaN</td>
      <td>87</td>
      <td>14.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Paul Gregutt</td>
      <td>@paulgwine</td>
      <td>Rainstorm 2013 Pinot Gris (Willamette Valley)</td>
      <td>Pinot Gris</td>
      <td>Rainstorm</td>
    </tr>
  </tbody>
</table>
</div>




```python
# str.contains 를 이용하여 구하기
descrip = reviews['description'].str.replace(",","")
```


```python
reviews['description'].str.contains('fruity').sum()
```




    9090



별점 시스템을 만들려고 한다. 따라서 별점에 대한 데이터가 필요하다.

별점은 1,2,3 즉 3개로 만들것이다.

포인트가 95점 이상이면 3점, 85점 이상이면 2점, 나머지는 1점으로 할 것이다. 

리뷰데이터를 통해 각 데이터의 별점을 구하시오.


```python
def star(point):
    if point >= 95:
        return 3
    elif point >= 85:
        return 2
    else:
        return 1
```


```python
reviews['별점'] = reviews['points'].apply( star )
```


```python
reviews.head(4)
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
      <th>별점</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Italy</td>
      <td>Aromas include tropical fruit, broom, brimston...</td>
      <td>Vulkà Bianco</td>
      <td>87</td>
      <td>NaN</td>
      <td>Sicily &amp; Sardinia</td>
      <td>Etna</td>
      <td>NaN</td>
      <td>Kerin O’Keefe</td>
      <td>@kerinokeefe</td>
      <td>Nicosia 2013 Vulkà Bianco  (Etna)</td>
      <td>White Blend</td>
      <td>Nicosia</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Portugal</td>
      <td>This is ripe and fruity, a wine that is smooth...</td>
      <td>Avidagos</td>
      <td>87</td>
      <td>15.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Quinta dos Avidagos 2011 Avidagos Red (Douro)</td>
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Tart and snappy, the flavors of lime flesh and...</td>
      <td>NaN</td>
      <td>87</td>
      <td>14.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Paul Gregutt</td>
      <td>@paulgwine</td>
      <td>Rainstorm 2013 Pinot Gris (Willamette Valley)</td>
      <td>Pinot Gris</td>
      <td>Rainstorm</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>US</td>
      <td>Pineapple rind, lemon pith and orange blossom ...</td>
      <td>Reserve Late Harvest</td>
      <td>87</td>
      <td>13.0</td>
      <td>Michigan</td>
      <td>Lake Michigan Shore</td>
      <td>NaN</td>
      <td>Alexander Peartree</td>
      <td>NaN</td>
      <td>St. Julian 2013 Reserve Late Harvest Riesling ...</td>
      <td>Riesling</td>
      <td>St. Julian</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
reviews.loc[ reviews['별점'] == 3,].head()
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
      <th>별점</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>345</th>
      <td>Australia</td>
      <td>This wine contains some material over 100 year...</td>
      <td>Rare</td>
      <td>100</td>
      <td>350.0</td>
      <td>Victoria</td>
      <td>Rutherglen</td>
      <td>NaN</td>
      <td>Joe Czerwinski</td>
      <td>@JoeCz</td>
      <td>Chambers Rosewood Vineyards NV Rare Muscat (Ru...</td>
      <td>Muscat</td>
      <td>Chambers Rosewood Vineyards</td>
      <td>3</td>
    </tr>
    <tr>
      <th>346</th>
      <td>Australia</td>
      <td>This deep brown wine smells like a damp, mossy...</td>
      <td>Rare</td>
      <td>98</td>
      <td>350.0</td>
      <td>Victoria</td>
      <td>Rutherglen</td>
      <td>NaN</td>
      <td>Joe Czerwinski</td>
      <td>@JoeCz</td>
      <td>Chambers Rosewood Vineyards NV Rare Muscadelle...</td>
      <td>Muscadelle</td>
      <td>Chambers Rosewood Vineyards</td>
      <td>3</td>
    </tr>
    <tr>
      <th>347</th>
      <td>Germany</td>
      <td>Dusty, saffron-spiced earthiness is juxtaposed...</td>
      <td>Kiedrich Gräfenberg Trockenbeerenauslese</td>
      <td>97</td>
      <td>775.0</td>
      <td>Rheingau</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Anna Lee C. Iijima</td>
      <td>NaN</td>
      <td>Robert Weil 2014 Kiedrich Gräfenberg Trockenbe...</td>
      <td>Riesling</td>
      <td>Robert Weil</td>
      <td>3</td>
    </tr>
    <tr>
      <th>348</th>
      <td>Australia</td>
      <td>Deep mahogany. Dried fig and black tea on the ...</td>
      <td>Grand</td>
      <td>97</td>
      <td>100.0</td>
      <td>Victoria</td>
      <td>Rutherglen</td>
      <td>NaN</td>
      <td>Joe Czerwinski</td>
      <td>@JoeCz</td>
      <td>Chambers Rosewood Vineyards NV Grand Muscat (R...</td>
      <td>Muscat</td>
      <td>Chambers Rosewood Vineyards</td>
      <td>3</td>
    </tr>
    <tr>
      <th>349</th>
      <td>Australia</td>
      <td>RunRig is always complex, and the 2012 doesn't...</td>
      <td>RunRig</td>
      <td>97</td>
      <td>225.0</td>
      <td>South Australia</td>
      <td>Barossa</td>
      <td>NaN</td>
      <td>Joe Czerwinski</td>
      <td>@JoeCz</td>
      <td>Torbreck 2012 RunRig Shiraz-Viognier (Barossa)</td>
      <td>Shiraz-Viognier</td>
      <td>Torbreck</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



리뷰의 region_2 컬럼에 데이터가 비어있는 경우에는, 'Unknown'으로 셋팅하자.


```python
reviews['region_2'].isna().sum()
```




    79460




```python
reviews['region_2'] = reviews['region_2'].fillna('Unknown')
```


```python
reviews.head(5)
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
      <th>country</th>
      <th>description</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>taster_name</th>
      <th>taster_twitter_handle</th>
      <th>title</th>
      <th>variety</th>
      <th>winery</th>
      <th>별점</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Italy</td>
      <td>Aromas include tropical fruit, broom, brimston...</td>
      <td>Vulkà Bianco</td>
      <td>87</td>
      <td>NaN</td>
      <td>Sicily &amp; Sardinia</td>
      <td>Etna</td>
      <td>Unknown</td>
      <td>Kerin O’Keefe</td>
      <td>@kerinokeefe</td>
      <td>Nicosia 2013 Vulkà Bianco  (Etna)</td>
      <td>White Blend</td>
      <td>Nicosia</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Portugal</td>
      <td>This is ripe and fruity, a wine that is smooth...</td>
      <td>Avidagos</td>
      <td>87</td>
      <td>15.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>Unknown</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Quinta dos Avidagos 2011 Avidagos Red (Douro)</td>
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Tart and snappy, the flavors of lime flesh and...</td>
      <td>NaN</td>
      <td>87</td>
      <td>14.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Paul Gregutt</td>
      <td>@paulgwine</td>
      <td>Rainstorm 2013 Pinot Gris (Willamette Valley)</td>
      <td>Pinot Gris</td>
      <td>Rainstorm</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>US</td>
      <td>Pineapple rind, lemon pith and orange blossom ...</td>
      <td>Reserve Late Harvest</td>
      <td>87</td>
      <td>13.0</td>
      <td>Michigan</td>
      <td>Lake Michigan Shore</td>
      <td>Unknown</td>
      <td>Alexander Peartree</td>
      <td>NaN</td>
      <td>St. Julian 2013 Reserve Late Harvest Riesling ...</td>
      <td>Riesling</td>
      <td>St. Julian</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>US</td>
      <td>Much like the regular bottling from 2012, this...</td>
      <td>Vintner's Reserve Wild Child Block</td>
      <td>87</td>
      <td>65.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Paul Gregutt</td>
      <td>@paulgwine</td>
      <td>Sweet Cheeks 2012 Vintner's Reserve Wild Child...</td>
      <td>Pinot Noir</td>
      <td>Sweet Cheeks</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



포인트로 그룹바이하고, 몇개의 데이터가 있는지 카운팅


```python
reviews['points'].value_counts()
```




    88     17207
    87     16933
    90     15410
    86     12600
    89     12226
    91     11359
    92      9613
    85      9530
    93      6489
    84      6480
    94      3758
    83      3025
    82      1836
    95      1535
    81       692
    96       523
    80       397
    97       229
    98        77
    99        33
    100       19
    Name: points, dtype: int64




```python
reviews.groupby('points')['points'].count()
```




    points
    80       397
    81       692
    82      1836
    83      3025
    84      6480
    85      9530
    86     12600
    87     16933
    88     17207
    89     12226
    90     15410
    91     11359
    92      9613
    93      6489
    94      3758
    95      1535
    96       523
    97       229
    98        77
    99        33
    100       19
    Name: points, dtype: int64



포인트별 가격의 최소값을 구해본다.


```python
reviews.groupby('points')['price'].min()
```




    points
    80      5.0
    81      5.0
    82      4.0
    83      4.0
    84      4.0
    85      4.0
    86      4.0
    87      5.0
    88      6.0
    89      7.0
    90      8.0
    91      7.0
    92     11.0
    93     12.0
    94     13.0
    95     20.0
    96     20.0
    97     35.0
    98     50.0
    99     44.0
    100    80.0
    Name: price, dtype: float64



각 국가별로, 가격의 최소값, 최대값 은?


```python
reviews.groupby('country')['price'].agg([np.min,np.max])
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
      <th>amin</th>
      <th>amax</th>
    </tr>
    <tr>
      <th>country</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Argentina</th>
      <td>4.0</td>
      <td>230.0</td>
    </tr>
    <tr>
      <th>Armenia</th>
      <td>14.0</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>Australia</th>
      <td>5.0</td>
      <td>850.0</td>
    </tr>
    <tr>
      <th>Austria</th>
      <td>7.0</td>
      <td>1100.0</td>
    </tr>
    <tr>
      <th>Bosnia and Herzegovina</th>
      <td>12.0</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>Brazil</th>
      <td>10.0</td>
      <td>60.0</td>
    </tr>
    <tr>
      <th>Bulgaria</th>
      <td>8.0</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>Canada</th>
      <td>12.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>Chile</th>
      <td>5.0</td>
      <td>400.0</td>
    </tr>
    <tr>
      <th>China</th>
      <td>18.0</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>Croatia</th>
      <td>12.0</td>
      <td>65.0</td>
    </tr>
    <tr>
      <th>Cyprus</th>
      <td>11.0</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Czech Republic</th>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Egypt</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>England</th>
      <td>25.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>France</th>
      <td>5.0</td>
      <td>3300.0</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>9.0</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>Germany</th>
      <td>5.0</td>
      <td>775.0</td>
    </tr>
    <tr>
      <th>Greece</th>
      <td>8.0</td>
      <td>79.0</td>
    </tr>
    <tr>
      <th>Hungary</th>
      <td>10.0</td>
      <td>764.0</td>
    </tr>
    <tr>
      <th>India</th>
      <td>10.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>Israel</th>
      <td>8.0</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>Italy</th>
      <td>5.0</td>
      <td>900.0</td>
    </tr>
    <tr>
      <th>Lebanon</th>
      <td>13.0</td>
      <td>75.0</td>
    </tr>
    <tr>
      <th>Luxembourg</th>
      <td>16.0</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>Macedonia</th>
      <td>15.0</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>Mexico</th>
      <td>8.0</td>
      <td>108.0</td>
    </tr>
    <tr>
      <th>Moldova</th>
      <td>8.0</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>Morocco</th>
      <td>14.0</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>New Zealand</th>
      <td>7.0</td>
      <td>130.0</td>
    </tr>
    <tr>
      <th>Peru</th>
      <td>10.0</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>Portugal</th>
      <td>5.0</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>Romania</th>
      <td>4.0</td>
      <td>320.0</td>
    </tr>
    <tr>
      <th>Serbia</th>
      <td>15.0</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>Slovakia</th>
      <td>16.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>Slovenia</th>
      <td>7.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>South Africa</th>
      <td>5.0</td>
      <td>330.0</td>
    </tr>
    <tr>
      <th>Spain</th>
      <td>4.0</td>
      <td>770.0</td>
    </tr>
    <tr>
      <th>Switzerland</th>
      <td>21.0</td>
      <td>160.0</td>
    </tr>
    <tr>
      <th>Turkey</th>
      <td>14.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>US</th>
      <td>4.0</td>
      <td>2013.0</td>
    </tr>
    <tr>
      <th>Ukraine</th>
      <td>6.0</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>Uruguay</th>
      <td>10.0</td>
      <td>130.0</td>
    </tr>
  </tbody>
</table>
</div>


