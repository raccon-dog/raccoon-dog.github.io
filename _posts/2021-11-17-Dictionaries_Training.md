---
layout : single
title : "파이썬 - 딕셔너리 실습 "
categories: Coding_Training
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# <font color='red'> *실습* </font> 
# <font color='red'> DICTIONARIES AND BOOLEANS </font> 

# <font color='blue'> 1. 밸류들을 전부 곱한 값을 출력하는 코드를 만드세요. </font>


```python
my_dict = {'data1':500,
           'data2':-10,
           'data3':300}

```


```python
my_dict['data1']*my_dict['data2']*my_dict['data3']
```




    -1500000



# <font color='blue'> 2. 각 학생별로, 중간과 기말의 평균점수를 구하세요.  


```python
student_details = [
  {'student_id' : 1, 'subject' : 'math', 'midterm' : 60, 'final' : 85},
  {'student_id' : 2, 'subject' : 'math', 'midterm' : 80, 'final' : 78},
  {'student_id' : 3, 'subject' : 'math', 'midterm' : 90, 'final' : 85}
]

```


```python
average_midterm = (student_details[0]['midterm'] + student_details[1]['midterm'] + student_details[2]['midterm']) / len(student_details)
average_final = (student_details[0]['final'] + student_details[1]['final'] + student_details[2]['final']) / len(student_details)
```


```python
print(average_midterm)
print(average_final)
```

    76.66666666666667
    82.66666666666667
    

# <font color='blue'> 3. 위에서 구한 평균점수를,"AVERAGE" 라는 키를 새로 만들어서, 각 학생의 딕셔너리에 추가하세요.


```python
student_details[0]['AVERAGE_MID'] = average_midterm
student_details[1]['AVERAGE_MID'] = average_midterm
student_details[2]['AVERAGE_MID'] = average_midterm
```


```python
student_details[0]['AVERAGE_Final'] = average_final
student_details[1]['AVERAGE_Final'] = average_final
student_details[2]['AVERAGE_Final'] = average_final
```


```python
student_details
```




    [{'student_id': 1,
      'subject': 'math',
      'midterm': 60,
      'final': 85,
      'AVERAGE_MID': 76.66666666666667,
      'AVERAGE_Final': 82.66666666666667},
     {'student_id': 2,
      'subject': 'math',
      'midterm': 80,
      'final': 78,
      'AVERAGE_MID': 76.66666666666667,
      'AVERAGE_Final': 82.66666666666667},
     {'student_id': 3,
      'subject': 'math',
      'midterm': 90,
      'final': 85,
      'AVERAGE_MID': 76.66666666666667,
      'AVERAGE_Final': 82.66666666666667}]



# <font color='blue'> 4. 각각의 숫자를,  제곱한 값으로 바꾸세요.


```python
dictionary = {'C1' : [10,20,30],
              'C2' : [20,30,40]}


```


```python
dictionary['C1'] = [(10**2),(20**2),(30**2)]
dictionary['C2'] = [(20**2),(30**2),(40**2)]
```


```python
dictionary
```




    {'C1': [100, 400, 900], 'C2': [400, 900, 1600]}



# <font color='blue'>  5. (1)모든 키를 리스트로 출력하세요. (2) 모든 밸류를 리스트로 출력하세요. (3) 모든 밸류의 값을 다 더하세요.


```python
my_salary = {"alex": 25, "sally": 28, "dina": 30}

```


```python
print(list(my_salary.keys()))
```

    ['alex', 'sally', 'dina']
    


```python
print(list(my_salary.values()))
```

    [25, 28, 30]
    


```python
sum (my_salary.values())
```




    83




```python
max (my_salary.values())
```




    30




```python
min (my_salary.values())
```




    25



# <font color='blue'>  6. 딕셔너리의 길이를 구하고, 나이에 대한 오름차순으로 정렬하세요.


```python
my_dict = {"sally": 23, "dina": 22, "holy": 50, "Joe": 10, "Peter": 44}

```


```python
len(my_dict)
```




    5




```python
my_dict.values()
```




    dict_values([23, 22, 50, 10, 44])




```python
sorted(my_dict.values())
```




    [10, 22, 23, 44, 50]



# <font color='blue'> 7. 다음 코드를 실행해서 결과를 확인하세요. </font> 


```python
x = 10
y = 20
print(x>y)
print(x<y)
print(x==y)
print(x!=y)

```

    False
    True
    False
    True
    
