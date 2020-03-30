# if-else

Coding을  할 때, 자주 쓰게 되는 구문중 하나인 조건문입니다. if-else를 같이 보기 전에, if 문을 어떻게 쓰는지 알아 보도록 합시다.

## if

```python
if <condition>:
    pass # pass는 아무런 동작도 하지 않겠다는 말입니다!
```

`<condition>`은 꼭 `<>`으로 감싸주어야 하는 것이 아닙니다. type이 `bool`이라면  **어떠한 것**이라도 올 수 있습니다. 

```python
true_data = True
false_data = False
if bool_data:
    print("checked_1")
if false_data:
    print("checked_2")
```

```python
# 출력 결과
checked_1
```

다음과 같이 `bool`로 선언된 값 자체를 넣을 수도 있으며,

```python
a = 12
if a % 4 == 0 and a % 3 == 0:
    print("checked_1")
if a == 7 or a / 5 == 2:
    print("checked_2")
```

```python
# 출력 결과
checked_1
```

return type이 `bool`인 연산자를 넣을 수도 있으며,

```python
def return_true():
    return True
def return_false():
    return False

if return_true():
    print("checked_1")
if return_false():
    print("checked_2")
```

```python
# 출력 결과
checked_1
```

return type이 `bool`인 function도 넣을 수 있습니다.

## else

else에는 특별한 condition을 가지고 실행할지 말지를 정하지 않습니다. 해당 구문은 `if`문 당 하나의 else 구문만 가질 수 있으며, `if` 문에서 실행되지 않는다면 `else`구문을 실행합니다.

```python
if <condition>:
	pass
else:
    pass
```

위와 같은 구문을 사용하면, 만약 condition이 binary한 결과를 가지는 상황에서 사용하면 좀 더 간결하게 쓸 수 있습니다.

```python
def is_even(num):
    if num % 2 == 0:
        return "yes"
    else:
        return "no"
print(is_even(7))
```

```python
# 출력 결과
no
```

사실 간결하게 쓸 수 있다는 표현보다 `if-else`는 한 묶음으로 동작한다고 보시면 됩니다. 즉 둘 중에 하나만 실행됩니다. 

> Tip👀
>
> 위의 예시를 단순히 `if`문 두 번으로도 구현할 수 있습니다. 그러나, `if`문을 두 번 나누어 쓰게 되는 경우, `interpreter`는 `if`문의 각 condition들을 전부 확인하게 됩니다. (해당 condition이 `True`인지 `False`인지) 
>
> 그렇기 때문에 binary condition에서는 if-else 구문을 활용하시는 편이 좋습니다.

## if-elif-else

**el**se **if** 의 약자로서 조건문이 binary한 경우로 나뉘어 지지 않는다면 주로 사용하는 구문입니다.

```python
def season(month):
    if month >= 3 and month <= 5:
        return "spring"
    elif month >= 6 and month <= 8:
        return "summer"
    elif month >= 9 and month <= 11:
        return "autumn"
    else:
        return "winter"
        
print(season(12))
```

```python
# 출력 결과
winter
```

여기서도 else를 보면 `if`와 `elif`의 조건에 들어가지 않는 나머지 경우(12,1,2)에 한하여 해당 구문을 실행하게 됩니다.

---

[Back - Control flow](./Control-flow.md)

