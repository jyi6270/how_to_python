list


```python
# [], list()
# 형변환 함수
num_list = [1,2,3,4,5,6,7]
print('type - ', type(num_list), 'casting - ', bool(num_list))

print('max - ', max(num_list))
print('min - ', min(num_list))
print('sum - ', sum(num_list))
print('mean - ', sum(num_list) / len(num_list))
```

    type -  <class 'list'> casting -  True
    max -  7
    min -  1
    sum -  28
    mean -  4.0
    


```python
tmp_list01 = [1,2,3]
tmp_list02 = [1,2,3]
print('instance address - ', id(tmp_list01), id(tmp_list02))
print()

print('is 연산자 - 주소값을 비교 - ', tmp_list01 is tmp_list02)
print()

# 하나의 변수를 참조하기 때문에 같은 주소
tmp_list03 = tmp_list01
print('is 연산자 - 주소값을 비교 - ', tmp_list01 is tmp_list03)
print()

# tmp3에 변수를 추가해도 tmp1에도 추가됨
tmp_list03.append('jslim')
print('tmp_list03.append - ', tmp_list01 )
```

    instance address -  2085071513152 2085071681728
    
    is 연산자 - 주소값을 비교 -  False
    
    is 연산자 - 주소값을 비교 -  True
    
    tmp_list03.append -  [1, 2, 3, 'jslim']
    


```python
# copy를 사용하여 값만 복사하면 주소값이 다름
from copy import copy

tmp_list04 = copy(tmp_list02)

print('instance address - ', id(tmp_list02), id(tmp_list04))
print()

tmp_list04.append('jslim')
print('tmp_list04 append - ', tmp_list02)

```

    instance address -  2085071681728 2085043446784
    
    tmp_list04 append -  [1, 2, 3]
    


```python
# inner list: [ [], [] ]
# range() : 숫자를 sequence

tmp_range = range(10)
print('type - ', type(tmp_range))
print('data - ', tmp_range)
print('range - ', 10 in tmp_range)

for value in tmp_range :
    print(value, end = '\t')
print()

print()
print('indexing - ', tmp_range[0], tmp_range[0:5])
```

    type -  <class 'range'>
    data -  range(0, 10)
    range -  False
    0	1	2	3	4	5	6	7	8	9	
    
    indexing -  0 range(0, 5)
    


```python
# range(start, end, step)
# range(end)
# range(start, end)

import random

tmp_list = []
for idx in range(5) :
    tmp_list.append(random.randint(1,5))
    
print('tmp_list - ' , tmp_list)
print()

# 정렬
print('sort - ')
tmp_list.sort(reverse = True)
print(tmp_list)
```

    tmp_list -  [2, 3, 2, 3, 1]
    
    sort - 
    [3, 3, 2, 2, 1]
    


```python
print('list 요소를 찾고자 할 때 - in', 5 in tmp_list)
if 5 in tmp_list :
    print('find~~~')
else:
    print('can not find')
```

#### list Comprehension


```python
tmp_list = [2, 4, 1, 5, 3]

for value in tmp_list :
    print(value, end = '\t')
    
print()

for idx in range(len(tmp_list)):
    print(tmp_list[idx], end = '\t')
    
print()

tmp_list_square = []
for idx in range(len(tmp_list)) :
    tmp_list_square.append(tmp_list[idx] ** 2)
print(tmp_list_square, end = '\t')

```

    2	4	1	5	3	
    2	4	1	5	3	
    [4, 16, 1, 25, 9]	


```python
'''
변수 = [실행문 for 변수 in 열거형객체]
변수 = [실행문 for 변수 in 열거행객체 if 조건식]
'''

tmp_list_square = [ value ** 2 for value in tmp_list ]
print(tmp_list_square)
print()

tmp_list_square = [ value ** 2 for value in tmp_list if value%3 == 0]
print(tmp_list_square)
print()

result = []
for value in tmp_list :
    calc = value**2
    if calc%3 == 0 :
      result.append(calc)
print('for + if -> result, ', result)


```

    [4, 16, 1, 25, 9]
    
    [9]
    
    for + if -> result,  [9]
    


```python
# range() 함수를 이용해서 1~100 사이의 3의 배수만 출력
# for, list Comprehension
result = []
for value in range(1,101) :
    if value%3 == 0 :
     result.append(value)
print('result - ', result)
print()

tmp_result = [ value for value in range(1,101) if value%3 == 0]
print('result - ', tmp_result)
print()


# 1.
result = []
for value in range(1, 101):
    if value % 3  == 0 :
        result. append(value)
print('1.' 'for + if  -> result ', result)
print()

# 2.
tmp_result= [ value for value in range(1, 101) if value % 3 == 0]
print('2. ', tmp_result)

```

    result -  [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99]
    
    result -  [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99]
    1.for + if  -> result  [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99]
    
    2.  [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99]
    

#### tuple type
- 선언: (), tuple()
- 순서 O(indexing, slicing), 중복 O, (수정,삭제) X Immutable
- 읽기 전용


```python
# tmp_tuple = (3, )
# 괄호 없이 사용 가능
tmp_tuple = 1,2,3,4,5,4

print('type - ', type(tmp_tuple), bool(tmp_tuple))
print('data - ', tmp_tuple)
print('indexing - ', tmp_tuple[4])
print('slicing - ', tmp_tuple[0:2])
```

    type -  <class 'tuple'> True
    data -  (1, 2, 3, 4, 5, 4)
    indexing -  5
    slicing -  (1, 2)
    


```python
# 수정 x
# tmp_tuple[4] = 6  #error

# 튜플은 수정, 삭제가 안 된다.
# 삭제하고 싶은 데이터가 있다면? 형변환

tmp_list = list(tmp_tuple)
print('type - ', type(tmp_list))
print('data - ', tmp_list)
tmp_list.remove(3)
print('data - ', tmp_list)
tmp_list.append(6)
print('data - ', tmp_list)

# list -> tuple
tmp_tuple = tuple(tmp_list)
print('type - ', type(tmp_tuple))
print('data - ', tmp_tuple)
```

    type -  <class 'list'>
    data -  [1, 2, 3, 4, 5, 4]
    data -  [1, 2, 4, 5, 4]
    data -  [1, 2, 4, 5, 4, 6]
    type -  <class 'tuple'>
    data -  (1, 2, 4, 5, 4, 6)
    

#### tuple Packing & Unpacking


```python
packing = ('김기쁨', '최진형', '정상환', '장수빈', '한은석')
packing
```




    ('김기쁨', '최진형', '정상환', '장수빈', '한은석')




```python
# 변수의 개수가 맞아야함
a, b, c, d, e = packing
print(a, b, c, d, e)

# 변수 개수가 맞지 않는 경우
a, *b, c = packing
print(a, b, c)
```

    김기쁨 최진형 정상환 장수빈 한은석
    김기쁨 ['최진형', '정상환', '장수빈'] 한은석
    


```python
def userFunction() :
    num_list = [1,2,3,4,5,6,7]
    
    data_max = max(num_list)
    data_min = min(num_list)
    data_sum = sum(num_list)
    data_avg = sum(num_list) / len(num_list)
    
    return (data_max, data_min, data_sum, data_avg)
```


```python
data_max, data_min, data_sum, data_avg = userFunction()
print(data_max, data_min, data_sum, data_avg)
```

    7 1 28 4.0
    

#### dict type
- {}, dict()
- 순서 X, 키 중복 X, (수정, 삭제) O
- 주의사항: 키값으로 list, set X(불변의 타입이 정의되어야 한다)


```python
tmp_dict = {
    'name' : 'jslim' ,
    'address' : 'seoul'
}
print('type - ', type(tmp_dict), bool(tmp_dict))
print('data - ', tmp_dict)
print('키 유무를 판단하고 싶다면?', 'name' in tmp_dict)
print('키를 통한 데이터 접근 - ', tmp_dict['name'])
print('키를 통한 데이터 변경 - ')
tmp_dict['name'] = '섭섭해'
print('data - ', tmp_dict)

tmp_dict['gender'] = 'N'
print('data - ', tmp_dict)
```

    type -  <class 'dict'> True
    data -  {'name': 'jslim', 'address': 'seoul'}
    키 유무를 판단하고 싶다면? True
    키를 통한 데이터 접근 -  jslim
    키를 통한 데이터 변경 - 
    data -  {'name': '섭섭해', 'address': 'seoul'}
    data -  {'name': '섭섭해', 'address': 'seoul', 'gender': 'N'}
    


```python
tmp_dict = {
    'melon' : [300, 20],
    'bibibig' : [400, 20],
    'bravo' : [150, 10]
}
print(tmp_dict)
print('키를 통한 데이터 추출 - ')
melon_list = tmp_dict['melon']
print('type - ', type(melon_list), melon_list)
print('메로나 가격을 10% 인상한다면? - ')
melon_list[0] = int(melon_list[0]*1.1)
print('type - ', type(melon_list), melon_list)
```

    {'melon': [300, 20], 'bibibig': [400, 20], 'bravo': [150, 10]}
    키를 통한 데이터 추출 - 
    type -  <class 'list'> [300, 20]
    메로나 가격을 10% 인상한다면? - 
    type -  <class 'list'> [330, 20]
    


```python
tmp_dict = {
    'melon' : {'price': 300, 'qty' : 20},
    'bibibig' : {'price': 500, 'qty' : 30},
    'bravo' : {'price': 150, 'qty' : 10}
}

print('키를 통한 데이터 추출 - ')
melon_dict = tmp_dict['melon']
print('type - ', type(melon_dict), melon_dict)
print()

melon_dict['qty'] = 50
print('수량변경 20 -> 50', melon_dict)
print()

print('bravo 추출')
print('가격인상 한다면?')

bravo_list = tmp_dict['bravo']
print('type - ', type(bravo_list), bravo_list, bravo_list[0])

```

    키를 통한 데이터 추출 - 
    type -  <class 'dict'> {'price': 300, 'qty': 20}
    
    수량변경 20 -> 50 {'price': 300, 'qty': 50}
    
    bravo 추출
    type -  <class 'dict'> {'price': 150, 'qty': 10}
    


```python
tmp_dict = {
    'melon' : {'price': 300, 'qty' : 20},
    'bibibig' : {'price': 500, 'qty' : 30},
    'bravo' : [('price', 150), ('qty', 10)]
}
print()

print('bravo 추출')
print('가격인상 한다면?')

bravo_list = tmp_dict['bravo']
print('type - ', type(bravo_list), bravo_list, bravo_list[0])

bravo_tuple = bravo_list[0]
bravo_price_list = list(bravo_tuple)
bravo_price_list[1] = 1000
bravo_list[0] = tuple(bravo_price_list)
print('type - ', type(bravo_list), bravo_list, bravo_list[0])

print(tmp_dict)
```

    
    bravo 추출
    가격인상 한다면?
    type -  <class 'list'> [('price', 150), ('qty', 10)] ('price', 150)
    type -  <class 'list'> [('price', 1000), ('qty', 10)] ('price', 1000)
    {'melon': {'price': 300, 'qty': 20}, 'bibibig': {'price': 500, 'qty': 30}, 'bravo': [('price', 1000), ('qty', 10)]}
    


```python
# dict()
tmp_dict = dict(
    city = 'kwangju',
    age = 30
)
print('type - ', type(tmp_dict), tmp_dict)

# error
#print('key 이용 데이터 추출 - ',  tmp_dict['address'])
print('key 이용 데이터 추출 - ',  tmp_dict.get(0))   #-- key 값으로 가져와야 함
print('key 이용 데이터 추출 - ', tmp_dict.get('city'))
print('update() 요소 추가가능 - ', tmp_dict.update({'job' : 'instructor'}))
print('type - ', type(tmp_dict), tmp_dict)
```

    type -  <class 'dict'> {'city': 'kwangju', 'age': 30}
    key 이용 데이터 추출 -  None
    key 이용 데이터 추출 -  kwangju
    update() 요소 추가가능 -  None
    type -  <class 'dict'> {'city': 'kwangju', 'age': 30, 'job': 'instructor'}
    

#### zip *중요


```python
keys = ('user01', 'user02', 'user03', 'user04', 'user05')
data = ('임정섭', '섭섭해', '임섭순', '임재원', '임재원')

zip_dict = dict(zip(keys, data))
print('type - ', type(zip_dict), zip_dict)

```

    type -  <class 'dict'> {'user01': '임정섭', 'user02': '섭섭해', 'user03': '임섭순', 'user04': '임재원', 'user05': '임재원'}
    


```python
# .zip을 사용하지 않고 zip하기
zip_dict = {}

for idx in range(len(keys)) :
    zip_dict.update({keys[idx] : data[idx]})
    
print('type - ', type(zip_dict), zip_dict)
```

    type -  <class 'dict'> {'user01': '임정섭', 'user02': '섭섭해', 'user03': '임섭순', 'user04': '임재원', 'user05': '임재원'}
    


```python
# dict는 순서가 없어서 자체적으로 루프를 돌릴 수 없기 때문에 다른 방식으로
# keys(), values(), items()
for key in zip_dict.keys():
    print(key, end = '\t')
print()

for value in zip_dict.values() :
    print(value, end = '\t')
print()

for key, value in zip_dict.items() :
    print(key, value, end= '\t')
```

    user01	user02	user03	user04	user05	
    임정섭	섭섭해	임섭순	임재원	임재원	
    user01 임정섭	user02 섭섭해	user03 임섭순	user04 임재원	user05 임재원	


```python
# 없애기
zip_dict.clear()
print('type - ', type(zip_dict), zip_dict)
```

    type -  <class 'dict'> {}
    

#### set type
- 순서 X, 중복 X
- 선언: {}, set()
- 인덱싱, 슬라이싱 X


```python
tmp_set = {1}
print('type - ', type(tmp_set), tmp_set, bool(tmp_set))
```

    type -  <class 'set'> {1} True
    


```python
# 리스트 형식으로 데이터가 들어가야함
tmp_set = set([1,2,3])    
print('type - ', type(tmp_set), tmp_set, bool(tmp_set))
# print('indexing X - ', tmp_set[0])  --error
```

    type -  <class 'set'> {1, 2, 3} True
    


```python
# 교집합(intersection) == &, 합집합(union) == |, 차집합(difference) == -

tmp_set01 = set([1,2,3,4,5,6])
tmp_set02 = set([4,5,6,7,8,9])

print('교집합 - ', tmp_set01.intersection(tmp_set02), tmp_set01 & tmp_set02)
print('합집합 - ', tmp_set01.union(tmp_set02), tmp_set01 | tmp_set02)
print('차집합 - ', tmp_set01.difference(tmp_set02), tmp_set01 - tmp_set02)
```

    교집합 -  {4, 5, 6} {4, 5, 6}
    합집합 -  {1, 2, 3, 4, 5, 6, 7, 8, 9} {1, 2, 3, 4, 5, 6, 7, 8, 9}
    차집합 -  {1, 2, 3} {1, 2, 3}
    


```python
# 중복제거하고 출력 --
gender = ['남자', '여자', '여자', '남자', '남자', '남자', '여자', '여자', '남자', '남자']
gender_set = set(gender)
print(gender_set)
gender_list = list(gender_set)
print('type - ', type(gender_list), gender_list, bool(gender_list))
```

    {'남자', '여자'}
    type -  <class 'list'> ['남자', '여자'] True
    


```python
# dir(gender_set) _iter_ 함수가 있는 경우 반복문 사용 가능
# 출력 예시 {lobe : 1, jslim: 2, luckyL 4 ....}
print('단어 빈도 수를 구하고 싶다 - ')
word_list = ['love', 'jslim', 'dog', 'lucky', 'cat', 'cat', 'cat', 'jslim', 'lucky', 'lucky', 'lucky' ]
print('type - ', type(word_list), word_list, bool(word_list))


print()
print('case01  ')
print()
word_dict = {}
for value in word_list :
    #print(value)
    if value in word_dict :
        word_dict[value] = word_dict[value] + 1
        #print('true')
    else :
        word_dict[value] = 1
        #print('false')
print(word_dict)
print()
print()
print('case01-1  ')
word_dict = {}
for value in word_list :
    word_dict[value] = word_dict.get(value, 0) + 1
print(word_dict)
```

    단어 빈도 수를 구하고 싶다 - 
    type -  <class 'list'> ['love', 'jslim', 'dog', 'lucky', 'cat', 'cat', 'cat', 'jslim', 'lucky', 'lucky', 'lucky'] True
    
    case01  
    
    {'love': 1, 'jslim': 2, 'dog': 1, 'lucky': 4, 'cat': 3}
    
    
    case01-1  
    {'love': 1, 'jslim': 2, 'dog': 1, 'lucky': 4, 'cat': 3}
    


```python
print()
print('case02 - ')
print()
word_dict = {}
tmp_list = list(set(word_list))
for data in tmp_list : 
    # print(data)
    word_dict.update( {data : word_list.count(data)})
print(word_dict)

```

    
    case02 - 
    
    {'dog': 1, 'cat': 3, 'jslim': 2, 'lucky': 4, 'love': 1}
    


```python
print()
print('case03 - ')
print()
dict(zip(set(word_list) , [word_list.count(i) for i in set(word_list)] ))

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
