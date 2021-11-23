---
layout : single
title : "파이썬 - Pandas 실습 -2 "
categories: Coding_Training
tag : [Python,Pandas]
author_profile: false
sidebar:
    nav: "docs"
---
winemag-data.csv 파일을 reviews 로 읽는다.


```python
import pandas as pd
```


```python
reviews = pd.read_csv("winemag-data.csv",index_col = 0)
```

인덱스를 title 컬럼으로 셋팅한다.


```python
# reviews.set_index('title', inplace=True)
reviews = reviews.set_index('title')
```

먼저 데이터가 비어있느것이 있는지 확인한다.


```python
reviews.isna().sum()
```




    country                     63
    description                  0
    designation              37465
    points                       0
    price                     8996
    province                    63
    region_1                 21247
    region_2                 79460
    taster_name              26244
    taster_twitter_handle    31213
    variety                      1
    winery                       0
    dtype: int64



그리고나서, 가격이 없는 데이터는 빼고, 데이터셋을 가져온다.


```python
data_set = reviews.dropna(subset=['price'])
data_set.head()
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
      <th>variety</th>
      <th>winery</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Quinta dos Avidagos 2011 Avidagos Red (Douro)</th>
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
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
    </tr>
    <tr>
      <th>Rainstorm 2013 Pinot Gris (Willamette Valley)</th>
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
      <td>Pinot Gris</td>
      <td>Rainstorm</td>
    </tr>
    <tr>
      <th>St. Julian 2013 Reserve Late Harvest Riesling (Lake Michigan Shore)</th>
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
      <td>Riesling</td>
      <td>St. Julian</td>
    </tr>
    <tr>
      <th>Sweet Cheeks 2012 Vintner's Reserve Wild Child Block Pinot Noir (Willamette Valley)</th>
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
      <td>Pinot Noir</td>
      <td>Sweet Cheeks</td>
    </tr>
    <tr>
      <th>Tandem 2011 Ars In Vitro Tempranillo-Merlot (Navarra)</th>
      <td>Spain</td>
      <td>Blackberry and raspberry aromas show a typical...</td>
      <td>Ars In Vitro</td>
      <td>87</td>
      <td>15.0</td>
      <td>Northern Spain</td>
      <td>Navarra</td>
      <td>NaN</td>
      <td>Michael Schachner</td>
      <td>@wineschach</td>
      <td>Tempranillo-Merlot</td>
      <td>Tandem</td>
    </tr>
  </tbody>
</table>
</div>




```python
reviews.shape
```




    (129971, 12)



리뷰에 새로운 컬럼 critic 만들고, everyone 이라고 값 넣는다.


```python
reviews['critic'] = 'everyone'
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
      <th>variety</th>
      <th>winery</th>
      <th>critic</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Nicosia 2013 Vulkà Bianco  (Etna)</th>
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
      <td>White Blend</td>
      <td>Nicosia</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Quinta dos Avidagos 2011 Avidagos Red (Douro)</th>
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
      <td>Portuguese Red</td>
      <td>Quinta dos Avidagos</td>
      <td>everyone</td>
    </tr>
  </tbody>
</table>
</div>



리뷰의 포인트 컬럼은 수치로 되어있다. 이 컬럼의 기초통계데이터를 확인하시오. (평균, 최대 최소 등)


```python
reviews["points"].describe()
```




    count    129971.000000
    mean         88.447138
    std           3.039730
    min          80.000000
    25%          86.000000
    50%          88.000000
    75%          91.000000
    max         100.000000
    Name: points, dtype: float64



점수를 100점 맞은 와인의 데이터를 가져오시오.  


```python
wine_data = reviews.loc[reviews['points'] == 100,]
```


```python
wine_data.head()
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
      <th>variety</th>
      <th>winery</th>
      <th>critic</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Chambers Rosewood Vineyards NV Rare Muscat (Rutherglen)</th>
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
      <td>Muscat</td>
      <td>Chambers Rosewood Vineyards</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Avignonesi 1995 Occhio di Pernice  (Vin Santo di Montepulciano)</th>
      <td>Italy</td>
      <td>Thick as molasses and dark as caramelized brow...</td>
      <td>Occhio di Pernice</td>
      <td>100</td>
      <td>210.0</td>
      <td>Tuscany</td>
      <td>Vin Santo di Montepulciano</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Prugnolo Gentile</td>
      <td>Avignonesi</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Krug 2002 Brut  (Champagne)</th>
      <td>France</td>
      <td>This is a fabulous wine from the greatest Cham...</td>
      <td>Brut</td>
      <td>100</td>
      <td>259.0</td>
      <td>Champagne</td>
      <td>Champagne</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Champagne Blend</td>
      <td>Krug</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Tenuta dell'Ornellaia 2007 Masseto Merlot (Toscana)</th>
      <td>Italy</td>
      <td>A perfect wine from a classic vintage, the 200...</td>
      <td>Masseto</td>
      <td>100</td>
      <td>460.0</td>
      <td>Tuscany</td>
      <td>Toscana</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Merlot</td>
      <td>Tenuta dell'Ornellaia</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Casa Ferreirinha 2008 Barca-Velha Red (Douro)</th>
      <td>Portugal</td>
      <td>This is the latest release of what has long be...</td>
      <td>Barca-Velha</td>
      <td>100</td>
      <td>450.0</td>
      <td>Douro</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Roger Voss</td>
      <td>@vossroger</td>
      <td>Portuguese Red</td>
      <td>Casa Ferreirinha</td>
      <td>everyone</td>
    </tr>
  </tbody>
</table>
</div>



taster_name 컬럼은 사람 이름으로 되어있다. 몇명의 사람들이 평가를 한것인까?


```python
# unique의 수.
reviews['taster_name'].describe()
```




    count         103727
    unique            19
    top       Roger Voss
    freq           25514
    Name: taster_name, dtype: object



리뷰 포인트의 평균을 구하시오


```python
reviews["points"].mean()
```




    88.44713820775404



테스터들의 이름을 전부 확인하시오


```python
reviews["taster_name"].unique()
```




    array(['Kerin O’Keefe', 'Roger Voss', 'Paul Gregutt',
           'Alexander Peartree', 'Michael Schachner', 'Anna Lee C. Iijima',
           'Virginie Boone', 'Matt Kettmann', nan, 'Sean P. Sullivan',
           'Jim Gordon', 'Joe Czerwinski', 'Anne Krebiehl\xa0MW',
           'Lauren Buzzeo', 'Mike DeSimone', 'Jeff Jenssen',
           'Susan Kostrzewa', 'Carrie Dykes', 'Fiona Adams',
           'Christina Pickard'], dtype=object)



각 테스터들은, 각각 몇개의 와인을 테스트 했는지 확인하시오. ( 테스터 이름, 갯수 )


```python
reviews['taster_name'].value_counts()
```




    Roger Voss            25514
    Michael Schachner     15134
    Kerin O’Keefe         10776
    Virginie Boone         9537
    Paul Gregutt           9532
    Matt Kettmann          6332
    Joe Czerwinski         5147
    Sean P. Sullivan       4966
    Anna Lee C. Iijima     4415
    Jim Gordon             4177
    Anne Krebiehl MW       3685
    Lauren Buzzeo          1835
    Susan Kostrzewa        1085
    Mike DeSimone           514
    Jeff Jenssen            491
    Alexander Peartree      415
    Carrie Dykes            139
    Fiona Adams              27
    Christina Pickard         6
    Name: taster_name, dtype: int64



리뷰의 포인트의 평균을 구하고, 리뷰의 포인트값이, 평균보다 큰 데이터 (즉, 평가가 좋은 와인) 만 가져오시오.


```python
good_wine = reviews['points']> reviews['points'].mean()
```


```python
reviews.loc[good_wine, ].head()
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
      <th>variety</th>
      <th>winery</th>
      <th>critic</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Dopff &amp; Irion 2004 Schoenenbourg Grand Cru Vendanges Tardives Riesling (Alsace)</th>
      <td>France</td>
      <td>Medium-gold in color. Complex and inviting nos...</td>
      <td>Schoenenbourg Grand Cru Vendanges Tardives</td>
      <td>92</td>
      <td>80.0</td>
      <td>Alsace</td>
      <td>Alsace</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Riesling</td>
      <td>Dopff &amp; Irion</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Ceretto 2003 Bricco Rocche Prapó  (Barolo)</th>
      <td>Italy</td>
      <td>Slightly backward, particularly given the vint...</td>
      <td>Bricco Rocche Prapó</td>
      <td>92</td>
      <td>70.0</td>
      <td>Piedmont</td>
      <td>Barolo</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Nebbiolo</td>
      <td>Ceretto</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Matrix 2007 Stuhlmuller Vineyard Chardonnay (Alexander Valley)</th>
      <td>US</td>
      <td>The vineyard is one of the better Chardonnay s...</td>
      <td>Stuhlmuller Vineyard</td>
      <td>92</td>
      <td>36.0</td>
      <td>California</td>
      <td>Alexander Valley</td>
      <td>Sonoma</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Chardonnay</td>
      <td>Matrix</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Mauritson 2007 Rockpile Cemetary Vineyard Zinfandel (Rockpile)</th>
      <td>US</td>
      <td>Defines Rockpile Zinfandel in intensity of fru...</td>
      <td>Rockpile Cemetary Vineyard</td>
      <td>92</td>
      <td>39.0</td>
      <td>California</td>
      <td>Rockpile</td>
      <td>Sonoma</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Zinfandel</td>
      <td>Mauritson</td>
      <td>everyone</td>
    </tr>
    <tr>
      <th>Henry's Drive Vignerons 2006 Parson's Flat Shiraz-Cabernet Sauvignon (Padthaway)</th>
      <td>Australia</td>
      <td>The blend is roughly two-thirds Shiraz and one...</td>
      <td>Parson's Flat</td>
      <td>92</td>
      <td>40.0</td>
      <td>South Australia</td>
      <td>Padthaway</td>
      <td>NaN</td>
      <td>Joe Czerwinski</td>
      <td>@JoeCz</td>
      <td>Shiraz-Cabernet Sauvignon</td>
      <td>Henry's Drive Vignerons</td>
      <td>everyone</td>
    </tr>
  </tbody>
</table>
</div>


