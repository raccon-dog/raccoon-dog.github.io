# <font color='red'> 실습 </font> 
## <font color='red'> PRINT AND USER INPUT OPERATION </font> 

# <font color='blue'> 1. 유저한테서 KMH값을 입력 받으면, 그에 맞는 MPH로 변환하는 코드를 만드세요. 
MPH = 0.6214 * KMH</font> 


```python
KMH = float(input('KMH 값 입력 :'))
MPH = 0.6214 * KMH
print(MPH)
```

    KMH 값 입력 :212
    131.7368
    

# <font color='blue'>2.  유저한테 두개의 float을 입력받아서, 두 수의 곱과 합을, 다음처럼 똑같이 출력하는 코드를 만드세요.</font> 
## 출력형태 : First is 4.3, and second is 5.21. So, Multiplication = 22.403, addition = 9.51


```python
A = float(input("첫번쨰 숫자 입력 :"))
B = float(input("두번쨰 숫자 입력 :"))
C = A*B
D = A+B
print('First is {}, and second is {}. So, Multiplication = {}, addition = {}'.format(A,B,C,D))
```

    첫번쨰 숫자 입력 :4.3
    두번쨰 숫자 입력 :5.21
    First is 4.3, and second is 5.21. So, Multiplication = 22.403, addition = 9.51
    
