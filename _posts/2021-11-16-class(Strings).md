---
layout : single
title : "파이썬 - 문자열"
categories: Coding_Class
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---

# PYTHON PROGRAMMING 기초

# STRINGS - 문자열
- 각각의 하나의 문자들이 나열된 상태, 즉 시퀀스(sequence) 이다!!!
- 문자열은, 싱글퀏이나 더블퀏 (single or double quotes)으로 감싸야 한다.


```python
x = 'Hello World'
```


```python
y = "Hello World"
```


```python
x
```




    'Hello World'




```python
y
```




    'Hello World'



## 3개의 단일 부호로 문자열을 만들 수 있다. 특히 줄을 바꿔가면서 긴 문자열 만들때 유용.


```python
poem = '''So "it is" quite different, then, if in a mountain town
the mountains are close, rather than far. Here

they are far, their distance away established,
consistent year to year, like a parent’s

or sibling’s. They have their own music.
So I confess I do not know what it’s like,

listening to mountains up close, like a lover,
the silence of them known, not guessed at.'''
```


```python
poem
```




    'So "it is" quite different, then, if in a mountain town\nthe mountains are close, rather than far. Here\n\nthey are far, their distance away established,\nconsistent year to year, like a parent’s\n\nor sibling’s. They have their own music.\nSo I confess I do not know what it’s like,\n\nlistening to mountains up close, like a lover,\nthe silence of them known, not guessed at.'




```python
print(poem)
```

    So "it is" quite different, then, if in a mountain town
    the mountains are close, rather than far. Here
    
    they are far, their distance away established,
    consistent year to year, like a parent’s
    
    or sibling’s. They have their own music.
    So I confess I do not know what it’s like,
    
    listening to mountains up close, like a lover,
    the silence of them known, not guessed at.
    

## 문자열을 다루는 함수들

### \+ 연산자는, 숫자 뿐만 아니라 문자열에서도 사용이 가능하다. 
- 여러 문자열들을 결합할 수 있다.


```python
first_name = 'Mitch'
```


```python
last_name = 'Steve'
```


```python
first_name + last_name
```




    'MitchSteve'




```python
full_name = first_name + ' ' + last_name
```


```python
print(full_name)
```

    Mitch Steve
    

### 대소문자로 바꿀수 있다.


```python
full_name.upper()
```




    'MITCH STEVE'




```python
full_name.lower()
```




    'mitch steve'




```python
full_name.title()
```




    'Mitch Steve'




```python
type('Hello') == str 
```




    True



### 문자열을 원하는기준으로, 각각 분리해 낸다.


```python
full_name.split('t')
```




    ['Mi', 'ch S', 'eve']




```python
full_name.split(' ')
```




    ['Mitch', 'Steve']




```python
full_name.split('ch')
```




    ['Mit', ' Steve']



### 문자 한개만 추출하기
- 순방향, 역방향 이해


```python
letters = 'abcdefghijklmnopqrstuvwxyz'
```

## 가져온다!! 억세스한다!! => 데이터 억세스 기호는, 변수명 바로  오른쪽에, 대괄호로 시작
## 대괄호 안의 숫자는, 인덱스(오프셋)라고 하며, index(offset)
## 컴퓨터에서는 0부터 시작한다!! => 컴퓨터가 자동으로 매기는 숫자


```python
letters[25]
```




    'z'




```python
letters[-3]
```




    'x'




```python
letters = 'qbcdefghijklmnopqrstuvwxyz'
```


```python
letters
```




    'qbcdefghijklmnopqrstuvwxyz'



- 문자열은 immutable 이다. 따라서 한번 생성된 문자열 자체를 바꾸는것은 할 수 없다. 
- 따라서, 새로운 메모리에 변경한 문자열을 새로 만드는 방법을 사용하게 된다.


```python
letters.replace('a','q')
```




    'qbcdefghijklmnopqrstuvwxyz'



### 문자열의 일부를 추출하기 -slicing 슬라이싱
- [:] 처음부터 끝까지
- [start:] start오프셋부터 끝까지
- [:end] 처음부터 end-1 오프셋까지 
- [start : end] start오프셋부터 end-1 오프셋까지
- [start : end : step] step만큼 문자를 건너뛰면서, 위와 동일하게 추출


```python
letters[2:7]
```




    'cdefg'




```python
letters[-5:]
```




    'vwxyz'




```python
letters[:4+1]
```




    'qbcde'




```python
letters.find('c')
```




    2




```python
letters.find('g')
```




    6




```python
letters.find('e')
```




    4




```python
letters[ : :2]
```




    'qcegikmoqsuwy'



### 문자열의 길이
- len() 함수를 사용하여 몇개의 문자로 되어있는지 알 수 있다.


```python
len(letters)
```




    26




```python
email = '       abc@naver.com'
```


```python
email.strip()
```




    'abc@naver.com'



### 문자열 위치 찾기
- find 함수는, 찾고자 하는 문자열이 존재하는 곳의 첫번째 오프셋을 알려준다.
- rfind 함수는, 찾고자 하는 문자열이 있는 마지막 오프셋을 알려준다. 


```python
print(poem)
```

    So "it is" quite different, then, if in a mountain town
    the mountains are close, rather than far. Here
    
    they are far, their distance away established,
    consistent year to year, like a parent’s
    
    or sibling’s. They have their own music.
    So I confess I do not know what it’s like,
    
    listening to mountains up close, like a lover,
    the silence of them known, not guessed at.
    


```python
poem.find('"')
```




    3




```python
poem.rfind('year')
```




    170




```python
len(poem)
```




    367



### 문자열의 갯수 파악
- count() 함수는 몇개의 문자열이 있는지 알려준다.


```python
poem.count('banana')
```




    0


