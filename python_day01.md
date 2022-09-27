```python
print('처음으로 만나는 파이썬 with jslim...')
```

    처음으로 만나는 파이썬 with jslim...
    

#### 파이썬 변수 및 주의사항
- 대소문자 구별
- 허용되는 특수문자: _, $
- 예약어는 변수 또는 함수명으로 사용 불가


```python
# 주석
```


```python
'''
변수
Built - In Type
- Numeric
- Sequence
- Text Sequence
- Set
- Mapping(dict, tupel)
- Boolean
- Class(Object Oriented Programming)
- Function

변수 지정방법
- Camel Case -> numberOfCollege   (변수, 함수)
- Pascal Case -> NumberOfCollege  (클래스)
- Snake Case -> number_of_college (변수, 함수)
'''
```




    '\n변수\nBuilt - In Type\n- Numeric\n- Sequence\n- Text Sequence\n- Net\n- Mapping(dict, tupel)\n- Boolean\n- Class(Object Oriented Programming)\n\n변수 지정방법\n- Camel Case -> numberOfCollege   (변수, 함수)\n- Pascal Case -> NumberOfCollege  (클래스)\n- Snake Case -> number_of_college (변수, 함수)\n'




```python
import keyword
print(keyword.kwlist)
```

    ['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
    


```python
print('Scalar Type - type()')

year = 2022
month = 9
day = 22

print('year type - ', type(year))
print('month type - ', type(month))
print('day type - ', type(day))
print()

floatValue = 3.14
print('float type - ', type(floatValue))
print()

booleanValue = True
print('boolean type - ', type(booleanValue))
print()

strValue = 'jslim'
print('string type - ', type(strValue))
print()

strValue = "jslim"
print('string type - ', type(strValue))
print()
```

    Scalar Type - type()
    year type -  <class 'int'>
    month type -  <class 'int'>
    day type -  <class 'int'>
    
    float type -  <class 'float'>
    
    boolean type -  <class 'bool'>
    
    string type -  <class 'str'>
    
    string type -  <class 'str'>
    
    


```python
print('순차형 - list')
print('인덱스로 관리되는 데이터(인덱싱, 슬라이싱)')
print('인덱스는 0부터')
tmp_list = ['jslim', 'python', 'django', 'numpy', 'pandas']
print()

print('data - ', tmp_list)
print('type - ', type(tmp_list))

print('indexing - ')
print(tmp_list[0])
print()

print('slicing - ')
print(tmp_list[0:3])         # 엔드 인덱스는 -1
print()
```

    순차형 - list
    인덱스로 관리되는 데이터(인덱싱, 슬라이싱)
    인덱스는 0부터
    
    data -  ['jslim', 'python', 'django', 'numpy', 'pandas']
    type -  <class 'list'>
    indexing - 
    jslim
    
    slicing - 
    ['jslim', 'python', 'django']
    
    


```python
print('*중요')
print('문자 순차형 - ')

txt_seq ='Talk is cheap. Show me the code'
print(txt_seq, type(txt_seq), len(txt_seq))
print()

print('talk slicing - ', txt_seq[0:4])

for char in txt_seq :                # {} 대신 :을 사용
    pass

print('블럭을 빠져 나왔다')
print()

for char in txt_seq :
    print(char)
```

    *중요
    문자 순차형 - 
    Talk is cheap. Show me the code <class 'str'> 31
    
    talk slicing -  Talk
    블럭을 빠져 나왔다
    
    T
    a
    l
    k
     
    i
    s
     
    c
    h
    e
    a
    p
    .
     
    S
    h
    o
    w
     
    m
    e
     
    t
    h
    e
     
    c
    o
    d
    e
    


```python
print('출력의 형식을 다르게 포맷팅할 수 있는 방법 - ')
print('print() : sep, end')
print()
print()

# 안에 작은 따옴표를 쓰려면 밖은 큰 따옴표
print("Speak Out. 'student'")
# 큰따옴표 3번 쓰면 내부에서 줄바꿈 인식
print("""우리는 분석을 위한 파이썬을 학습합니다.
그래서, 파이썬이 좋아요.
섭섭이도 좋아요.""")
print('오늘은', '목요일', '입니다')
print()

print('option - sep')
print('P', 'Y', 'T', 'H', 'O', 'N', sep = '\t')      # 공백을 tap으로
print('P', 'Y', 'T', 'H', 'O', 'N', sep = '')
print('P', 'Y', 'T', 'H', 'O', 'N', sep = '-')
print('python', 'org', sep = '.')
print('jslim9413', 'naver.com', sep = '@')
print()

print('option - end')
print('Welcome To', end = ' ')      # 줄바꿈 하지 않기
print('Web Site')
```

    출력의 형식을 다르게 포맷팅할 수 있는 방법 - 
    print() : sep, end
    
    
    Speak Out. 'student'
    우리는 분석을 위한 파이썬을 학습합니다.
    그래서, 파이썬이 좋아요.
    섭섭이도 좋아요.
    오늘은 목요일 입니다
    
    option - sep
    P	Y	T	H	O	N
    PYTHON
    P-Y-T-H-O-N
    python.org
    jslim9413@naver.com
    
    option - end
    Welcome To Web Site
    


```python
print('format (%d, %s, %f)')
print('format {}')
print('당신의 %s(은) %s이고 나이는 %d살 입니다.' %('이름은', '섭섭해', 24))
print('당신의 {}(은) {}이고 나이는 {}살 입니다.' .format('이름은', '섭섭해', 24))
print('당신의 {1}(은) {2}이고 나이는 {0}살 입니다.' .format(24, '이름은', '섭섭해'))
print()

print('%.2f' %(3.14159))               # 정수자리.소수점자리f
print('%1.2f' %(3.14159))
```

    format (%d, %s, %f)
    format {}
    당신의 이름은(은) 섭섭해이고 나이는 24살 입니다.
    당신의 이름은(은) 섭섭해이고 나이는 24살 입니다.
    당신의 이름은(은) 섭섭해이고 나이는 24살 입니다.
    
    3.14
    3.14
    


```python
txt_seq = 'Talk is cheap. Show me the code'
print('-index를 제공한다')
print('indexing - ', txt_seq[-1])         # 뒤에서부터 출력
print('slicing - ', txt_seq[-4 : ])
print()

print('[startindex : endindex : step]')
print('step - ', txt_seq[0 : len(txt_seq) : 2])    # 스텝: 처음부터 끝까지 두 칸씩 띄어서
print('step - ', txt_seq[  :  :  -1])
```

    -index를 제공한다
    indexing -  e
    slicing -  code
    
    [startindex : endindex : step]
    step -  Tl scep hwm h oe
    step -  edoc eht em wohS .paehc si klaT
    


```python
tmp_str = '홀짝홀짝홀짝홀짝홀짝홀짝홀짝홀짝'
print('type - ', type(tmp_str))
print()

print('짝만 출력 - ', tmp_str[ 1: : 2])
print('홀만 출력 - ', tmp_str[ 0: : 2])
```

    type -  <class 'str'>
    
    짝만 출력 -  짝짝짝짝짝짝짝짝
    홀만 출력 -  홀홀홀홀홀홀홀홀
    


```python
print('문자열 함수 - upper(), startswith(), count(), endswith(), ...')
print('사용법 - 문자열변수.함수()')

tmp_str = 'python'
print('capitalize - ', tmp_str.capitalize())
print('upper - ', tmp_str.upper())

tmp_str = '010-4603-2283'
print('replace - ', tmp_str.replace('-', ' '))

tmp_str = 'http://www.naver.com'
print('도메인만 추출 - ', tmp_str[-3: ])
print('도메인만 추출 - ', tmp_str[tmp_str.find('com'): ])
```

    문자열 함수 - upper(), startswith(), count(), endswith(), ...
    사용법 - 문자열변수.함수()
    capitalize -  Python
    upper -  PYTHON
    replace -  010 4603 2283
    도메인만 추출 -  com
    도메인만 추출 -  com
    


```python
tmp_str = 'http://www.naver.com'
print('주소와 도메인을 분리 - ', tmp_str.split('.'))
print('주소와 도메인을 분리 - ', type(tmp_str.split('.')))
```

    주소와 도메인을 분리 -  ['http://www', 'naver', 'com']
    주소와 도메인을 분리 -  <class 'list'>
    


```python
tmp_str = '    multicampus    '
print('공백제거 후 데이터 추출 - ', tmp_str.lstrip(), len(tmp_str.lstrip()))
print('공백제거 후 데이터 추출 - ', tmp_str.rstrip(), len(tmp_str.rstrip()))
print('공백제거 후 데이터 추출 - ', tmp_str.strip(), len(tmp_str.strip()))
```

    공백제거 후 데이터 추출 -  multicampus     15
    공백제거 후 데이터 추출 -      multicampus 15
    공백제거 후 데이터 추출 -  multicampus 11
    


```python
tmp_str = '보고서.xls'
print('확장자가 xls로 끝나는지 확인 - ', tmp_str.endswith(('xls', 'xlsx')))

tmp_str = '2022_보고서.xls'
print('XXXX 시작하는 문서를 확인 - ', tmp_str.startswith(('2022')))
```

    확장자가 xls로 끝나는지 확인 -  True
    


```python
print('set - type')

tmp_set = {3,5,7,3}         # 중복 허용 X
print('data - type : ', tmp_set, type(tmp_set))
```

    set - type
    data - type :  {3, 5, 7} <class 'set'>
    


```python
print('Mapping - dict, tuple')
print()


tmp_dict = {}        # 중괄호 비어있으면 타입이 딕셔너리
print('data - type : ', tmp_dict, type(tmp_dict))

tmp_dict = {
    'name'  : 'machine Learning',        # 키밸류 형식 매핑
    'version'  : 2.0
}
print('data - type : ', tmp_dict, type(tmp_dict))
print()


tmp_tuple = ()        # 소괄호는 튜플
print('data - type : ',  tmp_tuple, type(tmp_tuple))

tmp_tuple = (1,)        # 숫자 하나만 들어가면 int가 되므로 , 를 찍어야함
print('data - type : ',  tmp_tuple, type(tmp_tuple))

tmp_tuple = ('name', 'python'), ('version', 2.0)
print('data - type: ', tmp_tuple, type(tmp_tuple))

```

    Mapping - dict, tuple
    
    data - type :  {} <class 'dict'>
    data - type :  {'name': 'machine Learning', 'version': 2.0} <class 'dict'>
    
    data - type :  () <class 'tuple'>
    data - type :  (1,) <class 'tuple'>
    data - type:  (('name', 'python'), ('version', 2.0)) <class 'tuple'>
    


```python
print('조건판단 boolean - True, False')
print('in 연산자 - ')
tmp_str = 'apple banana pineapple mango grape melon'
print('data - ', tmp_str)
print()
print('apple' in tmp_str)
print('Apple'.lower() in tmp_str)
```

    조건판단 boolean - True, False
    in 연산자 - 
    data -  apple banana pineapple mango grape melon
    
    True
    True
    


```python
def userFunction() :
    print('함수도 변수의 타입이다.')
```


```python
tmp_func = userFunction
print('type - ', tmp_func)
```

    type -  <function userFunction at 0x000002210262CF70>
    

#### list ***
- array 아님, R- Vector
- 순서 O, 중복 O, 수정 삭제 가능
- 선언: [], list()
- 순서가 존재하므로 indexing, slicing(index 0 ~)


```python
tmp_list = []
print('type - ', type(tmp_list))

tmp_list = [1, 2, 3, 4, 5, 'Jslim', ['show', 'me', 'the', 'money']]
print('type - ' , type(tmp_list))
print('data - ' , tmp_list)
print()

# 리스트만 추출
extract= tmp_list[-1]
print('type - ', type(extract))
print('data - ', extract)
# show만 추출
extract= tmp_list[-1][0]
print('type - ', type(extract))
print('data - ', extract)
```

    type -  <class 'list'>
    type -  <class 'list'>
    data -  [1, 2, 3, 4, 5, 'Jslim', ['show', 'me', 'the', 'money']]
    
    type -  <class 'list'>
    data -  ['show', 'me', 'the', 'money']
    type -  <class 'str'>
    data -  show
    


```python
# 파이썬 내장함수 https://docs.python.org/ko/3/library/functions.html
https://docs.python.org/3.9/library/index.html

x_list = [1,2,3]
y_list = [4,5]
print('list 연산 - ')
print('+', x_list + y_list)
z_list = x_list + y_list
print('+', z_list, type(z_list))

print('새로운 데이터 추가 - ')
z_list.append(1)
print(z_list)

print('새로운 데이터 원하는 인덱스번지에 추가 - insert')
z_list.insert(1, 6)
print(z_list)

print('정렬 - sort')
z_list.sort()
print(z_list)

print('내림차순 정렬 - reverse')
z_list.reverse()
print(z_list)

print('추출 - ')
print('indexing - ' , z_list[0], z_list)
print('pop - ', z_list.pop(0), z_list)       # 원본 데이터에서 아예 추출

print('인덱스 번지를 원할 때 - ', z_list.index(5), z_list[z_list.index(5)])

print('삭제 - del, remove(data)', z_list.remove(1), z_list)   # 한 번만 삭제

print('중복 개수를 확인하고자 할 때 - ', z_list.count(5))

print(z_list)
tmp_list = [8,9,10]
print('extend - ')
z_list.extend(tmp_list)    # 요소만 추가
z_list.append(tmp_list)    # 리스트를 그대로 추가
z_list = z_list + tmp_list # 요소만 추가, 변수에 할당해야함
print(z_list)     
```

    list 연산 - 
    + [1, 2, 3, 4, 5]
    + [1, 2, 3, 4, 5] <class 'list'>
    새로운 데이터 추가 - 
    [1, 2, 3, 4, 5, 1]
    새로운 데이터 원하는 인덱스번지에 추가 - insert
    [1, 6, 2, 3, 4, 5, 1]
    정렬 - sort
    [1, 1, 2, 3, 4, 5, 6]
    내림차순 정렬 - reverse
    [6, 5, 4, 3, 2, 1, 1]
    추출 - 
    indexing -  6 [6, 5, 4, 3, 2, 1, 1]
    pop -  6 [5, 4, 3, 2, 1, 1]
    인덱스 번지를 원할 때 -  0 5
    삭제 - del, remove(data) None [5, 4, 3, 2, 1]
    중복 개수를 확인하고자 할 때 -  1
    [5, 4, 3, 2, 1]
    extend - 
    [5, 4, 3, 2, 1, 8, 9, 10]
    


```python
# ---- 실습
movie_rank = ['그루엘라' , '랑종' , '모가디슈' , '블랙위도우' , '강철비2' , '반도' , '킹덤']
'''
1. 배드맨을 마지막에 추가
2. 랑종과 모가디슈 사이에 임정섭을 추가
3. 블랙위도우 삭제
4. 모가디슈와 강철비2 삭제
5. 그루엘라의 인덱스를 구해서 pop()함수를 이용한 삭제
6. 최종 리스트 출력 
'''
movie_rank.append('배드맨')
print(movie_rank)

movie_rank.insert(2, '임정섭')
print(movie_rank)

movie_rank.remove('블랙위도우')
print(movie_rank)

movie_rank.remove('모가디슈')
print(movie_rank)

movie_rank.remove('강철비2')
print(movie_rank)

movie_rank.index('그루엘라')
movie_rank.pop(0)
print(movie_rank)



```

    ['그루엘라', '랑종', '모가디슈', '블랙위도우', '강철비2', '반도', '킹덤', '배드맨']
    ['그루엘라', '랑종', '임정섭', '모가디슈', '블랙위도우', '강철비2', '반도', '킹덤', '배드맨']
    ['그루엘라', '랑종', '임정섭', '모가디슈', '강철비2', '반도', '킹덤', '배드맨']
    ['그루엘라', '랑종', '임정섭', '강철비2', '반도', '킹덤', '배드맨']
    ['그루엘라', '랑종', '임정섭', '반도', '킹덤', '배드맨']
    ['랑종', '임정섭', '반도', '킹덤', '배드맨']
    


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
