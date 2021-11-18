---
layout : single
title : "파이썬 - 조건문과 논리연산자 "
categories: Coding_Class
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# PYTHON PROGRAMMING FUNDAMENTALS


## 프로그램에 Comment (코멘트) 달기

### 주석이라고도 합니다.
### 파이썬에서는  문장 맨 앞에 # 을 붙여줍니다.
### 컴퓨터가 그 문장은 실행하지 않습니다. 단지 사람을 위한 문장입니다.


```python
# 프린트 하는 문장입니다. 
print("hello")
```

    hello
    


```python
# 회원가입할때, 비밀번호는 6자리 이상 12자리 이하로 해야한다.
```


```python
password = input('비밀번호입력 :')
```

    비밀번호입력 :321321323232313
    
![1](/assets/images/Comparison/1.PNG)
![2](/assets/images/Comparison/2.PNG)

```python
ret = data <= cnt % 2
```


```python
ret
```




    False



# LOGICAL OPERATORS 

## 실제 and 연산을 위 4개 조건으로 실행 해봅니다. 
![and](/assets/images/Comparison/3.jpg)

```python
False and False
```




    False




```python
True and True
```




    True




```python
True and False
```




    False




```python
False and True
```




    False



## 실제 or 연산을 위 4개 조건으로 실행 해봅니다. 
![or](/assets/images/Comparison/4.jpg)

```python
False or False
```




    False




```python
False or True
```




    True




```python
True or False
```




    True




```python
True or True
```




    True



## 여러개의 조합


```python
(True and True) or False
```




    True




```python
(True or False) and True
```




    True



# CONDITIONAL STATEMENTS 

## 조건문이란, 우리 일상생활에서 흔히 쓰는 문장.  if ~ 라면, ~ 한다. 

### 비가 오면 우산을 들고 나가고, 비가 오지 않으면 운동화를 신고 간다.

### 배가 고프면 사과를 먹고, 배가 고프지 않으면 콜라를 먹는다.

### 5가 2보다 크면 If condition is True 를 출력하고, 그렇지 않으면, If condition is False를 출력한다.


```python
#조건 + 행동(액션) => 조건문
```


```python
if 5 > 12:
    print('If condition is True')
else:
    print('If condition is False')
```

    If condition is False
    


```python
if len(password) > 13:
    print("비밀번호는 12자리 까지입니다.")
elif len(password) < 6:
    print("비밀번호는 6자리 이상이여야 합니다.")
else:
    pass
```

    비밀번호는 12자리 까지입니다.
    

## 위의 문장에서, 무엇을 주의깊게 봐야 할까요?  

### 파이썬 문법입니다.  '정의' 이므로 이렇게 따라해야만 컴퓨터가 이해할 수 있습니다.

### <font color='blue'> 탭 ! tab !  입니다. 들여쓰기(indentation)가 중요합니다. 


### 여러 문장을 수행하는 예제


```python
my_satatus = 0
my_size = 6

if my_size > 5 :
    my_status = 10
    print("배부릅니다.")
else:
    my_status = 3
    print('더 먹을 수 있습니다.')
```

    배부릅니다.
    


```python
my_status
```




    10
  


## CPU의 코드 실행 순서
![cpu](/assets/images/Comparison/5.png)
### 위의 식을 작성해봅시다.


```python
apple_count = 5

if apple_count >= 10 :
    print("사과를 구매할 필요가 없습니다.")
elif apple_count >= 4 :
    print("사과가 적정량을 유지하고 있습니다.")
else:
    print("사과를 구매해야 합니다.")
```

    사과가 적정량을 유지하고 있습니다.
    

## Nested 중첩된 조건문


```python
year = 2019
month = 3
day = 3

day+=1

if day > 31 :
    month+=1
    day = 1
    
    if month > 12 :
        year+=1
        month = 1
        
print("{} 년 {} 월 {} 일".format(year, month, day))
```

    2019 년 3 월 4 일
    

### input 함수


```python
name = input("Welcome to the course, what's your name? ") 
print("Welcome " + name + ":)")

```

    Welcome to the course, what's your name? PYS
    Welcome PYS:)
    
