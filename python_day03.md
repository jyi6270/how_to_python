#### boolean type
- True | False
- 논리연산자( not, and, or )
- 비교연산자( ~  , &  , |  )
- '', [], (), {}, 0, None -> False
- 0이 아닌 값들은 True


```python
a = 5 #0101
b = 0 #0000
print('bitwise - ', a&b)
print('bitwise - ', a|b)

print('bitwise - ', bool(a&b))
print('bitwise - ', bool(a|b))
print('boolean - ', bool(-1))
print()

tmp_list = []
tmp_str = ''
tmp_dict = {}
print('bool type - ', bool(tmp_list), bool(tmp_str), bool(tmp_dict))
print()

flag = True
print('bool type - ', int(flag), int(bool(tmp_list)))    # semi 불리언, 1 = 데이터가 있음


```

    bitwise -  0
    bitwise -  5
    bitwise -  False
    bitwise -  True
    boolean -  True
    
    bool type -  False False False
    
    bool type -  1 0
    


```python
print('논리연산자 -  and, or, not')
true_flag = True
false_flag = False

print('and - ', true_flag and false_flag)
print('or - ', true_flag or flase_flag)
print('not - ', not true_flag)
```

    논리연산자 -  and, or, not
    and -  False
    or -  True
    not -  False
    

#### date, datetime type
- install.packages() = conda install | pip install  # 아나콘다 명령프롬프트 - 관리자권한 실행
- library() = import, from ~ import ~
- xxxxx.py(module) - 변수, 함수
- 여러개의 모듈을 같은 네임스페이스로 관리 - package
- 함수 < 모듈 < 패키지
- 형식) import 모듈이름
- 형식) from 패키지명, 모듈 import 함수, 클래스
- 형식) from 패키지명 import 모듈
- 형식) from 모듈 import 함수, 클래스


```python
from datetime import date, datetime
```


```python
today = date.today()
print('type - ', type(today), today)
print('year - ', today.year, today.month, today.day)
print()

today_time = datetime.today()
print('type - ', type(today_time), today_time)
print('year month day - ', today_time.year, today_time.month, today_time.day)
print('hour minute second - ', today_time.hour, today_time.minute, today_time.second)
```

    type -  <class 'datetime.date'> 2022-09-26
    year -  2022 9 26
    
    type -  <class 'datetime.datetime'> 2022-09-26 10:14:34.949678
    year month day -  2022 9 26
    hour minute second -  10 14 34
    


```python
# 날짜에 대한 연산을 도와주는 함수
from datetime import timedelta
from dateutil.relativedelta import relativedelta
```


```python
# today + 1     -- error
# timedelta는 day에 대한 연산 작업만 제공
days = timedelta(days = 2)
print('type - ', type(days))
print(today + days)

days = timedelta(days = -2)
print('type - ', type(days))
print(today + days)
print()

# day 뿐만 아니라 연월일까지 하려면 relativedelta
days = relativedelta(days = 2)
months = relativedelta(months = 2)
years = relativedelta(years = 2)
print(today + days, today + months, today + years)
```

    type -  <class 'datetime.timedelta'>
    2022-09-28
    type -  <class 'datetime.timedelta'>
    2022-09-24
    
    


```python
# 특정날짜 생성시 문자열을 날짜로
from dateutil.parser import parse
user_date = parse('2022-09-26')
print('type - ', type(user_date))

today = datetime.today()
print('type - ', type(today))
```

    type -  <class 'datetime.datetime'>
    type -  <class 'datetime.datetime'>
    


```python
# 타입변환을 위한 함수 strftime(), strptime()
str_date = '2022-09-26'

user_date = datetime.strptime(str_date, '%Y-%m-%d')
print('문자 -> 날짜 - ', datetime.strptime(str_date, '%Y-%m-%d'))
print(type(datetime.strptime(str_date, '%Y-%m-%d')))

print('날짜 -> 문자 - ', user_date.strftime('%m-%d-%Y'), type(user_date.strftime('%m-%d-%Y')))

```

    문자 -> 날짜 -  2022-09-26 00:00:00
    <class 'datetime.datetime'>
    날짜 -> 문자 -  09-26-2022 <class 'str'>
    

#### input 함수


```python
name = input('enter your name : ')
name
```


```python
score = int(input('enter your score: '))
print('type - ', score *3, type(score))
```

#### 제어구문
- if ~
- 중첩형식 가능
- 블럭 :
- 들여쓰기(Indent)
- elif ~
- if ~ in


```python
score = int(input('점수를 입력하세요 : '))
if score >= 60 :
    print('통과')
else :
    print('과락')
```


```python
score = int(input('점수를 입력하세요 : '))
if score >= 90 :
    print('A')
elif score >= 80 :
    print('B')
elif score >= 70 :
    print('C')
elif score >= 60 :
    print('D')
else :
    print('F')
```

- input 함수를 이용해서 년도를 입력받고 해당 년도가 윤년인지 아닌지를 판단
- 조건) 4의 배수이고 100의 배수가 아니거나 400의 배수일 때


```python
year = int(input('연도를 입력하세요 : '))
if (year%4 == 0) & ~(year%100 == 0) | (year%400 == 0):
    print('윤년')
else:
    print('평년')
```


```python
area = ['천안', '세종', '대구']
region = str(input('지역 입력: '))

if region in area :
    print('exist')
else :
    print('{} 지역은 포함되지 않습니다.'.format(region))
```


```python
area = ['천안': 100, '세종': 200, '대구': 300]
region = str(input('지역 입력: '))

if region in area :
    print('exist')
else :
    print('{} 지역은 포함되지 않습니다.'.format(region))
```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
