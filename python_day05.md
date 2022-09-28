#### 함수 function - method(oop)


```python
data = [1,3,5,7,9]
tot = 0
for val in data :
    tot += val
print('누적 값 확인 - ', tot)
```

    누적 값 확인 -  25
    


```python
def total_calc() :
    pass
print('정의된 함수를 호출 - ', total_calc())
```


```python
def total_calc(lst) :
    total = 0
    for val in lst:
        total += val
    return total

print('정의된 함수를 호출 - ', total_calc(data))
value = total_calc(data)
print('total - ', value)
```

    정의된 함수를 호출 -  25
    total -  25
    


```python
import import_ipynb
from python_note.user_module import *
print(tot_calc(data))

import import_ipynb
from python_note import user_module
print(user_module.tot_calc(data))

```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Input In [15], in <cell line: 3>()
          1 import import_ipynb
          2 from python_note.user_module import *
    ----> 3 print(tot_calc(data))
          5 import import_ipynb
          6 from python_note import user_module
    

    NameError: name 'tot_calc' is not defined


- 함수의 유형


```python
def printGreeting01() :
    print('이제 함수를 살펴보겠습니다. 유형 1 - 인자 X, 리턴X')
    
printGreeting01()
```

    이제 함수를 살펴보겠습니다. 유형 1 - 인자 X, 리턴X
    


```python
def printGreeting02(msg) :
    print('유형2 - 인자 O, 리턴 X')

printGreeting02('jslim')
#printGreeting02() - error
```

    유형2 - 인자 O, 리턴 X
    


```python
def printGreeting03():
    print('유형 3 - 인자X, 리턴 O')
    return(1,2)

#printGreeting03('jslim') - error
x, y = printGreeting03()  #- 언패킹
print('x- ', x)
print('y- ', y)
```

    유형 3 - 인자X, 리턴 O
    x-  1
    y-  2
    


```python
# 인자로 들어온 값의 범위에서 홀수의 합, 짝수의 합을 리턴
def printGreting04(start: int, end: int) :
    print('유형 4 - 인자 O, 리턴 O')
    oddSum = evenSum = 0
    for val in range(start, end+1) :
        if val %2 == 0 :
            evenSum += val
        else :
            oddSum += val
    return oddSum, evenSum      #-튜플로 리턴

odd, even = printGreeting04(1, 100)
print('홀수의 합 - ', odd)
print('짝수의 합 - ', even)
```


```python
# 입력받은 문자열에 인터넷 주소를 반환하는 함수를 정의
# - naver -> www.naver.com
# - makeUrl()

def makeUrl(str) :
    return 'www.'+str+'.com'

result = makeUrl('naver')
print(result)
```

    www.naver.com
    


```python
urls = ['naver', 'google', 'samsung', 'lg', 'sk', 'multicampus']
#url_list = makeUrls(urls)
#print(url_list)

def makeUrls(lst : list) :
    result = []
    for url in lst:
        result.append('www.'+url+'.com')
    return result
    
url_list = makeUrls(urls)
print(url_list)
```

    ['www.naver.com', 'www.google.com', 'www.samsung.com', 'www.lg.com', 'www.sk.com', 'www.multicampus.com']
    


```python
#list Comprehension
def makeUrls(lst):
    result = ['www.'+url+'.com' for url in lst]
    return result
url_list = makeUrls(urls)
print(url_list)
```

    ['www.naver.com', 'www.google.com', 'www.samsung.com', 'www.lg.com', 'www.sk.com', 'www.multicampus.com']
    


```python
# 숫자로 구성된 리스트를 입력받아 짝수들을 추출해서 반환하는 pickEven() 함수
user_list = [3, 5, 4, 10, 32, 6, 9, 13, 20]

def pickEven(lst):
    result = [ val for val in lst if val %2 == 0]
    return result

even_list = pickEven(user_list)
print(even_list)
```

    [4, 10, 32, 6, 20]
    


```python
# flag T = 좋아, F = 싫어하는 것
# 출력예시) xxx님은 xxx색을 좋아(싫어)합니다
def favorite_color(name, color, flag):
    if flag == True :
        print('{}님은 {}색을 좋아합니다.'.format(name, color))
    else :
        print('{}님은 {}색을 싫어합니다.'.format(name, color))


favorite_color('섭섭해', '빨강', False)
favorite_color('김기쁨', '하늘', True)
favorite_color('정상환', '보라', False)

```

    섭섭해님은 빨강색을 싫어합니다.
    김기쁨님은 하늘색을 좋아합니다.
    정상환님은 보라색을 싫어합니다.
    


```python
user_info_list = [{'name': '섭섭해', 'color': '빨간색', 'flag' : False},
                 {'name': '김기쁨', 'color': '하늘색', 'flag' : True},
                 {'name': '정상환', 'color': '보라색', 'flag' : False}]

def favorite_color_list01(lst: list):
    for dict in lst:
        if dict['flag'] == True:
            print(dict['name'],'님은', dict['color'],'을 좋아합니다.')
        else:
            print(dict['name'],'님은', dict['color'],'을 싫어합니다.')
        
favorite_color_list01(user_info_list)



def favorite_color_list02(lst: list):
    for idx in range(len(lst)):
        if lst[idx]['flag'] :
            print('{}님은 {}을 좋아합니다.'.format(lst[idx]['name'], lst[idx]['color']))
        else:
            print('{}님은 {}을 싫어합니다.'.format(lst[idx]['name'], lst[idx]['color']))
            
favorite_color_list02(user_info_list)
```

    섭섭해 님은 빨간색 을 싫어합니다.
    김기쁨 님은 하늘색 을 좋아합니다.
    정상환 님은 보라색 을 싫어합니다.
    섭섭해님은 빨간색을 싫어합니다.
    김기쁨님은 하늘색을 좋아합니다.
    정상환님은 보라색을 싫어합니다.
    

- 가변인수 args, kwargs


```python
# 하나의 *는 함수 인자로 튜플을 받는다는 뜻
def average(*scores):
    sum = 0
    for idx in range(len(scores)) :
        sum += scores[idx]
    print('sum - ', sum)
    avg = sum / len(scores)
    print('%d 과목의 평균은: %f' % (len(scores), avg))

average(100)
average(100, 80, 74)
average(100,80, 74, 23, 53)
```

    sum -  100
    1 과목의 평균은: 100.000000
    sum -  254
    3 과목의 평균은: 84.666667
    sum -  330
    5 과목의 평균은: 66.000000
    


```python
print('** 딕셔너리를 인자로 받는 것을 의미함 - ')
print('함수 정의 worker - ')
def kwargsDict(** kwargs) :
    for key, value in kwargs.items() :
        print('key = {}, value = {}'.format(key, value))
    print('*'*50)

print('함수 호출 caller - ')
kwargsDict(name = 'jslim')
kwargsDict(name = 'jslim', age = 24)
kwargsDict(name = 'jslim', age = 24, gender = 'm')
    
```

    ** 딕셔너리를 인자로 받는 것을 의미함 - 
    함수 정의 worker - 
    함수 호출 caller - 
    key = name, value = jslim
    **************************************************
    key = name, value = jslim
    key = age, value = 24
    **************************************************
    key = name, value = jslim
    key = age, value = 24
    key = gender, value = m
    **************************************************
    


```python
def printCoin():
    for idx in range(0, 10):
        print('coin')
```


```python
# type - function
coin = printCoin
coin()
```

    coin
    coin
    coin
    coin
    coin
    coin
    coin
    coin
    coin
    coin
    


```python
# 만약 가변인수와 일반데이터가 혼용되어 있다면

def mixType(args01, args02, *args03, **args04):
    print('args01 - ', args01)
    print('args02 - ', args02)
    print('args03 - ', args03)
    print('args04 - ', args04)

    
    
print('함수 호출 caller - ')
mixType(10, 20, 'lim', 'kim', 'park', 'moon', 'cho', age = 24, gender = 'f', address = 'seoul')
```

    함수 호출 caller - 
    args01 -  10
    args02 -  20
    args03 -  ('lim', 'kim', 'park', 'moon', 'cho')
    args04 -  {'age': 24, 'gender': 'f', 'address': 'seoul'}
    

- 함수의 인자로 함수전달이 가능. 즉, 함수를 인자로 넘겨줄 수 있음


```python
from statistics import *

def userStatistics(func, *data):
    if func == 'sum':
        print(sum(data))
    if func == 'mean':
        print(mean(data))
    if func == 'stdev':
        print(stdev(data))
        
print('함수 호출 caller - ')
userStatistics('sum',1, 2, 3, 4, 5, 6, 7)
userStatistics('mean',1, 2, 3, 4, 5)
userStatistics('stdev',1, 2, 3)
```

    함수 호출 caller - 
    28
    3
    1.0
    


```python
def userStatistics(func, *data):
    print(func(data))
    
print('함수 호출 caller - ')
userStatistics(sum,1, 2, 3, 4, 5, 6, 7)
userStatistics(mean,1, 2, 3, 4, 5)
userStatistics(stdev,1, 2, 3)
```

    함수 호출 caller - 
    28
    3
    1.0
    

- 지역 변수(Local Variable) : 블럭 내에서만 유효
- 전역 변수(Global Variable) : 하위의 모든 함수에서 사용가능한 유효범위를 갖는다


```python
# 지역변수를 전역변수로 
def func() :
    global xxx
    xxx = 100
    print('inner func print - ', xxx)
    print('address - ', id(xxx))
    
print('caller - ')
xxx = 10
print('outer func print - ', xxx)
func()
print('outer func print - ', xxx)
print('address - ', id(xxx))
```

    caller - 
    outer func print -  10
    inner func print -  100
    address -  2560839996880
    outer func print -  100
    address -  2560839996880
    

- 람다(lambda)
- 형식) lambda 매개변수 : 표현식


```python
def hap(x, y):
    return x + y

result = hap(10, 20)
print('result - ', result)
```

    result -  30
    


```python
result = lambda x, y : x+y (10, 20)
print('result - ', result)

result = (lambda x, y : x+y) (10, 20)
print('result - ', result)

func = lambda x, y : x+y
result = func(10, 20)
print('result - ', result)



def func_final(x, y, func):
    print('>>>>', func(x,y))

print('caller - ')
func_final(10, 20, lambda x, y: x+y)
```

    result -  <function <lambda> at 0x0000025444DEF700>
    result -  30
    result -  30
    caller - 
    >>>> 30
    

- util 함수 (zip, map, reduce)
- map: 리스트로부터 요소를 하나씩 꺼내서 함수를 적용시킨 다음, 그 결과를 새로운 리스트에 담아서 리턴
- reduce: 누적값을 리턴하는 함수
- filter: 조건에 만족하는 데이터만 리스트에 담아서 리턴


```python
# map(함수, 리스트)

print('map - ', list(map(lambda x : x **2, range(5)) ))
```

    map -  [0, 1, 4, 9, 16]
    


```python
# reduce(함수, 시퀀스)

from functools import reduce
print('reduce - ', reduce(lambda x, y : x + y, range(5)))
print('reduce - ', reduce(lambda x, y : y + x, 'abcde' ))
```

    reduce -  10
    reduce -  edcba
    


```python
# filter(함수, 리스트)
print('filter - ', list(filter(lambda x : x%2 == 0 , range(21))))

```

    filter -  [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
    


```python
print('hint - ')
def user_length(word : str, num : int) -> None:
    print('hint - ', len(word) * num)
    
    
user_length('good Teacher', 1)
```

    hint - 
    hint -  12
    


```python

```


```python

```


```python

```


```python

```
