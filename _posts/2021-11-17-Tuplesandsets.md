---
layout : single
title : "파이썬 - 자료형구조(튜플) "
categories: Coding_Class
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# PYTHON PROGRAMMING FUNDAMENTALS
# TUPLES AND SETS

# TUPLES 

- Immutable Python objects. 
- 튜플은 시퀀스, 즉 순서가 있습니다. 
- 튜플은 괄호 ( ) 를 사용합니다. 


```python
()
```




    ()




```python
tuple()
```




    ()




```python
my_tuple = (1,'a',3.14)
```


```python
my_tuple[2]
```




    3.14



# SETS
- 셋에 들어있는 데이터는 순서가 없습니다.
- 셋에는 동일한 값이 저장되지 않습니다. 우리가 배웠던 집합과 같습니다. 
- 셋은 중괄호 { } 로 정의합니다. 


```python
empty_set = {}
```


```python
empty_set2 = set()
```


```python
type(empty_set)
```




    dict




```python
type(empty_set2)
```




    set




```python
{1, 5, 2, 5, 6, 10, 15, 9, 1, 1, 5}
```




    {1, 2, 5, 6, 9, 10, 15}




```python
page_view = [1,1,1,5,7,2,100,5,9,3,22,48,55,3,4,1005,5,9,7,9,4,8,5,2,3,6,8,7,4,56,4,89,7]
```


```python
page_view = set(page_view)
```


```python
page_view
```




    {1, 2, 3, 4, 5, 6, 7, 8, 9, 22, 48, 55, 56, 89, 100, 1005}




```python
len(page_view)
```




    16




```python
event_A = {3,5,1,7,9,2}
```


```python
event_B = {8, 4, 2, 1, 9, 5, 11}
```

###  set 의 연산자와 값의 추가,삭제


```python
event_A | event_B
```




    {1, 2, 3, 4, 5, 7, 8, 9, 11}




```python
event_A & event_B
```




    {1, 2, 5, 9}




```python
event_A - event_B
```




    {3, 7}




```python
event_A.add(15)
```


```python
event_A
```




    {1, 2, 3, 5, 7, 9, 15}




```python
event_A.discard(3)
```


```python
event_A
```




    {1, 2, 5, 7, 9, 15}


