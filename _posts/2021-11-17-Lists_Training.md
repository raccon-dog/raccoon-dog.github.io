---
layout : single
title : "파이썬 - 리스트 실습 "
categories: Coding_Training
tag : Python
author_profile: false
sidebar:
    nav: "docs"
---

# <font color='red'> *실습* </font> 
# <font color='red'> LISTS </font> 

# <font color='blue'> 1. 아래 이름들을, names 리스트로 만드세요.
    
    "sara", "chanel", "mike", "ryan", "holy", "alex", "rob"


```python
names = ["sara", "chanel", "mike", "ryan", "holy", "alex", "rob"]
```


```python
names
```




    ['sara', 'chanel', 'mike', 'ryan', 'holy', 'alex', 'rob']



# <font color='blue'> 2. 각 이름의 맨 앞자를 대문자로 바꿔서, names 리스트를 다시 만드세요.
   


```python
strings = '"sara", "chanel", "mike", "ryan", "holy", "alex", "rob"'
```


```python
strings = strings.strip('"')
```


```python
Strings = strings.title()
```


```python
names = Strings.split(",")
```


```python
names
```




    ['Sara"', ' "Chanel"', ' "Mike"', ' "Ryan"', ' "Holy"', ' "Alex"', ' "Rob']



# <font color='blue'> 3. (1)두번째 항목 출력, (2) 마지막 항목을 출력 </font> 



```python
names[1]
```




    ' "Chanel"'




```python
names[-1]
```




    ' "Rob"'




```python
type(names)
```




    list



# <font color='blue'> 4. "Chanel" "Mitch" "Ryan" 항목 출력, </font> 


```python
names
```




    ['sara', 'chanel', 'mike', 'ryan', 'holy', 'alex', 'rob']




```python
print(names[1:4])
```

    [' "Chanel"', ' "Mike"', ' "Ryan"']
    

# <font color='blue'> 5. 리스트 맨 마지막 3개 항목을 출력하기</font> 


```python
print(names2[-3:])
```

    [' "Holy"', ' "Alex"', ' "Rob"']
    

# <font color='blue'> 6. 다음을 출력 (1) aly, (2) sally (3) peter, aly </font> 



```python
my_list = ["Mitch", ["sara", "sally", "joe"], "peter", "aly"]
```


```python
print(my_list[-1])
print(my_list[1][1])
print(my_list[2:4])
```

    aly
    sally
    ['peter', 'aly']
    

# <font color='blue'> 7. 현재 리스트의 길이를 먼저 구하고, 자신의 이름을 맨 끝에 추가하세요. </font> 


```python
my_list = ["Mitch", ["sara", "sally", "joe"], "peter", "aly"]
```


```python
len(my_list)
```




    4




```python
my_list.append("pys")
```


```python
my_list
```




    ['Mitch', ['sara', 'sally', 'joe'], 'peter', 'aly', 'pys']



# <font color='blue'> 8. "PETER" 를 리스트에서 제거하세요. </font> 
  


```python
my_list.remove("peter")
```


```python
my_list
```




    ['Mitch', ['sara', 'sally', 'joe'], 'aly', 'pys']



# <font color='blue'> 9. "Mitch" 오른쪽에 "Mike"를 추가하세요. </font> 
  


```python
my_list.insert(1,"Mike")
```


```python
my_list
```




    ['Mitch', 'Mike', ['sara', 'sally', 'joe'], 'aly', 'pys']



# <font color='blue'> 10. 오름차순으로 순서대로 정렬하세요. </font> 
   
   


```python
my_list = [50, 20, 30, 10, 40, 15, 45]


```


```python
my_list.sort()
```


```python
my_list
```




    [10, 15, 20, 30, 40, 45, 50]



# <font color='blue'> 11. 위 리스트를 내림차순으로 정렬하세요. </font> 


```python
my_list.sort(reverse=True)
```


```python
my_list
```




    [50, 45, 40, 30, 20, 15, 10]



# <font color='blue'> 12. 리스트 안에, 리스트들이 들어 있습니다. 안쪽 리스트들의 맨 마지막 항목들만 뽑아서, 새로운 리스트를 만드세요. </font> 
- chocolate, potatoes, protein bar 를 뽑아내는 코드를 작성하고, 이들을 리스트로 만듭니다.
   


```python
grocery_list = [['chips','jelly','chocolate'],['sweet potatoes','potatoes'],['peanuts','protein bar']]

```


```python
new_list = [grocery_list[0][-1],grocery_list[1][-1],grocery_list[2][1]]
```


```python
new_list.append(grocery_list[0][-1])
new_list.append(grocery_list[1][-1])
new_list.append(grocery_list[2][1])
```


```python
new_list
```




    ['chocolate',
     'potatoes',
     'protein bar',
     'chocolate',
     'potatoes',
     'protein bar']



# <font color='blue'> 13. 다음 문장을, 공백기준으로 잘라서, 리스트로 만드세요. 그리고 to 라는 단어가 몇개 인지 확인하세요. </font> 
- 예)   [ 'She', 'had', 'a', 'lot',,,,]
- 문자열 부분에서 배운 함수를 참고하세요


```python
essay = '''"She had a lot of money. She was a generous woman. She was once poor. She understood what it was like. She wanted to help out. On Christmas day, she handed out food to the poor. She made the food herself. She put a turkey leg, a scoop of mash potatoes, and peas on a plate. She gave the plate to each homeless person she saw.

The homeless people loved her. One homeless man even gave her a penny. She said to keep it for himself. She decided to do more. She gave $50 to every homeless person she saw. She felt good."'''
```


```python
essay = essay.strip('"')
```


```python
essay = essay.lower()
```


```python
print(essay)
```

    she had a lot of money. she was a generous woman. she was once poor. she understood what it was like. she wanted to help out. on christmas day, she handed out food to the poor. she made the food herself. she put a turkey leg, a scoop of mash potatoes, and peas on a plate. she gave the plate to each homeless person she saw.
    
    the homeless people loved her. one homeless man even gave her a penny. she said to keep it for himself. she decided to do more. she gave $50 to every homeless person she saw. she felt good.
    


```python
list2 = essay.split(" ")
```


```python
list2
```




    ['she',
     'had',
     'a',
     'lot',
     'of',
     'money.',
     'she',
     'was',
     'a',
     'generous',
     'woman.',
     'she',
     'was',
     'once',
     'poor.',
     'she',
     'understood',
     'what',
     'it',
     'was',
     'like.',
     'she',
     'wanted',
     'to',
     'help',
     'out.',
     'on',
     'christmas',
     'day,',
     'she',
     'handed',
     'out',
     'food',
     'to',
     'the',
     'poor.',
     'she',
     'made',
     'the',
     'food',
     'herself.',
     'she',
     'put',
     'a',
     'turkey',
     'leg,',
     'a',
     'scoop',
     'of',
     'mash',
     'potatoes,',
     'and',
     'peas',
     'on',
     'a',
     'plate.',
     'she',
     'gave',
     'the',
     'plate',
     'to',
     'each',
     'homeless',
     'person',
     'she',
     'saw.\n\nthe',
     'homeless',
     'people',
     'loved',
     'her.',
     'one',
     'homeless',
     'man',
     'even',
     'gave',
     'her',
     'a',
     'penny.',
     'she',
     'said',
     'to',
     'keep',
     'it',
     'for',
     'himself.',
     'she',
     'decided',
     'to',
     'do',
     'more.',
     'she',
     'gave',
     '$50',
     'to',
     'every',
     'homeless',
     'person',
     'she',
     'saw.',
     'she',
     'felt',
     'good.']




```python
list2.count("to")
```




    6


