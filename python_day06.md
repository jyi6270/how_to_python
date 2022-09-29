#### class (Object Oriented Programming)
- 은닉화
- 상속
- 다형성
- 추상화


```python
'''
함수 < 클래스(변수, 함수) < 모듈(xxxxx.py) < package

클래스란?
- 함수의 모음
- 여러개의 함수와 공유 데이터(변수)를 묶어서 관리하는 템플릿
- 구성: 함수 + 속성 + 초기화함수(생성자)

class vs instance

변수 = xxxx() # 인스턴스 생성
변수.함수() # call
변수.속성 # call

결론: 파이썬의 모든 함수는 객체로 취급된다. 객체로 취급된다는 것은 클래스라는 의미.

'''
```

- 사용자 정의 클래스 작성


```python
class person :
    
    cls_var = '클래스 소유의 변수'
    
    # initializer
    # __xxxx__ (magic function)
    # 인스턴스 소유의 변수란 초기화 함수내에 선언한 변수를 의미하고
    # 변수의 scope 은 클래스 전역에서 사용이 가능하다
    
    def __init__(self, name, age, gender) :
        print('초기화 함수로 instance 생성시 호출 되는 함수입니다.')
        self.name = name
        self.age = age
        self.gender = gender
        
        
    def doing(self):
        print('인스턴스 소유의 함수')
        self.something('함수내에서 함수호출 - ')
        
    def something(self, str) :
        print('인스턴스 소유의 함수 - something')
        print(str)

    def personinfo(self) :
        return self.name+'\t'+str(self.age)+'\t'+self.gender
        
    @classmethod
    def classFunc(cls) :
        print('해당 함수는 인스턴스 소유가 아닌 클래스 소유 - 인스턴스 소유의 함수, 변수 사용 불가')
        
obj = person('jslim', 24, 'm')
print('type - ', type(obj))
print()

print('caller - function')
obj.doing()

print('caller - variable')
print(obj.name, obj.age, obj.gender)
print()

print(obj.personinfo())
```

    초기화 함수로 instance 생성시 호출 되는 함수입니다.
    type -  <class '__main__.person'>
    
    caller - function
    인스턴스 소유의 함수
    인스턴스 소유의 함수 - something
    함수내에서 함수호출 - 
    caller - variable
    jslim 24 m
    
    jslim	24	m
    


```python
print('클래스 탬플릿으로부터 여러개의 인스턴스 생성이 가능하다 - ')
stu01 = person('김끼쁨', 26, 'm')
stu02 = person('정쌍환', 26, 'f')
stu03 = person('최찐형', 27, 'm')

person_list = []
person_list.append(stu01)
person_list.append(stu02)
person_list.append(stu03)

print('인스턴스 정보를 출력 - ')
for instance in person_list:
    print(instance.personinfo())
```

    클래스 탬플릿으로부터 여러개의 인스턴스 생성이 가능하다 - 
    초기화 함수로 instance 생성시 호출 되는 함수입니다.
    초기화 함수로 instance 생성시 호출 되는 함수입니다.
    초기화 함수로 instance 생성시 호출 되는 함수입니다.
    인스턴스 정보를 출력 - 
    김끼쁨	26	m
    정쌍환	26	f
    최찐형	27	m
    


```python
print('클래스 소유 변수는 인스턴스 생성없이 클래스 이름으로 접근 가능하다 - ')
print('cls 변수 출력 - ', person.cls_var)
person.cls_var = '값을 변경합니다.'
print(person.cls_var)

print(stu01.cls_var)
print(stu02.cls_var)

print('클래스 소유 함수 호출 - ')
person.classFunc()


stu01.doing()
```

    클래스 소유 변수는 인스턴스 생성없이 클래스 이름으로 접근 가능하다 - 
    cls 변수 출력 -  클래스 소유의 변수
    값을 변경합니다.
    값을 변경합니다.
    값을 변경합니다.
    클래스 소유 함수 호출 - 
    해당 함수는 인스턴스 소유가 아닌 클래스 소유 - 인스턴스 소유의 함수, 변수 사용 불가
    인스턴스 소유의 함수
    인스턴스 소유의 함수 - something
    함수내에서 함수호출 - 
    


```python
'''
인스턴스 변수 - account_number, balance, InterestRate
accountInfo() - 계좌정보를 출력
withDraw() - 매개변수로 들어온 금액만큼 출금하여 잔액을 변경한다.(잔액이 부족하면 출금불가)
deposit() - 잔액에 누적한다.
print InterestRate() - 현재 잔액에 이자율을 계산하여 소수점 2자리까지 금액을 출력
'''

class account:
    def __init__(self, account_number, balance, interestRate):
        self.account_number = account_number
        self.balance = balance
        self.interestRate = interestRate
    def accountInfo(self):
        print('계좌번호: {}이며 현재 잔액은 :{}이고 이자율은 {}%입니다.'.format(self.account_number,
                                                           self.balance,
                                                           self.interestRate))
    def withDraw(self, amount):
        if self.balance > amount:
            self.balance -= amount
        else:
            print('잔액이 부족합니다.')
            
    def deposit(self, amount: int):
        self.balance += amount
        print(self.balance)
        
    def printinterestRate(self):
        print(self.balance + (self.balance * self.interestRate))

```


```python
print('caller - ')
acc = account('123-1234-123456789', 500000, 0.02)
acc.accountInfo()
acc.withDraw(600000)
acc.deposit(200000)
acc.accountInfo()
acc.withDraw(600000)
acc.accountInfo()
print()
print('현재 잔액의 이자를 포함한 금액 확인 - ')
acc.printinterestRate()
```

    caller - 
    계좌번호: 123-1234-123456789이며 현재 잔액은 :500000이고 이자율은 0.02%입니다.
    잔액이 부족합니다.
    700000
    계좌번호: 123-1234-123456789이며 현재 잔액은 :700000이고 이자율은 0.02%입니다.
    계좌번호: 123-1234-123456789이며 현재 잔액은 :100000이고 이자율은 0.02%입니다.
    
    현재 잔액의 이자를 포함한 금액 확인 - 
    102000.0
    

- 은닉화(encapsulation)
- information hiding(정보 은닉)


```python
class userDate(object) :
    def setYear(self, year) :
        if year < 0:
            self.__year = 2022      #-- 언더바가 함수를 은닉화해서 private의 의미
        else:
            self.__year = year
            
    def getYear(self) :
        return self.__year
```


```python
print('instance create - ')

obj = userDate()
#obj.year = -2022  -- error
obj.setYear(2050)
print('year - ', obj.getYear())
```

    instance create - 
    year -  2050
    

- 상속(inheritance)
- is a ~
- 부모는 추상적으로 범위가 넓어져야한다.
- 자식은 구체적으로 범위가 좁혀져야한다.


```python
# object - user_super - user_sub
class user_super(object) :
    def super_sayEcho(self, name):
        print('>>> super', name+'님 안녕하세요~~')

class user_sub(user_super) :
    def sub_sayEcho(self, name):
        print('>>> sub', name+'님 안녕하세요~~')
```


```python
obj = user_sub()
obj.super_sayEcho('jslim')
obj.sub_sayEcho('jslim')
```

    >>> super jslim님 안녕하세요~~
    >>> sub jslim님 안녕하세요~~
    


```python
obj = user_super()
obj.super_sayEcho('jslim')
#obj.sub_sayEcho('jslim')     #-- error 부모는 자식의 구성요소에 접근 X
```

    >>> super jslim님 안녕하세요~~
    


```python
class person_vo(object):
    def __init__(self, name, age, address):
        self.name = name
        self.age = age
        self.address = address
        
    def person_info(self):
        return self.name + '\t' + str(self.age) + '\t' + self.address

class student_vo(person_vo):
    def __init__(self, name, age, address, ssn) :
        super().__init__(name, age, address)
        self.ssn = ssn
        
    def student_info(self):
        return super().person_info() + '\t' + self.ssn

class teacher_vo(person_vo) :
    def __init__(self, name, age, address, subject) :
        super().__init__(name, age, address)
        self.subject = subject
        
    def teacher_info(self):
        return super().person_info() + '\t' + self.subject
```


```python
stu01 = student_vo('임정섭', 24, '광주', '1992')
print('stu info - ', stu01.student_info())

tea01 = teacher_vo('임정섭', 24, '광주', 'PythonScripts')
print('tea info - ', tea01.teacher_info())

```

    stu info -  임정섭	24	광주	1992
    tea info -  임정섭	24	광주	PythonScripts
    


```python

```
