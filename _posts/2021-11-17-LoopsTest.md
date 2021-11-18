# <font color='red'> *실습* </font> 
# <font color='red'> Loops </font> 

# <font color='blue'> 1,2.    a, b, c 의 값은?

## a = 5
## b = a + 2
## a = 1
## c = b - a



```python
a = 1 , b = 7 c = 6
```

# <font color='blue'> 3. 1부터 150까지 전부 더한 값을 출력하세요.


```python
A = list(range(0,151))
```


```python
sum(A)
```




    11325



# <font color='blue'> 4. 다음처럼 * 모양을 7개부터 1개까지 출력하는 프로그램을 만드세요.


![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-07-13%2021.35.32.png](attachment:%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-07-13%2021.35.32.png)


```python
numbers = list(range(1,8))
```


```python
numbers = sorted(numbers,reverse=True)
```


```python
numbers
```




    [7, 6, 5, 4, 3, 2, 1]




```python
for i in numbers :
    print(i*"*")
```

    *******
    ******
    *****
    ****
    ***
    **
    *
    

# <font color='blue'> 5. 유저가 입력한 숫자에 해당되는, 구구단을 하는 프로그램을 작성하세요.
    
## 입력 ) 단을 입력하세요 : 3

## 출력 ) 3 X 1 = 3
##              ...


```python
x = int(input("단을 입력하세요: "))
for i in range(1,10):
    print(i * x)
```

    단을 입력하세요: 3
    3
    6
    9
    12
    15
    18
    21
    24
    27
    

# <font color='blue'> 6. 1부터 100까지 출력하되, 3의 배수에는 "박수" 라는 글자를 출력하는 프로그램을 작성하세요.

1
2
박수
4
5
박수
7
8
박수
...


```python
for i in range(1,101):
    if i%3 == 0:
        print("박수")
    else:
        print(i)
```

    1
    2
    박수
    4
    5
    박수
    7
    8
    박수
    10
    11
    박수
    13
    14
    박수
    16
    17
    박수
    19
    20
    박수
    22
    23
    박수
    25
    26
    박수
    28
    29
    박수
    31
    32
    박수
    34
    35
    박수
    37
    38
    박수
    40
    41
    박수
    43
    44
    박수
    46
    47
    박수
    49
    50
    박수
    52
    53
    박수
    55
    56
    박수
    58
    59
    박수
    61
    62
    박수
    64
    65
    박수
    67
    68
    박수
    70
    71
    박수
    73
    74
    박수
    76
    77
    박수
    79
    80
    박수
    82
    83
    박수
    85
    86
    박수
    88
    89
    박수
    91
    92
    박수
    94
    95
    박수
    97
    98
    박수
    100
    

# <font color='blue'> 7. 유저한테 숫자를 6번 입력받으세요. 
# <font color='blue'> 유저가 입력한 숫자들 중에서 음수의 갯수를 출력하세요.



```python
숫자 입력 : 
숫자 입력 : 
숫자 입력 : 
숫자 입력 : 
숫자 입력 : 
숫자 입력 : 
음수의 갯수는 2개입니다.
```


```python
Minus = []
for i in range(6):
    i = int(input("숫자 입력 : "))
    if i < 0 :
        Minus.append(i)
print("음수의 갯수는 {}개 입니다.".format(len(Minus)))
```

    숫자 입력 : 1
    숫자 입력 : 2
    숫자 입력 : 3
    숫자 입력 : 4
    숫자 입력 : 5
    숫자 입력 : -1
    음수의 갯수는 1개 입니다.
    

# <font color='blue'> 7-1. 유저한테 숫자 6개를 입력받으세요.
# <font color='blue'> 유저가 입력한 숫자들을, 입력한 역순으로 출력하세요.

입력 예) 숫자를 6개 입력하세요.
             5  7  -23  -1  99  321

출력 예)  321  99  -1  -23  7  5



```python
number_list = []
for i in range(6):
    i = int(input("숫자 입력 : "))
    number_list.append(i)
print(number_list[::-1])
```

    숫자 입력 : 1
    숫자 입력 : 2
    숫자 입력 : 3
    숫자 입력 : 4
    숫자 입력 : 5
    숫자 입력 : 6
    [6, 5, 4, 3, 2, 1]
    

# <font color='blue'> 8. A 학급에 총 10명의 학생이 있습니다. 이 학생들의 중간고사 점수는 다음과 같습니다.

# <font color='blue'> 70, 60, 55, 75, 95, 90, 80, 80, 85, 76

# <font color='blue'> 그런데 중간고사 채점에 문제가 있어서, 전부 7점씩 뺀 점수로 리스트를 만드세요.


```python
score_list = [70, 60, 55, 75, 95, 90, 80, 80, 85, 76]
```


```python
new_score_list =[]
```


```python
for i in score_list:
    new_score_list.append(i-7)
```


```python
new_score_list
```




    [63, 53, 48, 68, 88, 83, 73, 73, 78, 69]



# <font color='blue'> 9. 위의 점수 중 최고 점수와 최저 점수는 몇점 인가?


```python
max(new_score_list)
```




    88




```python
min(new_score_list)
```




    48



# <font color='blue'> 10. 유저가 점수를 입력하면, 해당 학점을 출력하는 프로그램입니다.  
# <font color='blue'> 단, 유저가 -1 을 입력하면, 프로그램을 종료합니다. -1 을 입력하기 전에는 계속 입력을 받습니다. 


![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-07-13%2021.51.27.png](attachment:%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-07-13%2021.51.27.png)


```python
점수를 입력 : 80
학점은 B 입니다.

점수를 입력 : 66
학점은 C 입니다.

점수를 입력 : 99
학점은 A 입니다.

점수를 입력 : 

```


```python
while True:
    score = int(input("점수를 입력 :"))
    if 85 <= score <= 100 :
        print("학점은 A입니다.")
    elif 75 <= score <= 84 :
        print("학점은 B입니다.")
    elif 65 <= score <= 74:
        print("학점은 C입니다.")
    elif 0 <= score <= 73:
        print("학점은 F입니다.")
    elif score == -1:
        break
    else:
        print("다시 입력해주세요")
```

    점수를 입력 :555555555555
    다시 입력해주세요
    점수를 입력 :888888888888888888
    다시 입력해주세요
    점수를 입력 :-1331
    다시 입력해주세요
    점수를 입력 :-1
    

# <font color='blue'> 11. 유저한테 구구단 시작단을 입력받으세요.
# <font color='blue'> 2를 입력받으면, 2단에서 9단까지 출력하세요.
# <font color='blue'> 8을 입력받으면, 8단에서 9단까지 출력하세요.
# <font color='blue'> 9단보다 큰 단을 입력하면, “잘못입력하였습니다.” 하고, 다시 단을 입력 받습니다.
# <font color='blue'> 단, 0 을 입력받으면, 프로그램을 종료하세요.
# <font color='blue'> 입력)  단을 입력하세요.
# <font color='blue'> 출력)  4X1 = 4 
# <font color='blue'>          ...



```python
단 입력 : 10
단을 잘못 입력하였습니다.

단 입력 : 
7 X 1 = 3
7 X 2 = 6
  .
  .
9 X 8 = 72
9 X 9 = 81
```


      File "<ipython-input-190-d03e651e6666>", line 1
        단 입력 : 10
          ^
    SyntaxError: invalid syntax
    



```python
while True:
    x = int(input("단 입력 : ")) 
    if x == 0:
        break
    elif x > 9 or x < 0 or x == 1:
        print("단을 잘못 입력하였습니다.")
    else:    
        while x < 10:
            for y in range(1,10):
                print("{} X {} = {}".format(x,y,x*y)) 
            x = x+1
```

    단 입력 : -3
    단을 잘못 입력하였습니다.
    단 입력 : -4
    단을 잘못 입력하였습니다.
    단 입력 : -5
    단을 잘못 입력하였습니다.
    단 입력 : -6
    단을 잘못 입력하였습니다.
    단 입력 : -1
    단을 잘못 입력하였습니다.
    단 입력 : 19
    단을 잘못 입력하였습니다.
    단 입력 : 10
    단을 잘못 입력하였습니다.
    단 입력 : 9
    9 X 1 = 9
    9 X 2 = 18
    9 X 3 = 27
    9 X 4 = 36
    9 X 5 = 45
    9 X 6 = 54
    9 X 7 = 63
    9 X 8 = 72
    9 X 9 = 81
    

# <font color='blue'> 12. 학생 이름과 수학점수를 입력받습니다. (아래 5번 반복)
# <font color='blue'> 입력) 이름 입력 : 홍길동
# <font color='blue'> 입력) 수학 점수 입력 : 78

.
# <font color='blue'> 5명을 입력받으면 더 이상 입력을 받지 않고 다음을 계산하여 출력합니다.
.

# <font color='blue'> 출력) 수학 점수 평균은 ... 점입니다.








# <font color='blue'> 13. 위에서 수학최고점수와 그 사람이 누군지 알아내어 아래처럼 출력합니다.

# <font color='blue'> "수학 최고점은 .. 점 이며, ... 입니다."








```python
my_dict = {}
```


```python
for i in range(5):
    x = input("이름 입력: ")
    y = input("수학 점수 입력: ")
    my_dict[int(y)] = x
print("수학 점수 평균은 {}점 입니다.".format((sum(my_dict.keys()))/5))
best = max(my_dict.keys())
print("수학 최고점은 {}점 이며, {}입니다.".format(best,my_dict[best]))

```

    이름 입력: A
    수학 점수 입력: 98
    이름 입력: B
    수학 점수 입력: 90
    이름 입력: C
    수학 점수 입력: 80
    이름 입력: D
    수학 점수 입력: 70
    이름 입력: E
    수학 점수 입력: 60
    수학 점수 평균은 79.6점 입니다.
    수학 최고점은 98점 이며, A입니다.
    


```python
my_dict
```




    {98: 'A', 90: 'B', 80: 'C', 70: 'D', 60: 'E'}



# <font color='blue'> 14. 해당 sms 문장에 스팸으로 등록한 단어가 있는지 검사하세요. 
## 스팸 단어 리스트 = [ '대출', '금리', '도박', '잭팟']
## 검사한 후, 스팸 단어가 있으면, "스팸"을 출력하고, 없으면 "스팸 아님"을 출력하세요.

## 문장 예 ) "최저 금리로 당일 송금, 대출 100만~3000만원 가능"


```python
sms = "최저 금리로 당일 송금, 대출 100만~3000만원 가능"
```


```python
sms = sms.strip(",")
```


```python
word = sms.split(" ")
```


```python
result = '스팸아님'
for word in spam_list :
    if word in sms :
        result = '스팸'

        break
print(result)        
```

    스팸
    
