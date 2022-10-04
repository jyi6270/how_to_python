#### 파일 입출력
- 파이썬이 텍스트파일, JSON 형식 입출력(예외발생)
- 분석을 위한 데이터 타입이 필요(DataFrame - Pandas를 통한 파일 입출력(csv, xls))


```python
'''
open(filePath, mode = ' read | write | append | binary', encoding = '')


# close를 안 해도 되는 with open
with open() as file :
    pass
'''
```




    "\nopen(filePath, mode = ' read | write | append | binary', encoding = '')\n\n\n# close를 안 해도 되는 with open\nwith open() as file :\n    pass\n"




```python
def file_sample_function(fileName: str, mode: str) :
    print('file path - ', fileName)
    print('mode - ', mode)
    
    try:
        if mode == 'r' :
            file = open(fileName, mode = mode, encoding = 'UTF-8')
            print('type - ', type(file))
            print('read - ', file.read())
        
            file.close()
            
    except FileNotFoundError as f :
        print(str(f))

```


```python
file_sample_function('./data/greeting.txt', 'r')
```

    file path -  ./data/greeting.txt
    mode -  r
    type -  <class '_io.TextIOWrapper'>
    read -  오늘은 아침부터 어려운 내용을 공부했다
    하나도 모르겠다.
    ㅠ.ㅠ
    그래도 열심히 학습에 정진하도록 하겠다.
    
    


```python
# file.close()를 finally로 빼면 file이 정의된 if 구문을 벗어나기 때문에 외부에서 file = None을 정의해야 한다
def file_sample_function(fileName: str, mode: str) :
    print('file path - ', fileName)
    print('mode - ', mode)
    
    file = None
    
    try:
        if mode == 'r' :
            file = open(fileName, mode = mode, encoding = 'UTF-8')
            print('type - ', type(file))
            print('read - ', file.read())
            
        elif mode == 'w' :
            file = open(fileName, mode = mode, encoding = 'UTF-8')
            file.write('Hello ~ , Seop')
            
        elif mode == 'a' :
            file = open(fileName, mode = mode, encoding = 'UTF-8')
            file.write('\nSeop append')
            
    except FileNotFoundError as f :
        print(str(f))
    finally :
        file.close()
```


```python
print('읽기 모드 - ')
file_sample_function('./data/greeting.txt', 'r')

print('쓰기 모드 - ')
file_sample_function('./data/testing.txt', 'w')

print('추가쓰기 모드 - ')
file_sample_function('./data/testing.txt', 'a')
```

    읽기 모드 - 
    file path -  ./data/greeting.txt
    mode -  r
    type -  <class '_io.TextIOWrapper'>
    read -  오늘은 아침부터 어려운 내용을 공부했다
    하나도 모르겠다.
    ㅠ.ㅠ
    그래도 열심히 학습에 정진하도록 하겠다.
    
    쓰기 모드 - 
    file path -  ./data/testing.txt
    mode -  w
    추가쓰기 모드 - 
    file path -  ./data/testing.txt
    mode -  a
    


```python
def file_with_open_functon(fileName, mode, encoding):
    print('file - ', fileName)
    print('mdoe - ', mode)
    print('encoding - ', encoding)
    
    with open(fileName, mode, encoding = encoding) as file :
        print(file.read())
```


```python
file_with_open_function('./data/testing.txt', 'r', 'UTF-8')
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Input In [27], in <cell line: 1>()
    ----> 1 file_with_open_function('./data/testing.txt', 'r', 'UTF-8')
    

    NameError: name 'file_with_open_function' is not defined



```python
'''
with open 구문과 input 함수 그리고 루프구문을 이용하여
exit 문자가 들어오기 전까지 입력된 데이터를 파일(./data/multiline.txt)로 저장
'''
```


```python
def file_with_open_mission_functon(fileName, mode, encoding):
    print('file - ', fileName)
    print('mdoe - ', mode)
    print('encoding - ', encoding)
    
    flag = True
    
    with open(fileName, mode, encoding = encoding) as file:
        while flag:
            input_msg = input('데이터를 입력하세요: ')
            if input_msg == 'exit' :
                flag = False
                break
            else:
                print('msg - ', input_msg)
                file.write(input_msg+'\n')
```


```python
file_with_open_mission_functon('./data/multiline.txt', 'w', 'UTF-8')
```

    file -  ./data/multiline.txt
    mdoe -  w
    encoding -  UTF-8
    데이터를 입력하세요: 안녕
    msg -  안녕
    데이터를 입력하세요: 헬로우
    msg -  헬로우
    데이터를 입력하세요: 올라
    msg -  올라
    데이터를 입력하세요: exit
    


```python
'''
텍스트 데이터를 읽어들일 때 문자열 리턴이 아닌 리스트 형식으로 리턴이 가능하다.
readline()
'''
```


```python
with open('./data/multiline.txt', 'r', encoding = 'UTF-8') as file :
    line = None
    while line != '' :
        line = file.readline()
        print('type -', type(line))
        print(line)
        print(line.strip('\n'))
```

    type - <class 'str'>
    안녕
    
    안녕
    type - <class 'str'>
    헬로우
    
    헬로우
    type - <class 'str'>
    올라
    
    올라
    type - <class 'str'>
    
    
    


```python
'''
cnt_words.txt 줄 단위로 읽어서 단어의 길이가 10이하인 단어들만 카운팅 한다면?
'''

def cnt_function():
    cnt = 0
    with open('./data/cnt_words.txt', 'r', encoding = 'UTF-8') as file:
        for line in file :
            word = line.strip('\n')
            if (len(word) <= 10 ):
                cnt+=1
    print('10자 이하인 단어의 개수는: ', cnt)
```


```python
cnt_function()
```

    10자 이하인 단어의 개수는:  6
    


```python
# special_words.txt 파일로부터 문자 'c' 포함된 단어를 각 줄에 출력한다면?
# 단어를 출력할  때 등장한 순서대로 출력

def include_function() :
    with open('./data/txt/special_words.txt', 'r', encoding= 'UTF- 8') as file :
        words = file.readline().split()
        print(words)
        print('type - ', type(words))
        # (, .) 제거 해보자 - strip()
        words = [word.strip(',.') for word in words]
        print(words)
        print('정답 - ')
        for word in words :
            if 'c' in word :
                print(word)
    
```


```python
include_function()
```

    ['Fortunately,', 'however,', 'for', 'the', 'reputation', 'of', 'Asteroid', 'B-612,', 'a', 'Turkish', 'dictator', 'made', 'a', 'law', 'that', 'his', 'subjects,', 'under', 'pain', 'of', 'death,', 'should', 'change', 'to', 'European', 'costume.', 'So', 'in', '1920', 'the', 'astronomer', 'gave', 'his', 'demonstration', 'all', 'over', 'again,', 'dressed', 'with', 'impressive', 'style', 'and', 'elegance.', 'And', 'this', 'time', 'everybody', 'accepted', 'his', 'report.']
    type -  <class 'list'>
    ['Fortunately', 'however', 'for', 'the', 'reputation', 'of', 'Asteroid', 'B-612', 'a', 'Turkish', 'dictator', 'made', 'a', 'law', 'that', 'his', 'subjects', 'under', 'pain', 'of', 'death', 'should', 'change', 'to', 'European', 'costume', 'So', 'in', '1920', 'the', 'astronomer', 'gave', 'his', 'demonstration', 'all', 'over', 'again', 'dressed', 'with', 'impressive', 'style', 'and', 'elegance', 'And', 'this', 'time', 'everybody', 'accepted', 'his', 'report']
    정답 - 
    dictator
    subjects
    change
    costume
    elegance
    accepted
    


```python
'''
회문(palindrome)
madam, nurses run, sos, rotator, level ...
만약 단어가 회문인지를 검사하는 함수 만든다면?
'''
str = 'jslim9413'
if str == str[::-1] :
    print('true')
else:
    print('false')
```

    false
    


```python
str[::-1]
```




    '3149milsj'




```python
list(reversed(str))
```




    ['3', '1', '4', '9', 'm', 'i', 'l', 's', 'j']




```python
list(str) == list(reversed(str))
```




    False




```python
0  1  2  3  4  5  6  7  8  9  10
m  u  l  t  i  c  a  m  p  u  s
11 10 9  8  7  6  5  4  3  2  1 (-)
```


```python
def isPalindrome():
    word = input('회문 검사를 위한 단어 입력: ')
    middle_idx = len(word) // 2
    print('idx - ', middle_idx)
    
    isFlag = True
    for idx in range(middle_idx) :
        if word[idx] != word[-1-idx] :
            isFlag = False
            break
            
    return isFlag
```


```python
result = isPalindrome()
if result:
    print('회문이네요')
else:
    print('회문이 아니네요')
```

    회문 검사를 위한 단어 입력: result
    idx -  3
    회문이 아니네요
    


```python
'''
제공되어지는 txt파일에서 회문인 단어만 출력하고 단어의 개수를 카운트 한다면?
주의) 단어사이의 줄 바꿈이 두 번 일어나서는 안 됨!
palindrome_words.txt
'''
def palindrome_function() :
    
```


```python
def palindrome_function() :
    with open('./data/txt/palindrome_words.txt', 'r', encoding= 'UTF- 8') as file :
        cnt = 0
        for word in file :
            word = word.strip('\n')
            if word == word[::-1] :
                print(word)
                cnt += 1
                
    print('회문인 단어의 개수는 : ', cnt)
```


```python
palindrome_function()
```

    did
    noon
    refer
    madam
    level
    nursesrun
    회문인 단어의 개수는 :  6
    


```python
'''
네트워크상에서 표준으로 사용되는 파일 형식 - JSON
{key : value, key : value}
encoding : python(dict) -> json : dumps()
decoding : json         -> python(dict, list) : loads()
'''

import json as j

tmp_dict = {'id' : 'jslim', 'pwd': 'jslim'}
print('type - ', type(tmp_dict))

str_dict = j.dumps(tmp_dict)
print('dict -> json', str_dict)
print('dict -> json', type(str_dict))

py_dict = j.loads(str_dict)
print('json -> dict ', py_dict)
print('json -> dict ', type(py_dict), py_dict['id'])
```

    type -  <class 'dict'>
    dict -> json {"id": "jslim", "pwd": "jslim"}
    dict -> json <class 'str'>
    json -> dict  {'id': 'jslim', 'pwd': 'jslim'}
    json -> dict  <class 'dict'> jslim
    


```python
def json_function():
    with open('./data/txt/usagov_bitly.txt','r', encoding = 'UTF-8') as file :
        for line in file :
            lines = file.readlines() # readline : 한줄, readlines : 전체를 리스트로 담아서 가져옴
            # print(lines)
            print()
            lines = [ j.loads(line) for line in lines]
            # print(lines)
            print('type - ', type(lines))
            print('url  - ', lines[0]['r'])
```


```python
json_function()
```

#### 수행평가
- zipcode.txt 이용
- input() 동 이름 입력받기 예)개포
- 해당하는 동의 주소를 출력하는 함수(search_address())를 정의
- 해당동이 존재하지 않을 수 있다.(예외처리)


```python
def search_address():
    with open('./data/txt/zipcode.txt', 'r', encoding = 'UTF-8') as file:
        area = input('동 이름을 입력하세요: ')
        for line in file:
            try:
                address = [line.strip('\n')]
                address01 = [address[0].split('\t')[3]]
                address02 = address01[0].split('동')[0]
                if area == address02:
                    print(line)
            except Exception as e :
                print('없는 동입니다.')
```


```python
search_address()
```

    동 이름을 입력하세요: 미미
    


```python

```
