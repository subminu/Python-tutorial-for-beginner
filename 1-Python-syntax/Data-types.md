# Data types
저번에는 variable이란 무엇이며, 어떻게 생성하는지를 알아보았습니다. 이번에는 어떠한 data type이 있는지, 왜 data type이 필요한지를 살펴보도록 하겠습니다.

| Type       | Statement                            |
| :-------   | :---------------------------------   |
| Text       | `str`                                |
| Numeric    | `int`, `float`, `complex`            |
| Boolean    | `bool`                               |
| Sequence   | `list`, `tuple`, `range`             |
| Mapping    | `dict`                               |
| Set        | `set`, `frozenset`                   |
| Binary     | `bytes`, `bytearray`, `memoryview`   |

> Tip👀
>
> 이번에 알아볼 Data type들은 `text`, `numeric`, `boolean`까지이니 나머지 type들은 아 그냥 저런게 있나보다 하고 넘어가주세요!

## Text
일반적으로 생각하는 문자, 문자열(string)을 말합니다. python에서 ""또는 ''로 둘러쌓인 것들 모두를 Text type으로 볼 수 있습니다.


```python
a = "안녕하세요"
b = '123'
c = "python"
print(a,b,c)
```

```python
# 출력 결과
안녕하세요 123 python
```


## Numeric
일반적으로 생각하는 숫자들에 해당됩니다. 여기서 세부적으로 정수의 경우 `int`(integer), 실수의 경우 `float`, 복소수의 경우 `complex`로 나뉩니다.

`complex`의 경우 허수단위를 **i**가 아닌 **j** 혹은 **J**로 사용합니다.


```python
a = 1
b = 2.5 # 소수 부분이 0인 경우 2.0과 같이 표기하여 정수와 구분합니다.
c = 1+3j
print(a,b,c)
```

```python
# 출력 결과
1 2.5 (1+3j)
```


지금 예시로 쓰인 숫자들은 여러분이 늘 쓰시는 10진수로 나타내어져 있습니다. 컴퓨터는 10진수 이외에 2진수, 8진수, 16진수를 지원합니다. 컴퓨터는 10진수보다 2진수, 8진수, 16진수가 더 익숙하니까 말이죠. (왜 더 익숙한지에 대해선 아래의 `Tip👀`에 적혀있습니다.) 다음 예시를 통해서 어떻게 10진수와 구별하는지 알아봅시다.


```python
# 전부다 같은 숫자를 가리키고 있다.
decimal = 12
binary = 0b110 # 2진수
octal = 0o14 # 8진수 
hexadecimal = 0xc # 16진수
```

| number        | statement |
| :------------ | :-------- |
| `binary`      | ```0b```  |
| `octal`       | ```0o```  |
| `hexadecimal` | ```0x```  |

앞에 숫자 0과 함께 `b`, `o`, `x`를 붙여 자신의 진법이 어떤 진법인지 알려주고 있음을 확인할 수 있습니다.

## Boolean
이 type같은 경우 `True`와 `False`에만 해당됩니다.(소문자로 적으면 interpreter가 boolean값으로 판단하지 않습니다!)

ex1)


```python
a = True
b = False
print(a,b)
```

    True False

ex2)

```python
c = true # 소문자로 적으면 안됩니다!
print(a)
```


```python
# 출력 결과
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)

<ipython-input-14-3aec30da9bd0> in <module>
----> 1 c = true # 소문자로 적으면 안됩니다!
      2 print(a)
NameError: name 'true' is not defined
```


> Tip👀
>
>  ​	컴퓨터가 이해할 수 있는 유일한 언어가 0,1인 것은 여러분들도 잘 알고 있을 것입니다. 그러나 python 코드에는 0과 1뿐만 아니라 영어로도 적고 문자열을 통해 다양한 문자들도 적는데 어떻게 컴퓨터는 이해할 수 있을까요? 이는 모두 이진법으로 바뀌어 지는 과정이 포함되어 있습니다.
>  ​	이진법(`binary`)은 0과 1을 통해 수를 표현하는 방식인데요. 컴퓨터에서 bit 단위로 표현하고 있습니다. 처음 코딩을 접하는 분은 bit(**b**inary dig**it**)가 무엇인지도 잘 모를 것이라 생각합니다. bit는 이 0과 1의 조합으로 나타낼 수 있는 상태를 표현하는 최소 단위라고 볼 수 있습니다.
>
>  ​	예를 들어보죠. bit는 `binary digit`이기 때문에 표현할 수 있는 상태가 2가지 밖에 없습니다(0 과 1, `False` 와 `True`). 그렇다면 이 bit를 여러개 이어붙여 8개의 bit로 만들었다고 칩시다. 8개로 이뤄진 bit가 나타낼 수 있는 상태는 몇가지 일까요? 2^8가지가 됩니다. 이렇게 8개가 모인 bit를 새로운 단위인 byte라고 부르며, 더 많이 이어 붙이면 kilobyte, megabyte, gigabyte..이렇게 단위가 점점 커지게 됩니다. 그럴수록 표현할 수 있는 가짓수는 많아지게 되는거죠.
>
>  ​	아래의 posts는 어떻게 숫자와 문자를 이진수로 바꾸는지 알려줍니다.
>
> - [컴퓨터가 0과1로 통신하는 원리를 알아봅시다](https://post.naver.com/viewer/postView.nhn?volumeNo=10059808&memberNo=29381200)
>
> - [아스키(ASCII)코드와 유니코드(Unicode)의 이해](https://whatisthenext.tistory.com/103)
>
> - [컴퓨터에 숫자가 저장되는 방법](https://github.com/paxbun/c-cpp-tutorial/tree/master/2-structure-of-computers#%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%90-%EC%88%AB%EC%9E%90%EA%B0%80-%EC%A0%80%EC%9E%A5%EB%90%98%EB%8A%94-%EB%B0%A9%EB%B2%95)(2진수. 8진수, 16진수를 사용하지는지 나와있음.)
> 
> ​    아스키코드와 유니코드는 문자를 숫자로 identical 하게 mapping한 table이라고 보시면 됩니다. 현재, python의 문자열들은 unicode를 통해 숫자로 변환 시키고 있습니다.

## Why data types are important
사실 이 이야기는 Python에만 국한되는 이야기가 아니라 다른 언어에서도 적용되는 이야기 입니다. 그러나 Python에서는 type에 대한 특별한 mention을 하지 않는 경우가 대부분이기 때문에 왜 중요한 것인지 느끼지 못할 때가 많습니다. 그럼에도 불구하고 필요한 이유를 꼽자면 다음과 같습니다.

- data type을 설정해 놓으면 memory 낭비를 줄여줍니다.
- 각 data type끼리 연산하는 방식을 따로 정의할 수 있습니다.
- 다른 사람들과의 코드를 공유할 때, 자신이 나중에 코드를 다시 볼 때, 이해하기 수월합니다.(이는 나중에 function과 함께 설명하도록 하겠습니다.)

### memory 낭비?
C/C++같은 경우 메모리에 직접 접근할 수있지만 Python의 경우 "Python memory manager"에 의해 내부적으로 자동 관리되어 집니다. 그렇기 때문에 일반 사용자가 Python에서 메모리에 직접 접근하는 일이 없어 이해가 되지 않으실 겁니다. 간단히 설명하자면, data type을 제대로 mention하면 전체 100의 공간에서 10의 공간을 사용하겠다고 해놓고 2의 공간만 사용하여 8의 공간을 낭비하는 일이 없어진다는 것입니다.

>Tip👀 
>
>Python과 다르게 C/C++은 엄격하게 data type을 mention하도록 되어 있으며 data type또한 python보다 훨씬 많습니다. [C의 정수 자료형](https://github.com/paxbun/c-cpp-tutorial/tree/master/4-types-and-variables#c%EC%9D%98-%EC%A0%95%EC%88%98-%EC%9E%90%EB%A3%8C%ED%98%95)만 하더라도 얼마나 엄격하게 다루고 있는지 알 수 있습니다.

### data type끼리의 연산?
상식적으로 3+5가 8임을 잘 알고 있을 것입니다.


```python
# int
print(3+5)

#float
print(1.2+2.3)

# complex
a = 1+5j
b = 2+2j
print(a+b) 
```

```python
# 출력 결과
8
3.5
(3+7j)
```


위를 보면 알 수 있듯이, 일반적인 수학지식에서 벗어나지 않습니다.

그렇다면 "3" + "5"의 값은 무엇일까요?


```python
print("3"+"5") # "8"이 나올까?
```

    35


"8"이 나오는게 아니라 "35"가 나오게 됩니다. 상식적으로 이해하기 힘들 수 있습니다. 하지만 다음의 예를 한 번 봅시다. 


```python
print("My name is "+"Python") # 왠지 "My name is Python"이 나올것 같다.
```

    My name is Python


문자열끼리의 연산은 숫자처럼 더해지는게 아니라 어어 붙여진다는 사실을 알 수 있었습니다. 이처럼 python은 사용자가 일반적으로 생각할 수 있는 연산 결과를 보여줄 수 있도록 사전에 자료형을 정의 하였습니다.(C/C++의 경우는 조금 다르지만요..)

> Tip👀 
>
>  ​    Python에서는 사용자 입맛대로 data type을 만들고 어떻게 연산 할 것인지 정의 할 수 있습니다!(어떻게 정의하는 지는 class/object에서 배울 수 있습니다!💻)

여기까지가 Data type입니다. 예시들을 보시면 아직 배우지 않은(?) +를 예시에서 사용했었는데요, 잠깐 언급하자면 +,-,\*,/와 같은 사칙연산에 쓰이는 것을 **연산자**라고 부릅니다. python에는 다양한 연산자가 존재합니다. 다음에는 어떠한 연산자가 있고 어떻게 쓰이는지 알아보도록 합시다.

---

[Next-Operators](./Operators.md)