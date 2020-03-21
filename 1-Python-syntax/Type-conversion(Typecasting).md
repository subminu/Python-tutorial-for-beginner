# Type conversion(Typecasting)

이번에는 형변환에 대해 알아볼 것입니다. 형변환이라 함은 [Data types](./Data-types.md)을 변환하는 것인데요. 저번 문서에서 언급 했듯, 형변환에는 두 종류의 형변환이 존재합니다.

- [`Explicit conversion`](./Type-conversion(Typecasting).md#explicit-conversion)

- [`Implicit conversion`](./Type-conversion(Typecasting).md#implicit-conversion)

저번 문서에서 언급한 `Explicit conversion`부터 보도록 하죠.

## Explicit conversion

명시적 형변환은 필요에 따라 특정 data의 type을 강제적으로 바꾸는 것을 말합니다. 형변환이라고 했으니, 각자의 data type에는 자신만의 Explicit conversion syntax가 따로 있겠죠?

| Type     | Statement                          | Syntax                                   |
| -------- | ---------------------------------- | ---------------------------------------- |
| Text     | `str`                              | `str()`                                  |
| Numeric  | `int`, `float`, `complex`          | `int()`, `float()`, `complex()`          |
| Boolean  | `bool`                             | `bool()`                                 |
| Sequence | `list`, `tuple`, `range`           | `list()`, `tuple()`, `range()`           |
| Mapping  | `dict`                             | `dict()`                                 |
| Set      | `set`, `frozenset`                 | `set()`, `frozenset()`                   |
| Binary   | `bytes`, `bytearray`, `memoryview` | `bytes()`, `bytearray()`, `memoryview()` |

엄청나게 많은 자료형이 있지만 형변환 하는 방법은 간단합니다. type이 `int`인 `x`를 type이 `str`인 데이터로 바꾸고 싶을때, 다음과 같은 명령어로 바꿀 수 있습니다.

```python
integer = 10
string = str(integer)
print(string)
```

```python
# 출력 결과
10
```

흠 출력은 했는데 이게 타입이 바뀐건지 안 바뀐건지 알 수가 없습니다. 제대로 확인하고 싶은데 확인할 방법은 없을까요? 

### `type()` function 

Python에는 해당 변수가 어떤 type인지 알 수 있도록 하는  `function`이 있습니다. 아직 `function`이 정확히 뭔지 모르겠지만 사용방법을 보면서 대충 어떤 기능이 있는지 알아보도록 합시다.

```python
integer = 10
print(type(integer))
string = str(integer)
print(type(string))
```

```python
# 출력 결과
<class 'int'>
<class 'str'>
```

출력 결과에서 아는 단어만 봅시다. 첫 번째 출력 결과에 `int`라는 글자를 확인하였고 `str()`명령어 이후 `str`이라는 글자를 확인 할 수 있었습니다. 흠..`type()`는 무엇인지는 잘 모르겠지만 저런식의 출력 결과로 Data type을 말해주는 구나 정도로 이해하면 되겠습니다.

```python
string = "blackwind"
print(int(string))
```

그렇다면 위의 예시는 어떨까요? "blackwind"를 `int`로 바꾸면 어떤 정수가 나올까요?

```python
# 출력 결과
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-1-89092f9f127f> in <module>()
      1 string = "blackwind"
----> 2 print(int(string))

ValueError: invalid literal for int() with base 10: 'blackwind'
```

결과는 보이는 것과 같이 에러가 뜹니다. 문자열에 순수 숫자 이외에 다른 문자가 하나라도 들어가 있으면 이렇게 10진수의 숫자로 바꿀 수 없다고 말합니다.

에러를 자세히 보니 `int()`는 기본적으로 정수를 10진법으로 바꿔주는 역할을 하는가 보네요? 컴퓨터는 2진수, 8진수, 16진수를 지원한다고 했는데 걔네들을 위한 형변환은 없을까요? 

| Base        | Syntax  |
| ----------- | ------- |
| binary      | `bin()` |
| octal       | `oct()` |
| hexadecimal | `hex()` |

똑같습니다. "()"안에 바꾸고 싶은 data를 담아 두면 어느 진법으로 나타내었는지 상관없이 해당 data를 명령하는 진법으로 바꾸어 줍니다. 그렇다면 저번 문서에서 처음 봤던 `bin()`이 무슨 역할을 했는지 알 수 있겠죠?

### Data loss

강제적으로 data type을 바꾸게 되면 data의 손실이 일어나는 경우도 있습니다. 어떤 경우가 있을까요?

```python
a = 3.14
print(int(a))
```

```python
# 출력 결과
3
```

위의 경우는 `float`이었던 `a`를 `int`로 바꾸었을 때 일어나는 Data loss 입니다. 소수부분의 정보가 사라진 것을 확인 할 수 있습니다. 이처럼 큰 범위를 표현할 수 있는 data type에서 작은 범위의 data type으로 형변환을  강제로 시키면 Data loss가 일어납니다.

### bool conversion?

`Boolean type`은 오직 두가지 상태밖에 없습니다 `True`와 `False`뿐 입니다. 그런데 어떻게 bool로 형변환을 할 수 있을까요?  

```python
print("bool(1) :",bool(1))
print("bool(0) :",bool(0))
print("bool(-2) :",bool(-2.2))
```

```python
# 출력 결과
bool(1) : True
bool(0) : False
bool(-2.2) : True
```

`Numeric  type`에서는 0은 `False`  나머지는 전부 `True`로 형변환이 됩니다.

```python
print("bool('hello') :",bool('hello'))
print("bool('') :",bool(''))
```

```python
# 출력 결과
bool('hello') : True
bool('') : False
```

`Text type`은 "" 나 ' ' 안에 아무것도 들어있지 않으면 `False` 나머지는 전부 `True`로 형변환이 됩니다.

`Sequence`, `Mapping`, `Set` type은 아직 배우지 않았지만 방식은 비슷합니다. 예시를 보고 그냥 그렇구나를 이해해 주세요.

```python
# list
print("bool([]) :",bool([]))
print("bool([1,2,3]) :",bool([1,2,3]))
# tuple
print("bool(()) :",bool(()))
print("bool((1,2,3)) :",bool((1,2,3)))
# dict
print("bool({}) :",bool({}))
print("bool({1:'a',2:'b',3:'c'}) :",bool({1:'a',2:'b',3:'c'}))
# set
print("bool(set()) :",bool(set()))
print("bool(set(1,2,3)) :",bool(set(1,2,3)))
```

```
bool([]) : False
bool([1,2,3]) : True
bool(()) : False
bool((1,2,3)) : True
bool({}) : False
bool({1:'a',2:'b',3:'c'}) : True
bool(set()) : False
bool(set(1,2,3)) : True
```

문자열과 동일하게 안에 무엇인가 담겨져 있으면 `True`로, 아무것도 없다면 `False`로 변환하게 됩니다.

> Tip👀
>
> `Sequence`, `Mapping`, `Set` type 끼리의 형변환에는 각 data structure에 대한 이해가 필요합니다. 그렇기 때문에 [Built-in Data structure](./Built-in-Data-structure.md)에서 다루도록 하겠습니다.

## Implicit conversion

사실 여러분들은 여태 문서를 꼼꼼히 읽고 오셨다면 `Implicit conversion`에 대한 예시 또한 보고 오셨을 것입니다. 

처음 보는 단어인데 어떻게 이해하면서 넘어갈 수 있었는지 궁금하실 겁니다. 다음은 [Data types](./Operators.md#arithmetic-operators)에서 `Implicit conversion`가 일어난 예시입니다.

```python
# 여려분이 알고 있는 수학적 지식에서 벗어나지 않습니다.
print("2 + 2.4 = ",2 + 2.4)
print("10 / 4 = ",10 / 4)
print("10 / 2 = ",10 / 2) # 추가된 예시
```

```python
# 출력 결과
2 + 2.4 =  4.4
10 / 4 =  2.5 
10 / 2 =  5.0 
```

첫 번째 부터 차근 차근 보도록 하죠. `Add`를 기준으로 왼쪽은 분명 `int` 타입, 오른쪽은 `float` 타입입니다. 서로 다른 타입이 더 해지면 그 결과값은 두 가지 타입을 모두 가지게 될까요? 그렇지 않습니다. 결과 값만 봐도 4.4는 `float`이란걸 알 수 있습니다. 그럼 `int`는 어떻게 되었을까요? 

`int`는 `Interpreter`에서 알아서 `float`으로 바꿔주고 난 후, 덧셈 처리를 진행하게 됩니다. 뺄셈도 마찬가지입니다!

두 번째 예시를 보도록 합시다. `int` 와 `int`연산에서 뜬금없이 `float`가 결과로 나왔습니다. 물론 여러분들이 보시기엔 당연히 실수가 나오는 것이 당연하겠지만 컴퓨터는 이해하지 못합니다.  당장 세 번째 예시만 보더라도 `10`을 `2`로 나누면 정수인 `5`가 나오는 것이 당연한데 `float`인 `5.0`이 나오는 것을 확인할 수 있습니다.(`5.0`이 왜 `float`인지 모르겠다구요?? [Data types](/Data-types.md#numeric)을 봐주세요.) 

그렇다면 컴퓨터는 이해하지 못한다면서 어떻게 출력은 실수로 나올  수 있을까요?

사실 이 또한 `Interpreter`가 알아서 data type을 변환시켜 줍니다.  일반적으로, 10 / 4 = 2.5인 것을 일반 사용자는 당연하게 받아지고 있습니다. 이에 대해 `Interpreter`는 우리가 생각한 결과가 나오도록 작업을 해둔 것입니다.

위의 `Explicit conversion`과 달리 우리가 data type을 바꾸라고 명령하지 않았음에도 불구하고 자동적으로 data type이 바뀌는 것을 `Implicit conversion`이라고 합니다.

> Tip👀
>
> `interpreter`라는 건 무엇 일까요?  설명하기 전에 기초적인 내용을 알아봅시다. 
>
> 컴퓨터는 0과 1로 이뤄진 숫자밖에 이해를 하지 못하기 때문에 Programming language를 Machine language로 바꿔주는 방식이 꼭 필요합니다. 이러한 작업에는 두 가지 방식이 있습니다. 
>
> `compile` 방식과 `interpreter` 방식입니다. 이에 따라 언어의 종류도 크게 `compile language` 와 `interpreter language`로 나뉘게 되는 겁니다. 
>
> `interpreter`는 사용자가 적은 코드 한줄한줄 컴퓨터에게 기계어로 번역해서 알려주어 컴퓨터가 해당 명령어를 실행하도록 합니다. 
>
> 반대로 `compile`은 사용자가 적은 코드 전체를  기계어로 번역한 뒤에 컴퓨터에게 넘겨주어 명령어를 실행하도록 합니다. 
>
> 여기서 생각해보면 `interpreter`는  프로그램을 실행시키는 도중에 통역사가 되어 컴퓨터에게 실시간으로 번역을 해주고, `compile`은 중간에 거치는 작업 없이 바로 컴퓨터가 이해하고 작동할 수 있도록 합니다.
>
> 그렇기 때문에 `interpreter language` 보다 `compile language`가 훨씬 빠르다고 볼 수 있습니다.