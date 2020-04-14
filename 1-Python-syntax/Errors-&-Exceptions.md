# Errors & Exceptions

이번 문서에서는 error와 exception이 무엇인지 알아보고, 해당 exception을 어떻게 다룰 수 있는지, 마지막으로 사용자 정의 exception은 어떻게 만들 수 있는지 알아보도록 하겠습니다.

## What is errors & exceptions

흔히, 코딩을 하는 상황에서 자신이 의도하지 않은 방향으로 프로그램이 실행되면 error가 났다고 표현을 하는데요. Python에서는 이를 크게 두가지로 나누어 정의합니다. **Syntax errors**와 **exceptions**입니다. 

## Syntax errors

코딩을 하다보면 가끔씩 python 문법에 맞지 않게 작성할 수도 있는데요. 이때 코드를 실행시키려고 하면 error를 발생시키는데 이때 일어나는 error를 **syntax error**라고 합니다.

```python
for i in range(5) # ':'을 붙이지 않음
    print(i)
```

```python
# 출력 결과
  File "<stdin>", line 1
    for i in range(5)
                    ^
SyntaxError: invalid syntax
```

위의 출력 결과 처럼, interpreter가 문제가 되는 지점을 `^`으로 가리켜 줍니다.

## Exceptions

Python 코드를 문법에 맞게 완벽하게 코드를 작성했음에도 불구하고 실행을 시키면 오류가 나는 경우가 있습니다. 실행을 시켜야지만 detect 되는 error를 **exception**라고 합니다. 

```python
print(1/0)
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
```

출력 결과의 마지막 줄을 보면 어떤 error가 일어났는지 알 수 있습니다. 해당 예시의 경우에는 `ZeroDivisionError`에서 0으로 나누었다는 설명과 함께 출력 된 것을 알 수 있습니다.  

### Built-in Exceptions

위와 같은 예시에서 사용자가 정의하지 않은 error임에도 불구하고 python에서는 error가 생기면 프로그램 실행을 멈추고 어떤 error가 발생했는지 알려줍니다. 이렇게 코딩을하면서 일어날 법한 error들을 사전에 정의한 exceptions들을 **built-in exception**이라고 합니다. 

OOP에서 배웠듯이 모든 것들이 object이라 하였습니다. 그렇기 때문에 당연히 built-in exception 또한 class로 정의가 되어있습니다. `BaseException`이란 class의 상속을 통해 여러 종류의 error들을 정의하였습니다.

Built-in Exception의 종류가 많기 때문에 여기서는 전부 다루지 않겠습니다. 해당 종류에 대한 정보를 알고 싶으시면 python 공식 문서를 통해 확인할 수 있습니다.

- [Built-in Exceoption - eng](https://docs.python.org/3/library/exceptions.html)
- [Built-in Exceoption - kor](https://docs.python.org/ko/3/library/exceptions.html)

## Handling Exceptions

Built-in exceptions를 통해 정의하지 않은 error에 대해 알 수 있는 것은 좋지만, built-in exception이 실행되면 프로그램 자체가 종료되고 오류가 일어난 정보를 출력해버리는 것이 문제입니다. 다음의 예시를 보도록 합시다.

```python
while True:
    x = int(input("How old are you? "))
    if x >= 18:
        print("you can vote.")
    else:
        print("you can't vote.")
```

위와 같이, 투표권을 확인하는 프로그램을 만들었다고 가정해봅시다. 여기서, `input()`을 통해 입력받은 값은 `str`으로 들어오기 때문에 `int`로 explicit type conversion이 필요합니다. 사용자가 숫자만 입력해주면 좋겠지만 실수로 문자를 입력했다고 합시다.

```python
# 입력
18
스물
```

```python
# 출력 결과
you can vote.
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: invalid literal for int() with base 10: '스물'
```

다음과 같이 `ValueError`와 함께 프로그램이 종료되어 버립니다. 우리가 원하는 것은 위와 같은 상황에서 프로그램이 종료되지 않고 다시 입력할 수 있도록 하는 것입니다. 이때 필요한 것이 **try & except**입니다.

### Try & except

해당 keyword를 사용하게 되면 프로그램을 강제 종료하는 대신에, 특정 행동을 수행할 수 있도록 정의 할 수 있습니다.

```python
try:
    <code, having possibility of error>
except <ErrorName>:
    pass
except <ErrorName>:
    pass
except:
    pass
```

`try` 다음에 오는 code block은 오류가 일어날 수 있는 코드를 적어두면, 해당 code block내에서 오류가 일어날 시, `except`의 `<ErrorName>`과 동일한 Error를 찾아서 실행합니다. `except` 뒤에 아무런 `<ErrorName>`을 적지 않으면 모든 error에 대하여 실행하는 구문이 됩니다. 

만약, error가 발생했음에도 불구하고 `except`에서 해당 error에 대한 특정 코드를 정의해 놓지 않으면 프로그램이 강제 종료되고 error에 대한 출력 결과가 나오게 됩니다.

```python
while True:
    try:
        x = int(input("How old are you? "))
        if x >= 18:
            print("you can vote.")
        else:
            print("you can't vote.")
    except ValueError:
        print("please write in digit.")
```

```python
# 입력
18
스물
```

```python
# 출력 결과
you can vote.
please write in digit. 
```

try & except 구문을 이용하여 새롭게 짠 프로그램을 이용하였을 때, 다음과 같이 프로그램이 종료되지 않고 계속 실행되는 것을 알 수 있습니다.

### Try & finally

`finally`는 `try`뒤에 오는 code block에서 어떠한 경우가 일어나든지 간에 finally를 실행하게 됩니다.

```python
try:
    print(x) # x를 정의하지 않음
finally:
    print("done")
```

```python
# 출력 결과
done
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
NameError: name 'x' is not defined
```

프로그램이 종료되기 전에 finally에 해당하는 `print("done")`을 실행한뒤 종료되었음을 알 수 있습니다.

## User defined exception

Built-in exception이외에 다른 사용자 정의 exception을 만들고 싶을때가 있을 수 있습니다. 위의 예시에서 나이를 입력하라고 할 때, 음수 값은 틀린 값이 됩니다. 이러한 경우에 대한 exception을 만들고 싶을 때, 다음과 같이 class로 정의하면 됩니다.

```python
class NegativeIntError(Exception):
    pass
```

Exception class로 부터 상속을 받으면 됩니다. 새롭게 만든 exception으로 다시 작성하면 다음과 같습니다.

```python
while True:
    try:
        x = int(input("How old are you? "))
        if x >= 18:
            print("you can vote.")
        if x < 0:
            raise NegativeIntError("Do not allow negative integer")
        else:
            print("you can't vote.")
    except ValueError:
        print("please write in digit.")
```

```python
# 입력
-1
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 7, in <module>
__main__.NegativeIntError: Do not allow negative integer
```

마지막 줄을 보시면, `__main__.NegativeIntError`의 사용자 정의 exception으로 실행된 것을 확인할 수 있습니다. 또한 "Do not allow negative integer"에 대한 내용 또한 출력된 것을 알 수 있습니다. 그러나 NegativeIntError를 받을 수 있는 except가 없기 때문에 프로그램이 중지되고 오류를 출력하게 됩니다. 프로그램이 중지되는 것을 원치 않는다면 NegativeIntError를 받는 except를 추가하면됩니다.

```python
while True:
    try:
        x = int(input("How old are you? "))
        if x >= 18:
            print("you can vote.")
        if x < 0:
            raise NegativeIntError
        else:
            print("you can't vote.")
    except ValueError:
        print("please write in digit.")
    except NegativeIntError:
        print("Do not allow negative integer")
```

```python
# 입력
-1
```

```python
# 출력 결과
Do not allow negative intege
```

프로그램이 종료되지 않고 계속 실행됨을 알 수 있습니다.

---

[Go - Modules](./Modules.md)