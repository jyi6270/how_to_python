#### 반복구문
- for ~ in
- for ~ else
- while
- break, continue


```python
#for 변수 in seq collection :
#    <loop body>

for val in range(10) :
    print(val, end = '\t')
print()

for val in range(0, 10) :
    print(val, end = '\t')
print()

for val in range(0, 10, 2) :
    print(val, end = '\t')
print()
```

    0	1	2	3	4	5	6	7	8	9	
    0	1	2	3	4	5	6	7	8	9	
    0	2	4	6	8	
    


```python
#scores = []
for idx in range(10) :
    scores.append(int(input('성적을 입력하세요: ')))
```


```python
scores
```


```python
print('scores 총합을 구한다면 - ', sum(scores))
scores_sum = 0
for data in scores :
    scores_sum += data
print('sum - ', scores_sum)
print('avg - ', scores_sum / len(scores))
```


```python
ending_msg = 'see you next time'
print('type - ', type(ending_msg))

# 문자도 텍스트 시퀀스이기 때문에 루프 가능
for char in ending_msg:
    print(data, end = '')
```


```python
tmp_tuple = (5, 4, 6, 7, 1, 2, 9, 0)
print(dir(tmp_tuple))   # dir로 확인했을 때 '__iter__' 가 있으면 루프 가능
for tup in tmp_tuple :
    print(tup, end = ' ')
```


```python
print('리스트의 요소를 카운트 한다면? - ')
cnt_list  = [1,2,3,23,4,5,6,4,5,5,3,21,1,43,5,6,3,23,4,3,2,3,4,2,3,54,2,2,34,23,4,2,4,5,65,3,2,24,5,6,65,3]
freq = {}
for element in cnt_list:
    if element in freq :
        freq[element] += 1
    else:
        freq[element] = 1
print(freq)
```

    리스트의 요소를 카운트 한다면? - 
    {1: 2, 2: 7, 3: 8, 23: 3, 4: 6, 5: 6, 6: 3, 21: 1, 43: 1, 54: 1, 34: 1, 65: 2, 24: 1}
    


```python
# pip install import_ipynb

import import_ipynb
from random import randint
from python_note.user_module import user_sum

print('패키지.모듈의 함수 호출 - ', user_sum(10, 20))
```

    패키지.모듈의 함수 호출 -  30
    


```python
print('10고개 난수 맞추기 - ')
answer = randint(1,100)
print('answer - ', answer)

tries = 1

for idx in range(10) :
    guess = int(input('1 ~ 100 사이의 숫자를 입력하세요: '))
    if guess == answer :
        print('answer - ')
        break
    elif guess > answer :
        print('The number is big.')
    else :
        print('The number is small.')
    tries +=1

print('정답 {}, 시도횟수: {}'.format(answer, tries))
```


      Input In [10]
        for tries in len(1:10):
                          ^
    SyntaxError: invalid syntax
    



```python
# 올림픽 4년마다 개최
# 2020 ~ 2050 년 사이의 올림픽이 개최되는 연도 출력
# 한 줄에 5개의 년도 출력
# end =

cnt = 0
for year in range(2020, 2051, 4):
    cnt += 1
    if cnt%5 == 0 :
        print(year, end = '\n')
    else:
        print(year, end = '\t')
```

    2020	2024	2028	2032	2036
    2040	2044	2048	


```python
print('단을 입력받아 구구단을 출력 - ')
dan = int(input('단: '))

for i in range(1, 10) :
    print(dan, '*', i, '=', dan* i, end = '\t')
```

    단을 입력받아 구구단을 출력 - 
    단: 5
    5 * 1 = 5	5 * 2 = 10	5 * 3 = 15	5 * 4 = 20	5 * 5 = 25	5 * 6 = 30	5 * 7 = 35	5 * 8 = 40	5 * 9 = 45	


```python
print('구구단을 만든다면? - ')
for i in range(2, 10):
    print(i, '단- ')
    for j in range(1, 10):
        print(i, '*', j, '=', i*j, end = '\t')
    print()
    

print('3단까지만 출력 - ')
for i in range(2, 10):
    print(i, '단- ')
    for j in range(1, 10):
        print(i, '*', j, '=', i*j, end = '\t')
    if i == 3:
        break
    print()  
    
    
print('3단을 제외하고 출력 - ')
for i in range(2, 10):
    if i == 3:
        continue
    print(i, '단- ')
    for j in range(1, 10):
        print(i, '*', j, '=', i*j, end = '\t')
    print()
```

    구구단을 만든다면? - 
    2 단- 
    2 * 1 = 2	2 * 2 = 4	2 * 3 = 6	2 * 4 = 8	2 * 5 = 10	2 * 6 = 12	2 * 7 = 14	2 * 8 = 16	2 * 9 = 18	
    3 단- 
    3 * 1 = 3	3 * 2 = 6	3 * 3 = 9	3 * 4 = 12	3 * 5 = 15	3 * 6 = 18	3 * 7 = 21	3 * 8 = 24	3 * 9 = 27	
    4 단- 
    4 * 1 = 4	4 * 2 = 8	4 * 3 = 12	4 * 4 = 16	4 * 5 = 20	4 * 6 = 24	4 * 7 = 28	4 * 8 = 32	4 * 9 = 36	
    5 단- 
    5 * 1 = 5	5 * 2 = 10	5 * 3 = 15	5 * 4 = 20	5 * 5 = 25	5 * 6 = 30	5 * 7 = 35	5 * 8 = 40	5 * 9 = 45	
    6 단- 
    6 * 1 = 6	6 * 2 = 12	6 * 3 = 18	6 * 4 = 24	6 * 5 = 30	6 * 6 = 36	6 * 7 = 42	6 * 8 = 48	6 * 9 = 54	
    7 단- 
    7 * 1 = 7	7 * 2 = 14	7 * 3 = 21	7 * 4 = 28	7 * 5 = 35	7 * 6 = 42	7 * 7 = 49	7 * 8 = 56	7 * 9 = 63	
    8 단- 
    8 * 1 = 8	8 * 2 = 16	8 * 3 = 24	8 * 4 = 32	8 * 5 = 40	8 * 6 = 48	8 * 7 = 56	8 * 8 = 64	8 * 9 = 72	
    9 단- 
    9 * 1 = 9	9 * 2 = 18	9 * 3 = 27	9 * 4 = 36	9 * 5 = 45	9 * 6 = 54	9 * 7 = 63	9 * 8 = 72	9 * 9 = 81	
    3단까지만 출력 - 
    2 단- 
    2 * 1 = 2	2 * 2 = 4	2 * 3 = 6	2 * 4 = 8	2 * 5 = 10	2 * 6 = 12	2 * 7 = 14	2 * 8 = 16	2 * 9 = 18	
    3 단- 
    3 * 1 = 3	3 * 2 = 6	3 * 3 = 9	3 * 4 = 12	3 * 5 = 15	3 * 6 = 18	3 * 7 = 21	3 * 8 = 24	3 * 9 = 27	


```python
# 아래 리스트에서 세 글자 이상인 문자만 출력한다면?
# len()
print()

tmpList = ['I' , 'AM' , 'study' , 'PYTHON' , 'language' , '!']
for idx in range(len(tmpList)):
    if len(tmpList[idx]) > 3:
        print(tmpList[idx])

```

    
    study
    PYTHON
    language
    


```python
# 확장자를 제외하고 파일 이름만 출력한다면?
# split()
tmpList = ['greeting.py' , 'ex01.py' , 'intro.hwp' , 'bigdata.doc']

for idx in range(len(tmpList)):
    print((tmpList[idx].split('.'))[0])
```

    greeting
    ex01
    intro
    bigdata
    


```python
# 인덱스 번호와 요소값을 확인 할 수 있는 enumerate()
tmpList = ['greeting.py' , 'ex01.py' , 'intro.hwp' , 'bigdata.doc']

for idx, value in enumerate(tmpList) :
    print(idx, value)
```

    0 greeting.py
    1 ex01.py
    2 intro.hwp
    3 bigdata.doc
    


```python
# 분류정확도
answer = [1, 0, 2, 1, 0]
pridct = [1, 0, 2, 0, 0]
accuracy = 0
for idx in range(len(answer)) :
    fit = answer[idx] == pridct[idx]
    accuracy += int(fit) *20

print(accuracy, '%', sep='')
```

    80%
    

- for ~ else


```python
numbers = [14, 3, 4, 7, 45, 17, 8, 65, 43]
   
for idx, num in enumerate(numbers):
    #print(numbers[idx], end = '\t')
    if numbers[idx] == 45:
        print('Found - ', numbers[idx])
        break
else:
    print('Not Found- ')
```

    Found -  45
    


```python
apts = [[1, 2], [3, 4], [5, 6]]
for row in apts:
    for col in row:
        print(col, end = '\t')
    print()
```

    1	2	
    3	4	
    5	6	
    


```python
apts = [[1, 2], [3, 4], [5, 6]]
for i, row in enumerate(apts):
    for j, col in enumerate(row):
        if apts[i][j] == 3:
            print('i, j = ', i, j)
    print()
```

    
    i, j =  1 0
    
    
    

- for 문자열 처리


```python
tmp_str = \
'''저는 파이썬을 공부중인 조용일 입니다.
주소는 서울시 입니다.
나이는 숫자에 불과합니다.
항상 긍정의 마인드로 화이팅!!!'''
```


```python
print('몇 문장인지?')
print('문장의 단어들은 몇 단어인지를 확인하고 싶다면')

sentences = []
words = []
for s in tmp_str.split('\n'):
    sentences.append(s)
    for w in s.split():
        words.append(w)
print('문장의 개수- ', len(sentences))
print('단어의 개수- ', len(words))
    

```

    몇 문장인지?
    문장의 단어들은 몇 단어인지를 확인하고 싶다면
    문장의 개수-  4
    단어의 개수-  15
    

- while ~ else
- 반복 횟수를 알 수 없고 특정 조건 만족시까지
- 변수 생성 불가 True / False 판단
- 조건식 False가 될 때까지 무한반복


```python
# for 변수 in [튜플, 리스트, 문자열 등 반복 가능한 객체]:
#      수행구문

# 초기식
# while 조건식:
#     수행구문

n = 5
while n > 0 :
    print(n)
    n = n - 1

print('조건식이 false일 때 루프를 빠져나옴')
```

    5
    4
    3
    2
    1
    조건식이 false일 때 루프를 빠져나옴
    


```python
tmp_list = ['foo', 'bar', 'baz']
while tmp_list :
    print(tmp_list.pop())
```

    baz
    bar
    foo
    


```python
# 1~ 100까지의 합, 3의 배수이면서 5의 배수가 아닌 합  
# 출력 - while
n = 1
result = 0
cnt = 0
while n <= 100:
    cnt += n
    if n%3 == 0 and n%5 !=0:
        result += n
    n +=1
print(result)
print(cnt)
```

    1368
    5050
    


```python
n = 10
while n > 0 :
    n -= 1
    if n == 5 :
        break
else :
    print('while ~ else')
    

# else 를 출력하고 싶다면 조건을 반대로
n = 10
while n < 0 :
    n -= 1
    if n == 5 :
        break
else :
    print('while ~ else')
```

    while ~ else
    


```python
# 문)
# 10고개, 구구단 while로 변경
```


```python
answer = randint(1,100)
print(answer)

n = 1
while n <= 10:
    guess = int(input('1~100 사이의 숫자를 입력하세요: '))
    if guess == answer :
        print('answer - ')
        break
    elif guess > answer :
        print('The number is big.')
    else :
        print('The number is small.')
    n+=1
print('정답: {}, 시도횟수: {}'.format(answer, n))


# 왜 10번 시도하면 시도횟수가 11로 뜰까?

```

    26
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    1~100 사이의 숫자를 입력하세요: 8
    The number is small.
    정답: 26, 시도횟수: 11
    


```python
n = 2
m = 1
while n <= 9 :
    print(n, '단- ')
    while m <= 9 :
        print(n, '*', m, '=', n*m, end = '\t')
        m+=1
        if m == 10:
            break
    n +=1
    m = 1
```

    2 단- 
    2 * 1 = 2	2 * 2 = 4	2 * 3 = 6	2 * 4 = 8	2 * 5 = 10	2 * 6 = 12	2 * 7 = 14	2 * 8 = 16	2 * 9 = 18	3 단- 
    3 * 1 = 3	3 * 2 = 6	3 * 3 = 9	3 * 4 = 12	3 * 5 = 15	3 * 6 = 18	3 * 7 = 21	3 * 8 = 24	3 * 9 = 27	4 단- 
    4 * 1 = 4	4 * 2 = 8	4 * 3 = 12	4 * 4 = 16	4 * 5 = 20	4 * 6 = 24	4 * 7 = 28	4 * 8 = 32	4 * 9 = 36	5 단- 
    5 * 1 = 5	5 * 2 = 10	5 * 3 = 15	5 * 4 = 20	5 * 5 = 25	5 * 6 = 30	5 * 7 = 35	5 * 8 = 40	5 * 9 = 45	6 단- 
    6 * 1 = 6	6 * 2 = 12	6 * 3 = 18	6 * 4 = 24	6 * 5 = 30	6 * 6 = 36	6 * 7 = 42	6 * 8 = 48	6 * 9 = 54	7 단- 
    7 * 1 = 7	7 * 2 = 14	7 * 3 = 21	7 * 4 = 28	7 * 5 = 35	7 * 6 = 42	7 * 7 = 49	7 * 8 = 56	7 * 9 = 63	8 단- 
    8 * 1 = 8	8 * 2 = 16	8 * 3 = 24	8 * 4 = 32	8 * 5 = 40	8 * 6 = 48	8 * 7 = 56	8 * 8 = 64	8 * 9 = 72	9 단- 
    9 * 1 = 9	9 * 2 = 18	9 * 3 = 27	9 * 4 = 36	9 * 5 = 45	9 * 6 = 54	9 * 7 = 63	9 * 8 = 72	9 * 9 = 81	


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


```python

```
