---
layout : single
title : "파이썬 - 조건문 실습"
categories: Coding_Training
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# <font color='red'> *실습* </font> 
# <font color='red'> Comparison and logical operators and if Statements </font> 

## 1. 유저한테 숫자 1개를 입력받아서, 

## 그 숫자가 10이면, 

## 정답입니다!  를 출력하는 프로그램


```python
User = int(input("숫자 입력:"))
if User == 10:
    print("정답입니다!")
else:
    print("다시 도전해보세요")
```

    숫자 입력:10
    정답입니다!
    

## 2. 유저한테 숫자 1개를 입력받아서,

## 그 숫자가 짝수이면 "짝수"를 출력하고, 홀수이면 "홀수"를 출력하는 프로그램


```python
user = int(input("숫자 입력 :"))
if user % 2 == 1:
    print("홀수입니다.")
else:
    print("짝수입니다.")
```

    숫자 입력 :3
    홀수입니다.
    

## 3. 유저한테 점수를 입력받아서,

## 점수가 0보다 작거나 100보다 크면, "잘못 입력했습니다."를 출력.

## 점수가 80 이상이면, "입력하신 학점 ...은  A 학점입니다." 를 출력

## 점수가 80 점 미만이면, "입력하신 학점 ... 은 B 학점입니다."를 출력


```python
user_score = int(input("점수 입력:"))
if user_score > 100 or user_score < 0 :
    print ("잘못 입력했습니다.")
elif user_score >=80:
    print ("입력하신 점수 {}은 A학점입니다.".format(user_score))
else:
    print ("입력하신 점수 {}은 B학점입니다.".format(user_score))
    
```

    점수 입력:77
    입력하신 점수 77은 B학점입니다.
    

## 4. 바람의 속도를 입력받아서, 해당 바람의 속도가 다음과 같을 경우, 해당되는 문자열을 출력하세요.

### 만약 유저가 1보다 작은 값을 입력하면, "1보다 큰 수를 입력하세요"를 출력합니다.

![img](/assets/images/Comparison/6.png)

```python
wind = int(input())
if wind >= 64:
    print("Hurricane")
elif wind >= 48:
    print("Storm")
elif wind >= 28:
    print("Gale")
elif wind >= 4:
    print("Breeze")
elif wind >= 1:
    print("Light air")
else:
    print("1보다 큰 수를 입력하세요.")
```

    65
    Hurricane
    

## 5. 회원가입을 하려 합니다. 유저한테 이메일과 비밀번호를 입력받습니다.

## 유저한테 이메일을 입력받습니다. 이때 이메일주소 형식(@)이 잘못 되었으면, 다시 입력하세요 를 출력합니다.

## 이메일 주소가 잘 입력되었으면, 이제 비밀번호를 두번 입력받습니다.

## 만약 첫번째 입력한 비밀번호와, 두번째 입력한 비밀번호가 다르면, 비밀번호가 일치하지 않습니다 를 출력합니다. 

#비밀번호의 길이는 4자리 이상 8자리 이하로만 받습니다. 
# 그렇지 않은 경우는 "비밀번호 길이는 4자리 이상 8자리 이하로 입력하세요


```python
email = input("이메일 입력: ")
if "@" not in email :
    print("다시 입력하세요")
else:
    password1 = input("비밀번호 입력 : ")
    if len(password1) < 4 or len(password1) > 8:
            print("비밀번호 길이는 4자리 이상 8자리 이하로 입력하세요")
    else:        
        password2 = input("비밀번호 확인 : ")
        if password1 != password2:
            print("비밀번호가 일치하지 않습니다")
        else:
            print("회원가입을 축하합니다!")
```

    이메일 입력: @
    비밀번호 입력 : 1234
    비밀번호 확인 : 1234
    회원가입을 축하합니다!
    
