# Operators
Python에는 사칙연산(+, -, \*, /)뿐만 있는게 아니라 다양한 연산자(Operators)가 있습니다. "=" 처럼 잠깐이지만 할당 연산자(Assignment operator)도 보았습니다. Python에서 지원하는 연산자의 종류는 다음과 같습니다.

- Arithmetic operators
- Assignment operators
- Comparion operators
- Logical operators
- Identity operators
- Membership operators
- Bitwise operators

> Tip👀 
>
> 엄청 많은 종류의 operators가 있지만 전부 기억할 필요가 없습니다! 그냥 이런게 있구나 라는 정도만 알아 두었다가 필요할 때마다 검색하면서 학습하는걸 추천드립니다.

## Arithmetic operators
여러분이 일반적으로 알고 있는 수학연산에 이용되는 연산자들 입니다, 보기 쉽게 표로 표현 하자면 다음과 같습니다.

| Operator | Name           | Example |
| :------- | :------------- | :------ |
| `+`      | Addition       | x + y   |
| `-`      | Substraction   | x - y   |
| `*`      | Multiplication | x * y   |
| `/`      | Dicision       | x / y   |
| `//`     | Floor division | x // y  |
| `%`      | Modulus        | x % y   |
| `**`     | Exponetiation  | x ** y  |

생소하게 느껴지실 부분만 설명드리자면 `//`은 몫을 구하는 연산자, `%`는 나머지를 구하는 연산자 입니다.

```python
# 여려분이 알고 있는 수학적 지식에서 벗어나지 않습니다.
print("2 + 2.4 = ",2 + 2.4)
print("3 - 1 = ", 3 - 1)
print("4 * 5 = ",4 * 5)
print("10 / 4 = ",10 / 4)
print("10 // 4 = ",10 // 4)
print("10 % 7 = ",10 % 7)
```

```python
# 출력 결과
2 + 2.4 =  4.4
3 - 1 =  2
4 * 5 =  20
10 / 4 =  2.5
10 // 4 =  2
10 % 7 =  3
```


## Assignment operators
할당 연산자의 종류는 다음과 같습니다.

| Operatore | Example | Same As    |
| :--------- | :------ | :--------- |
| `=`       | x = 3   | x = 3      |
| `+=`      | x += 3  | x = x + 3  |
| `-=`      | x -= 3  | x = x - 3  |
| `*=`      | x *= 3  | x  = x * 3 |
| `/=`      | x /= 3  | x = x / 3  |
| `//=`     | x //= 3 | x = x // 3 |
| `%=`      | x %= 3  | x = x % 3  |
| `**=`     | x **= 3 | x = x ** 3 |
| `&=`      | x &= 3  | x = x & 3  |
|  `\|=`  | x \|= 3| x = x \| 3 |
| `^=`      | x ^= 3  | x = x ^ 3  |
| `>>=`     | x >>= 3 | x = x >> 3 |
| `<<=`     | x <<= 3 | x = x << 3 |

뭔가 종류도 많아 보이기도 하지만 실상은 "=" 연산자와 다른 연산자와의 축약형이라고 볼 수 있습니다. 아직 배우지 않은 연산자와 처음 보는 연산자가 있어도 당황하지 마세요.

## Comparison operators
비교 연산자라고 하죠? [Variables](./Variables.md#Variables)에서 할당 연산자인 "="이 흔히 알고 있는 같다의 의미가 아니라서 어리둥절 했을 텐데요. 다음의 연산자 표를 통해 같다의 의미를 가진 연산자가 무엇인지 알 수 있을 것입니다.

| Operatore | Mean                      | Example |
| :-------- | :------------------------ | :------ |
| `==`      | Equal                     | x == y  |
| `!=`      | Not equal                 | x != y  |
| `>`       | Greater than              | x > y   |
| `<`       | Less than                 | x < y   |
| `>=`      | Grearter than or equal to | x >= y  |
| `<=`      | Less than or equal to     | x <= y  |

여기서 주의해야할 점은 `!=`, `>=`, `<=`을 할당 연산자의 축약형으로 착각하면 안된다는 점입니다. 그러나 직관적으로 이해가 되는 연산자라 그럴 일은 없겠죠..?😊

>Tip👀 
>
>다음의 예시를 살펴 봅시다.
>``` python
>a = x + y
>```
>이 예시에는 a에는 당연히 x와 y를 합한 결과값이 저장됩니다. 가령 3 + 5라고 하면 a에는 8이라는 결과값이 들어가겠지요.
>```python
>b = x > y
>```
>그렇다면 b의 경우에는 어떠한 값이 저장될까요? 비교연산자의 결과값은 항상 `True` 또는 `False` 값으로 나오게 됩니다. 가령 3 > 5인 경우에는 `False`를, 2.4 > 2의 경우에는 `True`를 반환하게 됩니다. `True` 와 `False`는 무엇이냐구요? 문자열 같다구요? [Data types](./Data-types.md#Boolean)를 보고 오세요.


```python
print("3 == 3.0 : ", 3 == 3.0)
print("10 != 9 : ", 10 != 0)
print("3 > 2 : ", 3 > 2)
print("5 < 3 : ", 5 < 3)
print("5 >= 5 : ", 5 >= 5)
print("5 <= 3 : ", 5 < 3)
```

```python
# 출력 결과
3 == 3.0 :  True
10 != 9 :  True
3 > 2 :  True
5 < 3 :  False
5 >= 5 :  True
5 <= 3 :  False
```


## Logical operators
여태까지의 연산자들의 특징을 보면 다음과 같습니다. 

```
(operand1) (operator) (operand2)
```

여기서 `operand1`과 `operand2`의 Data type이 Numeric인 경우만을 다뤘습니다. 하지만 앞서 True와 False 같은 Boolean type도 있음을 확인했었습니다. Boolean type이 존재하면 당연히 Boolean 연산을 지원하는 연산자가 있습니다.

| Operatore | Description                                     | Example           |
| :-------- | :---------------------------------------------- | :---------------- |
| `and`     | Returns True only if both of operands are true  | x > 3 and x < 5   |
| `or`      | Return False only if both of operands are false | x >= 3  or x >= 5 |
| `not`     | Reverse the result                              | not(x == y)       |

> Tip👀 
>
> 여기서 조심해야할 점이 있습니다. 컴퓨터가 직접 `and`, `or` operator를 수행할 때를 가정하면서 생각해보겠습니다.
>
>
> * case 1 : (operand1) and (operand2)
>
> 만약 (operand1)의 값이 `False`라면 컴퓨터는 (operand2)를 계산할까요? 정답은 계산하지 않습니다. (operand1)에서 `False`가 나오면 그 즉시 `False`를 반환하게 됩니다.
>
> * case 2 : (operand1) `or` (operand2)
>
> or`도 마찬가지 입니다. 만약 (operand1)의 값이 `True`라면 컴퓨터는 (operand2)를 계산하지 않고 그 즉시 `True`를 반환하게 됩니다.
>
> 예시를 보여드릴 테지만 굳이 지금 이해하지 않으셔도 됩니다. [Functions](./Functions.md)를 배우고 오시면 이해하는데 도움이 될 것입니다.
>
> ```python
> def operand_return_True():
>    print("operand_return_True() was ran.")
>    return True
> 
> def operand_return_False():
>    print("operand_return_False() was ran.")
>    return False
> 
> print("--- start case 1 : and ---")
> print(operand_return_False() and operand_return_True())
> print("----------- end ----------")
> print()
> print("--- start case 2 : or  ---")
> print(operand_return_True() or operand_return_True())
> print("---------- end -----------")
> ```
>
>   
>
> ```python
> # 출력 결과
> --- start case 1 : and ---
> operand_return_False() was ran.
> False
> ----------- end ----------
> --- start case 2 : or  ---
> operand_return_True() was ran.
> True
> ---------- end -----------
> ```


## Identity operators
사실 이 부분은 [Class/Objects](./Class-Object.md)를 배우고 나서야 제대로 이해할 수 있을 것이라 생각하지만 종류를 알려드리자면 다음과 같습니다.

| Operatore | Description                                                  |
| :-------- | :----------------------------------------------------------- |
| `is`      | Returns True only if both of operands have a same value and data type(object,same memory location) |
| `is not`  | Return False only if both of operands have a same value and data type(object,same memory location) |

설명을 보시면 `is`는 두 개의 피연산자가 같은 값과 데이터 타입이 같을 때만 `True`를반환한다고 하는데 어떤 의미인지 다음 예시를 통해 감을 잡아봅시다. 


```python
print(3 is 3)
print("debugging" is "happy")
print(3 is 3.0)
```

```python
# 출력 결과
True
False
False
```

위의 예시를 보면, `3 is 3`와 `"debugging" is "happy"`가 왜 각각 `True`와 `False`가 나왔는지 바로 이해가 가실 겁니다. 자명하게 같은 것과 내용이 다른 두 문자열을 비교하고 있으니까요. 그러나 `3 is 3.0`의 경우는 조금 다릅니다. 둘 다 분명 3을 말하는 것 같은데 왜 같지 않다고 말하는 걸까요? 

이유는 Data type이 다르기 때문입니다. 3은 `int`, 즉 Numeric type 중 정수 이며 3.0은 `float` 실수이기 때문에 근본적으로 다르다고 보고 `False`라는 최종 결과값이 반환된 것이라고 볼 수 있습니다.

## Membership operators
사실 이 부분은 [Built-in Data structure](./Built-in-Data-structure.md)에 대한 부분을 알고 있어야 이해가 쉽지만 다음의 연산자가 있다는 것은 알아두세요.

| Operatore | Description                                                  |
| :-------- | :----------------------------------------------------------- |
| `in`      | Returns True only if a sequence contains the specified value |
| `not in`  | Return True only if a sequence doesn't contain the specified value |

Sequence가 아직 무엇인지 모르니 아래의 코드를 통해 직관적으로 이해하도록 합시다. 지금 이해 못하더라도 전혀 상관이 없습니다!


```python
# "[]","()","{}"의 기호는 신경쓰지 말고 직관적으로 봐주세요!
print(3 in [1,2,3]) 
print(5 in [1,2,3])
print("현풍전산" in ("삼성전자","현풍전산", "Google", "Apple"))
print("happy" not in {"debugging", "naming", "machine leaning"})
```

```python
# 출력 결과
True
False
True
True
```


## Bitwise operators
여러분이 binary를 직접 다룰일은 많지 않지만 python에서 제공하는 operators를 지금 한번 훑어보는 것도 나중에 필요할 때, 도움이 될 것입니다.

| Operators | Name                 | Desciption                                                   |
| :-------- | :------------------- | :------------------------------------------------------------ |
| `&`       | AND                  | Sets each bit to 1 only if  both bits are 1. Otherwise, sets 0. |
| `\|`       | OR                   | Sets each bit to 0 only if  both bits are 0. Otherwise, sets 1. |
| `^`       | XOR                  | Sets each bit to 0 only if both bits have same value. Otherwise, sets 1. |
| `~`       | NOT                  | Returns the complement of x, the number you get by switching each 1 for a 0 and each 0 for a 1. This is the same as -x - 1.                                        |
| `<<`      | Zero fill left shift | Shift left by pushing zeros in from the right and let the leftmost bits fall off |
| `>>`      | Signed right shift   | Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off |

여기서 Name이 OR에 해당하는 "\|"은 Ender 키 위에 있는 \와 shift를 같이 누르면 칠 수 있습니다. 예시를 통해 이해해도록 하죠. 혹시나 python에서 이진수를 표현하는 방법을 모르시는 분은 [Numeric](./Data-types.md#Numeric)을 보고 와주세요!


```python
a = 0b101
b = 0b111
c = 0b1001001
print("a & b = ", bin(a & b)) # bin()을 처음 보는거 같은데요..?
print("a | b = ", bin(a | b))
print("a ^ b = ", bin(a ^ b))
print("~a = ", bin(~a))
print("c << 1 = ", bin(c << 1))
print("c << 2 = ", bin(c << 2))
print("c >> 1 = ", bin(c >> 1))
print("c >> 3 = ", bin(c >> 3))
```

```python
# 출력 결과
a & b =  0b101
a | b =  0b111
a ^ b =  0b10
~a =  -0b110
c << 1 =  0b10010010
c << 2 =  0b100100100
c >> 1 =  0b100100
c >> 3 =  0b1001
```


`&` : 두 개의 2진수의 각자리 숫자를 비교하여 각자리 숫자들이 둘다 1인 경우 1을 반환해주고 그 이외의 경우는 0을 반환시킨다.

`|` : 두 개의 2진수의 각자리 숫자를 비교하여 각자리 숫자들 중 하나라도 1이 있으면 1을 반환 해주고 그 이외의 경우는 0을 반환시킨다.

`^` : 두 개의 2진수의 각자리 숫자를 비교하여 각자리 숫자들 서로 숫자가 다르면 1을 반환 해주고 그 이외의 경우는 0을 반환시킨다.

`~` : 2진수의 각 자리 수를 반대로 바꾼다. (0을 1로 1을 0으로) 그렇게 바꾼 값은 -(x+1)을 2진수로 표현한 값과 같다.

`<<` : 뒤에 있는 수만큼 bit자체를 화살표 방향으로 민다.(여기서 밀고 남은 빈자리는 0을 채워 넣는다.)

`>>` : 뒤에 있는 수만큼 bit자체를 화살표 방향으로 민다. (여기서 밀린 값은 그냥 버린다.)

>Tip👀 
>
>중간에 `bin()`을 보시고 당황하지 않으셨나요?? 기본적으로 bitwise operators의 output 값은 decimal 값으로 반환하도록 되어있습니다. 10진법으로 나타내어진 수를 보고 바로 이해하긴 힘드니, 교육적인 목적으로 `Implicit type conversion`을 진행하였습니다.

팁이라고 알려준다 해놓고 `Implicit type conversion(명시적 형변환)`이라는 새로운 용어를 꺼내들었습니다. 걱정하지마세요. 다음 강의에 배울 내용은 `Type conversion(Type Casting)`에 관련된 내용입니다. 형변환에는 어떠한 종류가 있고(명시적 형변환, 암묵적 형변환) 왜 형변환이 존재햐야하는지 알아보도록 하겠습니다.
[Next-Type conversion(Typecasting)](./Type-conversion(Typecasting).md)
