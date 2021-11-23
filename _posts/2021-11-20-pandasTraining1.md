winemag-data_first150k.csv 파일을 reviews 로 읽는다.



```python
import pandas as pd
```


```python
reviews = pd.read_csv('winemag-data_first150k.csv',index_col = 0)
```


```python
reviews = pd.DataFrame(reviews)
```


```python
reviews.head()
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
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>US</td>
      <td>This tremendous 100% varietal wine hails from ...</td>
      <td>Martha's Vineyard</td>
      <td>96</td>
      <td>235.0</td>
      <td>California</td>
      <td>Napa Valley</td>
      <td>Napa</td>
      <td>Cabernet Sauvignon</td>
      <td>Heitz</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>Ripe aromas of fig, blackberry and cassis are ...</td>
      <td>Carodorum Selección Especial Reserva</td>
      <td>96</td>
      <td>110.0</td>
      <td>Northern Spain</td>
      <td>Toro</td>
      <td>NaN</td>
      <td>Tinta de Toro</td>
      <td>Bodega Carmen Rodríguez</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Mac Watson honors the memory of a wine once ma...</td>
      <td>Special Selected Late Harvest</td>
      <td>96</td>
      <td>90.0</td>
      <td>California</td>
      <td>Knights Valley</td>
      <td>Sonoma</td>
      <td>Sauvignon Blanc</td>
      <td>Macauley</td>
    </tr>
    <tr>
      <th>3</th>
      <td>US</td>
      <td>This spent 20 months in 30% new French oak, an...</td>
      <td>Reserve</td>
      <td>96</td>
      <td>65.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Pinot Noir</td>
      <td>Ponzi</td>
    </tr>
    <tr>
      <th>4</th>
      <td>France</td>
      <td>This is the top wine from La Bégude, named aft...</td>
      <td>La Brûlade</td>
      <td>95</td>
      <td>66.0</td>
      <td>Provence</td>
      <td>Bandol</td>
      <td>NaN</td>
      <td>Provence red blend</td>
      <td>Domaine de la Bégude</td>
    </tr>
  </tbody>
</table>
</div>



리뷰의 디스크립션 컬럼을 desc 로 저장한다.



```python
reviews = reviews.rename(columns = {'description':'desc'})
```


```python
reviews.head()
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
      <th>desc</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>US</td>
      <td>This tremendous 100% varietal wine hails from ...</td>
      <td>Martha's Vineyard</td>
      <td>96</td>
      <td>235.0</td>
      <td>California</td>
      <td>Napa Valley</td>
      <td>Napa</td>
      <td>Cabernet Sauvignon</td>
      <td>Heitz</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>Ripe aromas of fig, blackberry and cassis are ...</td>
      <td>Carodorum Selección Especial Reserva</td>
      <td>96</td>
      <td>110.0</td>
      <td>Northern Spain</td>
      <td>Toro</td>
      <td>NaN</td>
      <td>Tinta de Toro</td>
      <td>Bodega Carmen Rodríguez</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Mac Watson honors the memory of a wine once ma...</td>
      <td>Special Selected Late Harvest</td>
      <td>96</td>
      <td>90.0</td>
      <td>California</td>
      <td>Knights Valley</td>
      <td>Sonoma</td>
      <td>Sauvignon Blanc</td>
      <td>Macauley</td>
    </tr>
    <tr>
      <th>3</th>
      <td>US</td>
      <td>This spent 20 months in 30% new French oak, an...</td>
      <td>Reserve</td>
      <td>96</td>
      <td>65.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Pinot Noir</td>
      <td>Ponzi</td>
    </tr>
    <tr>
      <th>4</th>
      <td>France</td>
      <td>This is the top wine from La Bégude, named aft...</td>
      <td>La Brûlade</td>
      <td>95</td>
      <td>66.0</td>
      <td>Provence</td>
      <td>Bandol</td>
      <td>NaN</td>
      <td>Provence red blend</td>
      <td>Domaine de la Bégude</td>
    </tr>
  </tbody>
</table>
</div>



first_description 이라는 변수에는, 디스크립션 컬럼의 첫번째 데이터를 저장한다.



```python
first_description = reviews['desc'][0]
```


```python
first_description
```




    'This tremendous 100% varietal wine hails from Oakville and was aged over three years in oak. Juicy red-cherry fruit and a compelling hint of caramel greet the palate, framed by elegant, fine tannins and a subtle minty tone in the background. Balanced and rewarding from start to finish, it has years ahead of it to develop further nuance. Enjoy 2022–2030.'



first_row 라는 변수에, 첫번째 리뷰 데이터(행)를 저장한다.



```python
first_row = reviews.iloc[0,]
```


```python
first_row
```




    country                                                       US
    desc           This tremendous 100% varietal wine hails from ...
    designation                                    Martha's Vineyard
    points                                                        96
    price                                                      235.0
    province                                              California
    region_1                                             Napa Valley
    region_2                                                    Napa
    variety                                       Cabernet Sauvignon
    winery                                                     Heitz
    Name: 0, dtype: object



리뷰의 description column 의 값들 중, 첫번째부터 10번째 데이터까지를 first_descriptions 변수에 저장한다.



```python
first_description = reviews['desc'][:10]
```


```python
first_description
```




    0    This tremendous 100% varietal wine hails from ...
    1    Ripe aromas of fig, blackberry and cassis are ...
    2    Mac Watson honors the memory of a wine once ma...
    3    This spent 20 months in 30% new French oak, an...
    4    This is the top wine from La Bégude, named aft...
    5    Deep, dense and pure from the opening bell, th...
    6    Slightly gritty black-fruit aromas include a s...
    7    Lush cedary black-fruit aromas are luxe and of...
    8    This re-named vineyard was formerly bottled as...
    9    The producer sources from two blocks of the vi...
    Name: desc, dtype: object



리뷰에서 인덱스가 1, 2, 3, 5, 8 인 데이터를,  sample_reviews 변수에 저장한다.


```python
sample_reviews = reviews.iloc[[1,2,3,5,8], ]
sample_reviews
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
      <th>desc</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>Ripe aromas of fig, blackberry and cassis are ...</td>
      <td>Carodorum Selección Especial Reserva</td>
      <td>96</td>
      <td>110.0</td>
      <td>Northern Spain</td>
      <td>Toro</td>
      <td>NaN</td>
      <td>Tinta de Toro</td>
      <td>Bodega Carmen Rodríguez</td>
    </tr>
    <tr>
      <th>2</th>
      <td>US</td>
      <td>Mac Watson honors the memory of a wine once ma...</td>
      <td>Special Selected Late Harvest</td>
      <td>96</td>
      <td>90.0</td>
      <td>California</td>
      <td>Knights Valley</td>
      <td>Sonoma</td>
      <td>Sauvignon Blanc</td>
      <td>Macauley</td>
    </tr>
    <tr>
      <th>3</th>
      <td>US</td>
      <td>This spent 20 months in 30% new French oak, an...</td>
      <td>Reserve</td>
      <td>96</td>
      <td>65.0</td>
      <td>Oregon</td>
      <td>Willamette Valley</td>
      <td>Willamette Valley</td>
      <td>Pinot Noir</td>
      <td>Ponzi</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Spain</td>
      <td>Deep, dense and pure from the opening bell, th...</td>
      <td>Numanthia</td>
      <td>95</td>
      <td>73.0</td>
      <td>Northern Spain</td>
      <td>Toro</td>
      <td>NaN</td>
      <td>Tinta de Toro</td>
      <td>Numanthia</td>
    </tr>
    <tr>
      <th>8</th>
      <td>US</td>
      <td>This re-named vineyard was formerly bottled as...</td>
      <td>Silice</td>
      <td>95</td>
      <td>65.0</td>
      <td>Oregon</td>
      <td>Chehalem Mountains</td>
      <td>Willamette Valley</td>
      <td>Pinot Noir</td>
      <td>Bergström</td>
    </tr>
  </tbody>
</table>
</div>



df 라는 변수에, 다음 조건을 만족하는 데이터프레임을 저장하시오. 
인덱스가 0, 1, 10, 100 인 데이터에서, 컬럼이 country, province, region_1, region_2 인 데이터들만 가져와서 저장하시오.


```python
sample = reviews.iloc[[0,1,10,100], ]
```


```python
df = sample[["country","province","region_1","region_2"]]
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
      <th>country</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>US</td>
      <td>California</td>
      <td>Napa Valley</td>
      <td>Napa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Spain</td>
      <td>Northern Spain</td>
      <td>Toro</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Italy</td>
      <td>Northeastern Italy</td>
      <td>Collio</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>100</th>
      <td>US</td>
      <td>California</td>
      <td>South Coast</td>
      <td>South Coast</td>
    </tr>
  </tbody>
</table>
</div>



Italy 에서 만들어진 와인에 대해서 italian_wines 이라는 이름으로 데이터프레임을 만드시오. 



```python
is_Italy = reviews['country'] == 'Italy'
```


```python
iitalian_wines = reviews[is_Italy]
```


```python
iitalian_wines.head()
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
      <th>desc</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10</th>
      <td>Italy</td>
      <td>Elegance, complexity and structure come togeth...</td>
      <td>Ronco della Chiesa</td>
      <td>95</td>
      <td>80.0</td>
      <td>Northeastern Italy</td>
      <td>Collio</td>
      <td>NaN</td>
      <td>Friulano</td>
      <td>Borgo del Tiglio</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Italy</td>
      <td>Underbrush, scorched earth, menthol and plum s...</td>
      <td>Vigna Piaggia</td>
      <td>90</td>
      <td>NaN</td>
      <td>Tuscany</td>
      <td>Brunello di Montalcino</td>
      <td>NaN</td>
      <td>Sangiovese</td>
      <td>Abbadia Ardenga</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Italy</td>
      <td>Forest floor, tilled soil, mature berry and a ...</td>
      <td>Riserva</td>
      <td>90</td>
      <td>135.0</td>
      <td>Tuscany</td>
      <td>Brunello di Montalcino</td>
      <td>NaN</td>
      <td>Sangiovese</td>
      <td>Carillon</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Italy</td>
      <td>Aromas of forest floor, violet, red berry and ...</td>
      <td>NaN</td>
      <td>90</td>
      <td>29.0</td>
      <td>Tuscany</td>
      <td>Vino Nobile di Montepulciano</td>
      <td>NaN</td>
      <td>Sangiovese</td>
      <td>Avignonesi</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Italy</td>
      <td>This has a charming nose that boasts rose, vio...</td>
      <td>NaN</td>
      <td>90</td>
      <td>23.0</td>
      <td>Tuscany</td>
      <td>Chianti Classico</td>
      <td>NaN</td>
      <td>Sangiovese</td>
      <td>Casina di Cornia</td>
    </tr>
  </tbody>
</table>
</div>



리뷰점수가 95점 이상이고, Australia와 New Zealand 에서 만들어진 와인에 대한 데이터프레임을 top_oceania_wines 이라는 이름의 변수로 저장.



```python
is_point = reviews['points'] >= 95
```


```python
is_New = reviews['country'] == "New Zealand"
```


```python
is_Aus = reviews['country'] == "Australia"
```


```python
condition = is_point&(is_Aus|is_New)
```


```python
top_oceania_wines = reviews.loc[condition ,]
```


```python
# reviews['country'].isin(["Australia","New Zealand"])

```


```python
top_oceania_wines.head()
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
      <th>desc</th>
      <th>designation</th>
      <th>points</th>
      <th>price</th>
      <th>province</th>
      <th>region_1</th>
      <th>region_2</th>
      <th>variety</th>
      <th>winery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2148</th>
      <td>Australia</td>
      <td>Full-bodied and plush yet vibrant and imbued w...</td>
      <td>The Factor</td>
      <td>98</td>
      <td>125.0</td>
      <td>South Australia</td>
      <td>Barossa Valley</td>
      <td>NaN</td>
      <td>Shiraz</td>
      <td>Torbreck</td>
    </tr>
    <tr>
      <th>2458</th>
      <td>Australia</td>
      <td>This is a top example of the classic Australia...</td>
      <td>The Peake</td>
      <td>96</td>
      <td>150.0</td>
      <td>South Australia</td>
      <td>McLaren Vale</td>
      <td>NaN</td>
      <td>Cabernet-Shiraz</td>
      <td>Hickinbotham</td>
    </tr>
    <tr>
      <th>3033</th>
      <td>Australia</td>
      <td>This Cabernet equivalent to Grange has explode...</td>
      <td>Bin 707</td>
      <td>95</td>
      <td>500.0</td>
      <td>South Australia</td>
      <td>South Australia</td>
      <td>NaN</td>
      <td>Cabernet Sauvignon</td>
      <td>Penfolds</td>
    </tr>
    <tr>
      <th>3044</th>
      <td>Australia</td>
      <td>From vines planted in 1912, this has been an i...</td>
      <td>Mount Edelstone Vineyard</td>
      <td>95</td>
      <td>200.0</td>
      <td>South Australia</td>
      <td>Eden Valley</td>
      <td>NaN</td>
      <td>Shiraz</td>
      <td>Henschke</td>
    </tr>
    <tr>
      <th>3047</th>
      <td>Australia</td>
      <td>This is a throwback to those brash, flavor-exu...</td>
      <td>One</td>
      <td>95</td>
      <td>95.0</td>
      <td>South Australia</td>
      <td>Langhorne Creek</td>
      <td>NaN</td>
      <td>Red Blend</td>
      <td>Heartland</td>
    </tr>
  </tbody>
</table>
</div>


