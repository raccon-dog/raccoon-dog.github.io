# <font color='red'> *실습* </font> 
# <font color='red'> Functions </font> 

# <font color='blue'> 1.1. 하나의 숫자를 입력받아서, 입력받은 수까지의 짝수만 리스트로 반환하는 함수를 만드세요. 
    예) 7을 입력하면, 결과로 [2,4,6] 리스트를 반환.


```python
def num_list(num):
    number_list=[]
    for i in range(1,num+1):
        if i % 2 ==0:
            number_list.append(i)
    return(number_list)
        
```


```python
num_list(8)
```




    [2, 4, 6, 8]



# <font color='blue'> 1.2. 두 수를 입력받아서, 두수의 합을 구하여 리턴하는, 함수 Sum 을 만드세요. 함수명은 Sum 입니다.


```python
def Sum(x,y):
    result = x + y
    return result
```


```python
Sum(5,6)
```




    11



# <font color='blue'> 2. 숫자 두개, 문자열 1개를 입력받아서, 더하기와 곱하기 연산을 하고, 리턴하는 함수를 만드세요.
## 함수명은 cal ( value1, value2, operator_str )
## operator_str 은 'add', 'mul' 두가지 입니다.
## 만약 cal(3, 4, 'add') 이면 더하기를 하고
## cal(3, 4, 'mul') 이면 곱하기를 합니다.


```python
def cal (value1,value2,operator_str):
    if operator_str == "add":
        return value1 + value2
    elif operator_str == "mul":
        return value1 * value2
```


```python
cal(5,6,'add')
```




    11




```python
cal(5,6,'mul')
```




    30



# <font color='blue'> 2-1. 숫자 두개를 입력받으면, 더하기와 곱하기 연산을 하고, 둘 다 리턴하는 함수를 만드세요.


```python
def cal2(num,num2):
    result = num+num2
    result2 = num*num2
    return result,result2
```


```python
cal2(3,4)
```




    (7, 12)



# <font color='blue'> 3. 과일 등급을 반환하는 함수를 작성하세요.
## 과일 크기를 입력으로 받으면, 등급을 리턴하는 함수.
    


```python
def grade(size = None):
    size = int(input("크기 입력:"))
    if size > 100:
        result = "상"
    elif size> 50:
        result = "중"
    elif size>0:
        result = "하"
    elif size < 0:
        result = "다시 입력해주세요"
    return result    
    
```


```python
A = grade()
```

    크기 입력:11
    


```python
A
```




    '하'



# <font color='blue'> 4. 다음 리스트가 있다. 이 리스트를 함수에 넘겨주면(파라미터), 리스트의 요소를 모두 더한 값을 리턴하는 함수 arr_sum 함수를 작성하세요.


```python
a = [112,234,-355,14,54,44, 94, -1203, 8,44 ]
```


```python
def arr_sum(List):
    result = sum(List)
    return result
        
```


```python
arr_sum(a)
```




    -954



# <font color='blue'> 5. 학생 이름과 수학점수를 입력받습니다. (4.b 12번 문제를 함수로 변경하는 문제)
# <font color='blue'> 입력) 이름 입력 : 홍길동
# <font color='blue'> 입력) 영어 점수 입력 : 98
# <font color='blue'> 입력) 수학 점수 입력 : 78

.
# <font color='blue'> 4명을 입력받으면 더 이상 입력을 받지 않고 다음을 계산하여 출력합니다.
.

# <font color='blue'> 출력) 영어 점수 평균은 ... 점입니다.
# <font color='blue'> 출력) 수학 점수 평균은 ... 점입니다.
    
# 위에서, 유저가 입력한 딕셔너리를, 파라미터로 받아서, 영어점수와 수학점수를 리턴하는 함수 score_average 를 작성하세요.









```python
my_dict_m = {}
my_dict_e = {}
for i in range(4):
    name = input("이름 입력 : ")
    e_score = int(input("영어 점수 입력 : "))
    m_score = int(input("수학 점수 입력 : "))
    my_dict_m[name] = m_score
    my_dict_e[name] = e_score
```

    이름 입력 : A
    영어 점수 입력 : 100
    수학 점수 입력 : 90
    이름 입력 : B
    영어 점수 입력 : 80
    수학 점수 입력 : 70
    이름 입력 : C
    영어 점수 입력 : 90
    수학 점수 입력 : 80
    이름 입력 : D
    영어 점수 입력 : 60
    수학 점수 입력 : 60
    


```python
def score_average(dic_m,dic_e):
    average_m = (sum(dic_m.values()))/len(dic_m.values())
    average_e = (sum(dic_e.values()))/len(dic_e.values())
    print("수학점수 평균은 {}점 입니다.".format(average_m))
    print("영어점수 평균은 {}점 입니다.".format(average_e))
    return average_m,average_e
```


```python
score_average(my_dict_m,my_dict_e)
```

    수학점수 평균은 75.0점 입니다.
    영어점수 평균은 82.5점 입니다.
    




    (75.0, 82.5)



# <font color='blue'> 6. 위에서

# <font color='blue'> 영어 최고점은 .. 점 입니다.
# <font color='blue'> 수학 최고점은 .. 점 입니다.

# 위에서 유저가 입력한 딕셔너리를, 파라미터로 받아서, 영어 최고점과 수학 최고점을 리턴하는 함수 get_max 를 작성하세요.






```python
def get_max(dic_m,dic_e):
    max_m = max(dic_m.values())
    max_e = max(dic_e.values())
    print("수학 최고점은 {}점 입니다.".format(max_m))
    print("영어 최고점은 {}점 입니다.".format(max_e))
    return max_m,max_e
```


```python
get_max(my_dict_m,my_dict_e)
```

    수학 최고점은 90점 입니다.
    영어 최고점은 100점 입니다.
    




    (90, 100)




```python
score_dict = {}
for i in range(4):
    name = input("이름 입력:")
    eng = int(input("영어 점수 입력:"))
    math = int(input("수학 점수 입력"))
    
    score_dict[name] = [eng,math]
```

    이름 입력:A
    영어 점수 입력:100
    수학 점수 입력100
    이름 입력:B
    영어 점수 입력:90
    수학 점수 입력90
    이름 입력:C
    영어 점수 입력:90
    수학 점수 입력90
    이름 입력:D
    영어 점수 입력:80
    수학 점수 입력80
    


```python
def score_average2(score_dict):
    value_list = list(score_dict.values())
    eng_list = []
    math_list = []
    for data in value_list :
        eng = data[0]
        math = data[1]
        eng_list.append(eng)
        math_list.append(math)
    avg_eng = sum(eng_list)/len(eng_list)
    avg_math = sum(math_list)/len(math_list)
    return avg_eng,avg_math
```


```python
result = score_average2(score_dict)
```


```python
print("영어 점수 평균은 {}점 입니다.".format(result[0]))
print("수학 점수 평균은 {}점 입니다.".format(result[1]))
```

    영어 점수 평균은 90.0점 입니다.
    수학 점수 평균은 90.0점 입니다.
    

### 파라미터를 하나만 받을경우 


```python
def get_max2(score_dict):
    value_list = list(score_dict.values())
    eng_list = []
    math_list = []
    for data in value_list :
        eng = data[0]
        math = data[1]
        eng_list.append(eng)
        math_list.append(math)
    max_eng = max(eng_list)
    max_math = max(math_list)
    return max_eng,max_math
    
```


```python
max_result = get_max2(score_dict)
```


```python
print("영어 점수 최고점은 {}점 입니다.".format(max_result[0]))
print("수학 점수 최고점은 {}점 입니다.".format(max_result[1]))
```

    영어 점수 최고점은 100점 입니다.
    수학 점수 최고점은 100점 입니다.
    
