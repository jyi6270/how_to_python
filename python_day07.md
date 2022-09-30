#### oop2


```python
class person_vo(object) :
    def __init__(self, name, age, address) : 
        self.__name    = name 
        self.__age     = age 
        self.__address = address 
    
    def setName(self, name) : 
        self.__name = name 
    def getName(self) : 
        return self.__name 
    
    def setAge(self, age) : 
        self.age = age 
    def getAge(self) : 
        return self.age 
    
    def setAddress(self, address) : 
        self.__address = address 
    def getAddress(self) : 
        return self.__address
    
    def person_info(self) :
        return self.__name +'\t'+ str(self.__age) +'\t'+ self.__address

```


```python
class student_vo(person_vo):
    def __init__(self, name, age, address, ssn) :
        super().__init__(name, age, address)
        self.ssn = ssn
        
    def student_info(self):
        return super().person_info() + '\t' + self.ssn
    
    # overriding
    def person_info(self) :
        return super().person_info() + '\t' + self.ssn
```


```python
class teacher_vo(person_vo) :
    def __init__(self, name, age, address, subject) :
        super().__init__(name, age, address)
        self.subject = subject
        
    def teacher_info(self):
        return super().person_info() + '\t' + self.subject
    
     # overriding
    def person_info(self):
        return super().person_info() + '\t' + self.subject
```


```python
print('person_vo Instance create - ')
perObj = person_vo('섭섭해', 24, '광주')
# print(perObj.name) -- 멤버변수의 은닉화로 직접 접근 불가
print(perObj.person_info())
```

    person_vo Instance create - 
    섭섭해	24	광주
    

- 다형성(overriding)
- 상속관계에서 부모에 정의된 함수를 자식에서 재정의하는 것으로 구현부가 달라야 한다.
- 부모에 정의된 함수의 인자의 수와 재정의된 함수의 인자의 수는 같아야 한다.


```python
person_list = []
person_list.append(student_vo('김기쁨', 26, '부천', '1992'))
person_list.append(teacher_vo('임정섭', 24, '서울', 'python'))
person_list.append(student_vo('김가영', 23, '천안', '1993'))

print('데이터 출력 - ')
for idx, entity in enumerate(person_list) :
    # print('idx - ', idx)
    # print('entity - ', type(entity.__class__.__name__))
    if entity.__class__.__name__ == 'student_vo' :
        print(entity.student_info())
    else:
        print(entity.teacher_info())
        
        
print('overriding - ')
print('데이터 출력 - ')
for idx, entity in enumerate(person_list):
    print(entity.person_info())
```

    데이터 출력 - 
    김기쁨	26	부천	1992
    임정섭	24	서울	python
    김가영	23	천안	1993
    overriding - 
    데이터 출력 - 
    김기쁨	26	부천	1992
    임정섭	24	서울	python
    김가영	23	천안	1993
    

- 추상화(추상클래스, 추상함수)
- 클래스를 만드는 이유: 인스턴스를 생성하기 위해서
- but 추상클래스 -> 인스턴스 생성이 불가


```python
from abc import *

class animal(object, metaclass = ABCMeta) :
    
    @abstractmethod
    def fly(self) :
        pass
    
    @abstractmethod
    def take_off(self) :
        pass
    
    @abstractmethod
    def landing(self) :
        pass
    
    def non_abstract_function(self):              #-- 일반함수를 사용할 순 있지만 객체생성은 불가능
        print('추상클래스에 정의된 일반함수')
```


```python
# 추상클래스는 객체 생성이 불가
obj = animal()
obj.fly()
```


```python
class super_man(animal) :
    def fly(self):
        print('super_man 이 망토를 휘날리며 날아갑니다.')
    
    def take_off(self):
        print('super_man 이 이륙한다.')
    
    def landing(self):
        print('super_man 이 착륙한다.')
```


```python
man = super_man()
man.fly()
man.take_off()
man.landing()
```

    super_man 이 망토를 휘날리며 날아갑니다.
    super_man 이 이륙한다.
    super_man 이 착륙한다.
    


```python
class bird(animal) :
    def fly(self):
        print('bird 이 망토를 휘날리며 날아갑니다.')
    
    def take_off(self):
        print('bird 이 이륙한다.')
    
    def landing(self):
        print('bird 이 착륙한다.')
```


```python
bird = bird()
bird.fly()
bird.take_off()
bird.landing()
```

    bird 이 망토를 휘날리며 날아갑니다.
    bird 이 이륙한다.
    bird 이 착륙한다.
    


```python
animals = []
animals.append(man)
animals.append(bird)
for entity in animals:
    entity.fly()
```

    super_man 이 망토를 휘날리며 날아갑니다.
    bird 이 망토를 휘날리며 날아갑니다.
    

- 예외처리(Exception)
- XXXXError
- 발생되는 에러 중 사소한 에러라면 실행을 종료하지 말고 예외처리를 통해서 실행을 계속 이어나가는 방법


```python
'''
Exception(상위)  -- 다중 에러를 하나로 포함
- AException
- BException
- ...

try: 예외발생 코드를 정의

except: 발생된 예외를 처리하는 곳으로 예외 발생시에만 실행되는 블럭

else: 예외가 발생하지 않았을 때 실행되는 블럭

finally: 예외발생 여부와 상관없이 실행되는 블럭

'''
def user_input():
    try:
        age = int(input('나이를 숫자로 입력하세요: '))
    except Exception as e :
        print(str(e))
        print('악의적으로 문자를 넣지 말고 숫자를 넣어주세요')
        user_input()
    else :
        print('your age is ', age, 'years old')
    finally:
        print('예외발생여부와 상관없이 수행하는 블럭입니다.')
    
```


```python
user_input()
```

    나이를 숫자로 입력하세요: yongil
    invalid literal for int() with base 10: 'yongil'
    악의적으로 문자를 넣지 말고 숫자를 넣어주세요
    나이를 숫자로 입력하세요: 27
    your age is  27 years old
    예외발생여부와 상관없이 수행하는 블럭입니다.
    예외발생여부와 상관없이 수행하는 블럭입니다.
    


```python
'''
매개변수로 넘겨 받은 각 첨자번지의 값에 제곱한 결과를 출력한다.
예외처리를 통한 마지막 print() 함수를 수행하게 하고 싶다면?
'''
def list_print(lst) :
    for element in lst :
        print('raw - ', element)
        try:
            print('squared - ', element ** 2)
        except Exception as e :
            print('제공할 수 있는 데이터가 아닙니다.')
        
    print('***function end***')
    

```


```python
tmp_list = [10, 20, 35, 'jslim', 40, 50]
list_print(tmp_list)
```

    raw -  10
    squared -  100
    raw -  20
    squared -  400
    raw -  35
    squared -  1225
    raw -  jslim
    제공할 수 있는 데이터가 아닙니다.
    raw -  40
    squared -  1600
    raw -  50
    squared -  2500
    ***function end***
    


```python
# for loop 전체를 try 하면 예외 발생시 루프 중단
def list_print(lst) :
    try:
        for element in lst :
            print('raw - ', element)
            print('squared - ', element ** 2)
    except Exception as e :
            print('제공할 수 있는 데이터가 아닙니다.')
        
    print('***function end***')
```


```python
tmp_list = [10, 20, 35, 'jslim', 40, 50]
list_print(tmp_list)
```

    raw -  10
    squared -  100
    raw -  20
    squared -  400
    raw -  35
    squared -  1225
    raw -  jslim
    제공할 수 있는 데이터가 아닙니다.
    ***function end***
    

- 사용자정의 예외 클래스 만들기


```python
print('사용자 정의 예외클래스는 Exception 상속으로 만들 수 있다 - ')
class userNegativeDivisionError(Exception):
    def __init__(self, msg) :
        self.msg = msg
```

    사용자 정의 예외클래스는 Exception 상속으로 만들 수 있다 - 
    


```python
def positiveDivide(x,y) :
    if(y < 0) :
        raise userNegativeDivisionError('값을 음수로 나눌 수 없음')
        
    return x/y
```


```python
try :
    result = positiveDivide(10, 0)
    print('result - ', result)
except Exception as e :
    print(str(e))
#except zeroDivisionError as z :
#    print(z.args[0])
#except userNegativeDivisionError as u :
#    print(u.msg)

```

    division by zero
    


```python
try :
    result = positiveDivide(10, 0)
    
except Exception as e :
    result = 0
    print('예외발생으로 result 값을 초기값으로 세팅!', result)
else:
    print('result - ', result)
```

    예외발생으로 result 값을 초기값으로 세팅! 0
    


```python

```


```python

```


```python

```
