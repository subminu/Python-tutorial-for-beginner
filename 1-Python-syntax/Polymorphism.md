# Polymorphism

이번 문서에서는 polymorphism이란 어떤 개념이고 python에서는 어떻게 구현하는지 알아보도록 합시다.

## What is Polymorphism

다형성(polymorphism)은 하나의 function(method)가 여러 data type을 지원하는 특성이라고 볼 수 있습니다. 예를 들어 봅시다. 자릿수를 계산하는 함수를 만든다고 했을때, polymorphism의 개념을 적용하지 않는다면 다음과 같이 서로다른 data type에 대해 각각 하나씩 만들어야합니다.

```python
def len_str(arg):
    pass

def len_dict(arg):
    pass

def len_list(arg):
    pass

...
```

위와 같이 구현은 가능하지만 호출할 때, 결과적으로는 자릿수를 세는 동일한 역할을 함수인데 불리는 함수명이 달라 사용자 입장에선 불편합니다. 

### User defined polymorphic function

만약 스스로 polymorphic function을 구현하고자 할때는 다음과 같이 할 수 있을 것입니다.

```python
def get_length(arg):
    if isinstance(arg, str):
        pass
    
    else if isinstance(arg, dict):
        pass
    
    else if isinstance(arg, list):
        pass
    
    ...
```

`isinstace(A,B)`는 A가 B의 instance인지 확인할 수 있는 함수입니다.  꼭 이런 식으로 코딩을 해야하는 것은 아니며, 구현할 수 있는 방식들 중 하나를 표현해낸 것입니다.

> Tip👀
>
> Polymorphism이라는 특성은 사용자의 입장에서 하나의 function(method)로 다양한 data type에서도 동일한 작업을 하는 것처럼 구현할 수 있으면 됩니다. 

### Built-in polymorphic function

Python에서는 이미 polymorphism이 적용된 `len()`함수를 제공하고 있습니다.

```python
print(len("hello"))
print(len({'a':1, 'b':2, 'c':3}))
print(len(["hello", "world"]))
```

```python
# 출력 결과
5
3
2
```

`len()`이란 함수 하나로 서로 다른 type을 동일하게 처리하는 것처럼 구현하였습니다. 실제로 길이를 구하는 방식은 각각 다를지 몰라도, 사용자 입장에선 함수 하나로 처리할 수 있으니 추상적이고 간결해집니다.

### User defined polymorphic method

Class의 method의 경우에는 namespace끼리 서로 영향을 끼치지 않는 점을 이용하여 polymorphism을 구현합니다.

```python
class Cat:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def make_sound(self):
        print("meow")
        
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def make_sound(self):
        print("woof")
        
Max = Cat("Max",1)        
Sandy = Dog("Sandy",2)

Max.make_sound()
Sandy.make_sound()
```

```python
# 출력 결과
meow
woof
```

사용자 입장에선 똑같은 `make_sound()`를 이용하여 울음소리를 출력하는 것처럼 보입니다.

### Method Overriding

상속(inheritance)에서 polymorphism을 지원한다고 생각해봅시다.

```python
class Human:
    def __init__(self):
        pass
    
    def do_something(self):
        print("talking")
        
class Student(Human):
    def __init__(self):
        pass
    
    def do_somthing(self):
        print("studying")
        
a = Student()
a.do_something()
```

```python
# 출력 결과
studying
```

다음과 같이 Human에서 이미 정의한 method, `do_something()`을 Student class에선 다르게 구현하고 싶을때 base(parent) class에서 정의한 method의 이름과 똑같이 적고 마치 정의를 덮어 쓰는 것 마냥 정의하는 것을 method overriding이라고 합니다.

### Special method Overriding

Special method란 `__(something)__`에서 underscore 두개로 둘러싸인 예약된 method들을 뜻합니다. 익숙한 예시들을 보도록 합시다.

```python
a = 1 + 3
b = (1).__add__(3)

print(a)
print(b)
```

```python
# 출력 결과
4
4
```

위의 예시에서 a와 b가 동일하게 4가 출력되는 것을 확인할 수 있습니다. 이처럼 연산자들도 사실 python의 special method를 호출하여 결과적으로 값을 계산하게 되는 것을 알 수 있습니다.

> Tip👀
>
> 연산자들 뿐만 아니라 다양한 method들이 존재 합니다. 해당 method들을 전부 살펴보는 것 보단 필요할때 찾아서 학습하는 편이 좋습니다. 해당 method들에 대한 설명은 공식문서에서 한국어를 지원하고 있으니 참고하시면 되겠습니다.
>
> * [Special method - eng](https://docs.python.org/3/reference/datamodel.html#special-method-names)
> * [Special method - kor](https://docs.python.org/ko/3/reference/datamodel.html#special-method-names)

special method를 활용하면 다음과 같이 `+`의 기능을 마음대로 customizing이 가능합니다.

```python
class Vector:
    def __init__(self, *arg):
        self.data = [i for i in arg]
        
    def __add__(self, vec):
        return Vector(*[q + p for q,p in zip(self.data, vec.data)])
  
    def __repr__(self): 
        """해당 객체에서 print를 했을 시에 보여줄 내용을 정의하는 special method"""
        return str(self.data)
```

위와 같이 Vector의 일부분을 구현하였다고 합시다. Vector 끼리의 합은 각 원소들끼리의 합으로 계산하여야 합니다. 물론 그냥 `add(a,b)`를 따로 만들어서 구현을 할 수는 있습니다. 그러나 special method를 활용하게되면 다음과 같은 계산을 `+`을 통해서도 할 수 있게 됩니다.

```python
a = Vector(1,2)
b = Vector(4,6)
print(a+b)
```

```python
# 출력 결과
[5, 8]
```

---

[Back - OOP](./Object-Oriented-Programming.md)