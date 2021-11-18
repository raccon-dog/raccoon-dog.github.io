---
layout : single
title : "파이썬 300제 101-110"
categories: Coding_Training
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# PYTHON PROGRAMMING FUNDAMENTALS


다음 토픽을 다룹니다. :    
- Functions
- Lambda Expressions
- Map


# FUNCTIONS
- 함수란, 재사용 되는 코드 블럭 입니다. 
- Data or arguments 가 전달되고, 결과가 return 됩니다.
- 우리가 프로그래밍 하다가, 반복되거나 재사용 되는 코드 블럭이 있으면, 이를 함수로 만들면 됩니다.
- 남들이 이렇게 재사용 잘 되는 함수들을 미리 만들어 놓은 것들도 많습니다. 이를 라이브러리라고 합니다.


## 함수를 나타내는 정의 (문법) 를 외우자.
- ### def
- ### 함수이름
- ### 파라미터의 의미
- ### 리턴이란?

![1](/assets/images/1.svg)


```python
def fahr_to_kelvin(temp):
    result = (temp-32) * (5/9)+ 273.15
    return result
```


```python
fahr_to_kelvin(1)
```




    255.92777777777775




```python
fahr_to_kelvin(100)
```




    310.92777777777775



# 함수는 사용하는 것이 아닌 함수를 호출(Call) 한 것 => funtion call
# 어딘가에는 함수의 실체 (정의: definition) 가 있습니다.


```python
result = 50
```


```python
temp = fahr_to_kelvin(result)
```


```python
result
```




    50



## 함수의 실행 순서를 이해하자. 
- ### CPU가 어떠한 실행 순서로 동작하는가?

![2](/assets/images/2.jpg)

## return 이 없는 경우


```python
def my_function():
    print('hello')
    print('bye')
```


```python
result = my_function()
```

    hello
    bye
    


```python
type(result)
```




    NoneType



## Parameter가 하나인 경우


```python
def squared(number) :
    result = number ** 2
    return result
```


```python
squared(9003030)
```




    81054549180900



## Parameters 가 두개인 경우


```python
def pow_times(number,count):
    result = number ** count
    return result
    
```


```python
pow_times(2,19)
```




    524288



## Return 값이 둘 이상인 경우


```python
# 숫자 2개를 입력받으면, 그 숫자들로 나눠서, 몫과 나머지를 리턴
```


```python
def cal(x,y):
    remainder = x // y
    mod = x % y
    return remainder, mod
```


```python
cal(10,5)
```




    (2, 0)



## Default parameter


```python
# 나이를 입력받으면, 나이가 몇인지 화면에 출력하는 함수
```


```python
def hello(age = 25):
    print("제 나이는 {}살 입니다.".format(age))
```


```python
hello(30)

#제 나이는 30살입니다.
```

    제 나이는 30살 입니다.
    


```python
hello()
```

    제 나이는 25살 입니다.
    


```python
hello(35)
```

    제 나이는 35살 입니다.
    


```python
input()
```

    안녕
    




    '안녕'




```python
input("입력 :")
```

    입력 :101010
    




    '101010'




```python
#이름과 나이를 입력받으면, "제 이름은 ... 이고 나이는 ... 살입니다."
```


```python
def hello(name = '홍길동',age = 30):
    print("안녕하세요 제 이름은 {}이고 나이는 {}살입니다.".format(name,age))
```


```python
hello('홍길동',30)
```

    안녕하세요 제 이름은 홍길동이고 나이는 30살입니다.
    


```python
hello(25)
```

    안녕하세요 제 이름은 25이고 나이는 30살입니다.
    


```python
hello('나나킴')
```

    안녕하세요 제 이름은 나나킴이고 나이는 30살입니다.
    


```python
hello(age=25)
```

    안녕하세요 제 이름은 홍길동이고 나이는 25살입니다.
    


```python
hello(age=25, name = "상식")
```

    안녕하세요 제 이름은 상식이고 나이는 25살입니다.
    

![last](/assets/images/last.png)
