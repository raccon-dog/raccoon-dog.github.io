---
layout : single
title : "파이썬 - 자료형구조(딕셔너리) "
categories: Coding_Class
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# PYTHON PROGRAMMING 기초
# DICTIONARIES AND BOOLEANS

# DICTIONARIES

- my_dict = {'key1':'value1', 'key2':'value2', 'key3':'value3'}
- 딕쳐너리는 키 밸류의 쌍으로 되어 있다. 
- 키는, 딕셔너리 안에 유일한 값으로 되어 있다. 따라서 키가 같은 값을 가질 수 없다. 그러나 밸류는 같은 값이 여러개 있어도 상관없다.
- 리스트는 인덱스의 오프셋으로 접근하지만, 딕셔너리는 키로 접근한다.


```python
dict()
```




    {}




```python
my_phone = {'brand' : 'apple','model' : 'iphone X', 'year' : 2018}
```


```python
my_phone
```




    {'brand': 'apple', 'model': 'iphone X', 'year': 2018}



# 한쌍 : item , 아이템 왼쪽은 key , 오른쪽은 value 


```python
my_phone['brand']
```




    'apple'




```python
my_phone['model']
```




    'iphone X'




```python
my_phone['year']
```




    2018




```python
my_phone.get('brand')
```




    'apple'




```python
my_phone.get('color')
```




    'red'




```python
my_phone
```




    {'brand': 'apple', 'model': 'iphone X', 'year': 2018}




```python
my_phone['model'] = "iphone 12"
```


```python
my_phone
```




    {'brand': 'apple', 'model': 'iphone 12', 'year': 2018}




```python
my_phone['year'] = 2021
```


```python
my_phone
```




    {'brand': 'apple', 'model': 'iphone 12', 'year': 2021}




```python
my_phone['color'] = 'red'
```


```python
my_phone
```




    {'brand': 'apple', 'model': 'iphone 12', 'year': 2021, 'color': 'red'}




```python
del my_phone['model']
```


```python
my_phone
```




    {'brand': 'apple', 'year': 2021, 'color': 'red'}



### 키,벨류로 매칭값 찾기


```python
my_phone.keys()
```




    dict_keys(['brand', 'year', 'color'])




```python
my_phone.values()
```




    dict_values(['apple', 2021, 'red'])




```python
my_phone.items()
```




    dict_items([('brand', 'apple'), ('year', 2021), ('color', 'red')])



### 항목 찾기


```python
'brand' in my_phone
```




    True




```python
'brand' not in my_phone
```




    False




```python
'apple' in my_phone.values()
```




    True



### clear() 함수 호출을 이용하여 내용지우기


```python
my_list = [1,2,3,4,5]
```


```python
my_list.clear()
```


```python
my_list
```




    []




```python
my_phone.clear()
```


```python
my_phone
```




    {}



# BOOLEANS 
- Boolean 은 다음 2가지의 오브젝트로 나타낸다. "False" and "True". 
- 숫자 0과 1과 같은 의미이다. 



```python
True or False
```




    True


