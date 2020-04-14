# Object Oriented Programming

해당 내용은 Python에 국한되는 내용이 아니지만 앞으로 Class와 Object를 배움에 있어 기본적으로 알고 있으면 좋은 개념들입니다.

프로그래밍을 하는 이유는 "문제를 풀기 위함"인 것은 누구나 알고 있습니다. 수학 문제를 풀 때도 여러가지 접근 방식이 있듯이 프로그래밍 문제를 해결하는데도 여러가지 접근 방법이 있습니다. 그 중 `Object Oriented Programming`(이하 `OOP`)은 객체를 만들어 문제를 해결하는 방법입니다.

> Tip👀
>
> 문제를 해결하는데 있어서 다양한 접근법이 존재합니다.
>
> | Programming paradigm        | ex*             |
> | --------------------------- | --------------- |
> | Procedual Programming       | C               |
> | Object Oriented Programming | Python, C++     |
> | Functional Programming      | Haskell, Scheme |
>
> 여기 예시들에 있는 언어를 사용하면 무조건 해당 접근법으로 문제를 풀어야하는게 아닙니다. 예시로 나온 언어들이 해당 paradigm을 지원하는 언어로 자주 쓰인다는 의미로 받아드리면 될 것 같습니다.
>
> Python 같은 경우,  multi-paradigm programming language라고 합니다. 즉 여러 paradigm으로 문제를 해결 할 수 있습니다.

그렇다면 객체를 통해 문제를 해결한다는 말에서 객체는 무엇일까요? 객체라고 하는 것은 본연의 특성과 행동을 지니고 있는 대상이라고 보시면 될 것 같습니다. 디냥이🐈라는 객체를 예를 들어 봅시다.

🐈는 

이처럼 이름, 나이, 성별은 디냥이라는 객체의 특성이라고 할 수 있겠죠. 또한 디냥이는 잠자기, 밥먹기등 여러 가지 행동들을 할 수 있습니다. 이러한 행동과 특성에 대한 집합체를 프로그래밍에서는 객체(`Object`)라고 합니다.

만약 Python으로 디냥이라는 객체(`Object`)를 만든다고 하면 위와 같은 특성과 행동을 각각 변수와 함수로 구현할 수 있겠죠?

이처럼 `OOP`는 어떠한 객체를 구상할 때,  **추상적으로** 구현하는 것을 전제로 만들게 됩니다. 이와 같은 특성을 추상화(**`abstraction`**)이라고 합니다. 

추상화(**`abstraction`**)을 포함하여 `OOP`에서는 중요한 개념 4가지가 있습니다.

- [`Abstraction`](./Abstraction.md)
- [`Encapsulation`](./Encapsulation.md)
- [`Inheritance`](./Inheritance.md)
- [`Polymorphism`](./Polymorphism.md)

해당 개념을 전부 숙지하신 뒤에 다음의 글을 읽으시면 좋습니다.

## Everything is an Object in Python

Python의 모든 것들은 `Object`로 구성되어 있습니다. [Type conversion(Typecasting) - type() function](./Type-conversion(Typecasting).md#type-function)의 예시에서 이미 한 번 경험하셨을 것입니다. 해당 예시를 재활용 하자면 다음과 같습니다.

```python
print(type(10))
print(type(1.2))
print(type(1+2j))
print(type("hello"))
```

```python
# 출력 결과
<class 'int'>
<class 'float'>
<class 'complex'>
<class 'str'>
```

당시에는 언급하지 않았지만 `type()`이라는 함수는 `type()`의 argument를 받으면 해당 parameter가 어떤 class로 만들어진 object인지 알려주는 함수입니다. 이러한 함수가 동작할 수 있는 이유는 모든 data들이 class를 통해 만들어진 `Object`이기 때문에 가능합니다.

물론 Python에서 제공하는 Built-in data sturcture들도 Object입니다.

```python
print(type([]))
print(type(()))
print(type({}))
print(type(set()))
```

```python
# 출력 결과
<class 'list'>
<class 'tuple'>
<class 'dict'>
<class 'set'>
```

여기서 그치지 않고 `function`또한 `Object`임을 `type()`을 통해 알 수 있습니다.

```python
def func():
    """this is a fucntion"""
    pass

print(type(func))
```

```python
# 출력 결과
<class 'function'>
```

당연히 여러분들이 만든 `User-defined Class`으로 만들어낸 객체 또한 `Object`입니다.

혼란스러울 수도 있습니다만 그럴 수록 정의에 입각한 사고로 바라보시면 됩니다. 앞서 말씀드렸다 시피 `Object`는 **`attribute`와 `behavior`들의 집합체**라고 하였습니다.

정의에 따라 모든것이 `Object`인지를 확인해 보도록 합시다. 

### Litaral values

`int`, `float`, `complex`, `str`의 경우 이미 어떠한 method들이 있는지 알고 있습니다. 당장에 [Operators](./Operators.md)만 하더라도 다양한 method들이 있음을 확인 할 수 있습니다. [Polymorphism - Special method overriding](./Polymorphism.md#Special-method-overriding)에서 다뤘다시피 operators도 special method를 호출하여 계산되어 집니다.

### Built-in Data structure

`list`, `tuple`, `set`, `dict` 또한 각각의 문서에서 어떠한 method들이 있는지 [Built-in Data structure](./Built-in-Data-structure.md)를 통하여 잠시 언급하였습니다. 

### Function

[Functions - docstring](./Functions.md#docstring)에서 깊게 설명하지 않은 부분이 바로 docstring 부분이었는데요. 이부분에 대해 다시 한 번 보자면 다음과 같습니다.

```python
def func():
    """this is a function"""
    pass
print(func.__doc__)
```

```python
# 출력 결과
this is a function
```

위와 같이 `""" """`로 적은 함수의 설명이 `__doc__`라는 `instance variable`에 저장되어 있는 것을 확인 할 수 있습니다.

> Tip👀
>
> 사실 위와 같이 확인할 필요 없이 다음의 명령어를 치면 어떻게 `Object`가 어떻게 구현되어 있는지 자세하게 확인할 수 있습니다.
>
> ```python
> help(Object)
> ```
>

드디어 python의 끝이 보이기 시작하는 것 같습니다. 다음 문서에서는 여태 나왔었던 error들이 어떻게 출력되는지, error에는 어떠한 종류가 있는지, 사용자 정의 error를 만드는 방법에 대해 소개해 드리도록 하겠습니다.

---

[Go - Errors & Exceptions](./Errors-&-Exceptions.md)