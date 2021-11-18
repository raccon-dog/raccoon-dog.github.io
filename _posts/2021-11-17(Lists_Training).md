# PYTHON PROGRAMMING 기초

# LISTS
- 데이터를 여러 개 저장하는데 사용합니다.
- 순서가 있습니다. 즉, 인덱스를 가지고 있습니다.
- 값을 바꿀 수 있습니다. 즉, mutable 이라고 합니다.


## 리스트 만들기


```python
List = [1,2,3,4,5,6,7]
```


```python
List
```




    [1, 2, 3, 4, 5, 6, 7]



# 데이터 억세스의 대괄호는, 변수명 바로 오른쪽에 나오는것

# 리스트의 대괄호는, 대괄호로 바로 시작.


```python
week = ['Mon','Tue','Wed','Thu','Fri']
```


```python
week
```




    ['Mon', 'Tue', 'Wed', 'Thu', 'Fri']




```python
[5,6,1,2,9]
```




    [5, 6, 1, 2, 9]



## 여러 종류의 데이터를, 하나의 리스트에 저장 가능함


```python
[2, 'Mitch', 3.14]
```




    [2, 'Mitch', 3.14]




```python
[2,'Mitch',3.14 ,[3,4,5]]
```




    [2, 'Mitch', 3.14, [3, 4, 5]]



## 리스트 offset 으로 값을 얻기


```python
week
```




    ['Mon', 'Tue', 'Wed', 'Thu', 'Fri']




```python
week[1:4]
```




    ['Tue', 'Wed', 'Thu']




```python
week[4]
```




    'Fri'



### 리스트 안에 있는 리스트의 값을 얻기 


```python
my_list = ['Mitch',[3,6,7],['yellow',5,6]]
```


```python
my_list[1][1
          ]
```




    6




```python
my_list[2][0][5]
```




    'w'



## offset 으로, 리스트 안에 있는 값을 바꾸기


```python
week
```




    ['Mon', 'Tue', 'Wed', 'Thu', 'Fri']



# 'Mon'을 'Sun'으로 변경 


```python
week[0] = 'Sun'
```


```python
week
```




    ['Sun', 'Tue', 'Wed', 'Thu', 'Fri']



## 리스트에 항목을 추가하기


```python
week
```




    ['Sun', 'Tue', 'Wed', 'Thu', 'Fri']



# 리스트의 맨 뒤에 데이터를 저장 'Sat' 


```python
week.append('Sat')
```


```python
week
```




    ['Sun', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']



# 내가 원하는 위치에 데이터를 추가. 'Mon' 추가 


```python
week.insert(1,'Mon')
```


```python
week
```




    ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']



## 항목을 삭제하기


```python
week
```




    ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']




```python
del week[1]
```


```python
week
```




    ['Sun', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']




```python
week.remove('Thu')
```


```python
week
```




    ['Sun', 'Tue', 'Wed', 'Fri', 'Sat']



# 삭제 3. pop함수를 이용한 삭제. 삭제하면서, 삭제된 데이터를 가져온다.


```python
week.pop()
```




    'Sat'




```python
week
```




    ['Sun', 'Tue', 'Wed', 'Fri']




```python
week.pop(1)
```




    'Tue'




```python
week
```




    ['Sun', 'Wed', 'Fri']



## 리스트 + 연산


```python
list()
```




    []




```python
fruits = list()
```


```python
fruits
```




    []




```python
fruits.append('Apple')
```


```python
fruits.append('Banana')
```


```python
fruits
```




    ['Apple', 'Banana']




```python
others = ['Mango','Coconut','Orange','Lemon']
```


```python
fruits
```




    ['Apple', 'Banana']




```python
others
```




    ['Mango', 'Coconut', 'Orange', 'Lemon']




```python
fruits = fruits + others
```


```python
fruits
```




    ['Apple', 'Banana', 'Mango', 'Coconut', 'Orange', 'Lemon']



## 값으로 오프셋 찾기


```python
fruits.index('Coconut')
```




    3



## 리스트 안에, 원하는 값이 있는지 확인하기


```python
'Guava' in fruits
```




    False




```python
'Mango' in fruits
```




    True



## 리스트에 들어있는 값들 중, 원하는 값이 몇개가 있는지 갯수 세기


```python
fruits.count('Mango')
```




    1



## 리스트에 들어있는 항목들의 전체 갯수 세기


```python
fruits
```




    ['Apple', 'Banana', 'Mango', 'Coconut', 'Orange', 'Lemon']




```python
len(fruits)
```




    6



## 항목들을 정렬하기
- 원래의 리스트 자체는 건들지 않고, 새롭게 정렬한 리스트를 반환하는 경우 : sorted()
- 원래의 리스트 자체를 정렬해서 변경하는 경우 : sort()


```python
fruits
```




    ['Apple', 'Banana', 'Mango', 'Coconut', 'Orange', 'Lemon']




```python
sorted(fruits)
```




    ['Apple', 'Banana', 'Coconut', 'Lemon', 'Mango', 'Orange']




```python
sorted(fruits, reverse=True)
```




    ['Orange', 'Mango', 'Lemon', 'Coconut', 'Banana', 'Apple']




```python
fruits
```




    ['Apple', 'Banana', 'Mango', 'Coconut', 'Orange', 'Lemon']




```python
fruits.sort()
```


```python
fruits
```




    ['Apple', 'Banana', 'Coconut', 'Lemon', 'Mango', 'Orange']




```python
fruits.sort(reverse=True)
```


```python
fruits
```




    ['Orange', 'Mango', 'Lemon', 'Coconut', 'Banana', 'Apple']



### 따라서 원본 변경 없이, 내 리스트만 카피해서 변경하기.


```python
sorted(fruits)
```




    ['Apple', 'Banana', 'Coconut', 'Lemon', 'Mango', 'Orange']


