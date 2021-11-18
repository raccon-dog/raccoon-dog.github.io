---
layout : single
title : "파이썬 - 문자열(실습)"
categories: Coding_Training
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---
# <font color='red'> *실습* </font> 
# <font color='red'> STRINGS </font> 

# <font color='blue'> 1. 유저로부터 문장을 입력받으세요. 그리고 그 문장을 공백기준 단어로 분리하여 출력하세요. </font>
- 입력 예) 유저로부터 : 안녕하세요? 오늘 날씨가 아주 좋네요.
- 출력 예) ['안녕하세요?', '오늘', '날씨가', '아주', '좋네요.']


```python
Sentence = input()
```

    안녕하세요? 오늘 날씨가 아주 좋네요.
    


```python
print(Sentence.split(" "))
```

    ['안녕하세요?', '오늘', '날씨가', '아주', '좋네요.']
    

# <font color='blue'> 2. 유저로 부터 영어 문자열을 입력받아서, 그 문자열을 대문자로 모두 바꾼후, 화면에 출력하세요. </font> 


```python
sentence1 = input()
```

    fvvff
    


```python
print(sentence1.upper())
```

    FVVFF
    

# <font color='blue'> 3. 다음의 이메일 주소에서, 이메일의 아이디 부분과 도메인 부분을 분리하여 화면에 출력하세요. </font> 


```python
email = 'cs_team@mycompany.co.kr'
```


```python
print(email.split('@'))
```

    ['cs_team', 'mycompany.co.kr']
    

# <font color='blue'> 4. 다음 문장에서, quite만 문자열을 추출하여 출력하세요.</font> 


```python
sentence = 'So it is quite different, then, if in a mountain town'
```


```python
sentence.find('quite')
```




    9




```python
print(sentence[9:14])
```

    quite
    

# <font color='blue'> 5. 다음 문장에서, 앞의 So를 제거하고, 뒤의 town을 제거한 문자열을 출력하세요.</font> 


```python
sentence = 'So it is quite different, then, if in a mountain town'
```


```python
sentence.find('town')
```




    49




```python
print(sentence[2:49])
```

     it is quite different, then, if in a mountain 
    

# <font color='blue'> 6. 다음 문장 전체에서, 4번째 문자마다 출력하세요.</font> 


```python
sentence = 'So it is quite different, then, if in a mountain town'
```


```python
print(sentence[::4])
```

    St tir,einmt n
    

# <font color='blue'> 7. 예를들어, 입력할 수 있는 글자수가 500글자 입니다. 다음 문장은 입력받을 수 있는 문장인지 확인하세요.</font> 


```python
essay = '''"She had a lot of money. She was a generous woman. She was once poor. She understood what it was like. She wanted to help out. On Christmas day, she handed out food to the poor. She made the food herself. She put a turkey leg, a scoop of mash potatoes, and peas on a plate. She gave the plate to each homeless person she saw.

The homeless people loved her. One homeless man even gave her a penny. She said to keep it for himself. She decided to do more. She gave $50 to every homeless person she saw. She felt good."'''
```


```python
len(essay)
```




    517



# <font color='blue'> 8. 위 문장(essay)에서 plate 라는 글자와, earth라는 글자가 들어있는지 확인하는 코드를 작성하세요.</font> 


```python
essay.find('plate')
```




    267




```python
essay.find('earth')
```




    -1




```python
'plate' in essay
```




    True




```python
'earth' in essay
```




    False


