# while

python에서 지원하는 2가지 loop문중 한가지인 `while`문입니다. 주로 **정해진 반복 횟수가 없을 때 ** 주로 사용됩니다.

```python
while <condition>:
    pass
```

`<condition>`의 부분에는 결과값이 `bool`이라면 **어떠한 것**이라도 대입가능합니다.

```python
i = 0
while i < 3:
    print(i)
    i += 1
```

```python
# 출력 결과
0
1
2
```

위의 예시처럼 `<condition>`값이 `True`일때만 반복문을 실행하며, `False`가 반환되면 반복문이 끝나는 것을 확인할 수 있습니다.

```python
def run(i):
    return i < 10

i = 0
while run(i):
    print(i)
    i += 3
```

```python
# 출력 결과
0
3
6
9
```

return 값이 `bool`이라면 함수도 `<condition>`에 담을 수 있습니다.

## nested while loop

`while`을 이용하여 구구단을 출력하는 프로그램을 만들어 봅시다. `for`문이 가능했던 것 처럼 `while`문 또한 이중으로 사용할 수 있습니다.

```python
i, j = 1, 1
while i < 10:
    while j < 10:
        print(i*j)
```

어떠한 `while`문과 `for`문이든 서로 똑같은 일을 수행하는 반복문으로 만들 수 있습니다. 다만, 편의성을 위해 두가지 `loop`문을 만들었다고 볼 수 있습니다. 

## continue/break

`while`문도 반복문이기 때문에 continue와 break를 사용하면 효율적으로 사용할 수 있습니다.

```python
def must_stop():
    return True

while True:
    if must_stop():
        break
```

다음의 예시를 보면 `while`문의 `<condition>`에 `True`이 들어가면 해당 반복문은 무한 반복문이 됩니다. 이러한 반복문을 빠져나오기 위해서는 다음과 같이 if문과 break의 조합으로 빠져나올 수 있습니다.

```python
i = 0
while i < 4:
    if i == 2:
        continue
    print(i)
    i += 1
```

```python
# 출력 결과
0
1
3
```

`continue`를 사용하면 다음과 같이 keyword를 기점으로 아래 코드는 실행되지 않으면서 다음 반복으로 넘어가는 것을 알 수 있습니다.

---

[Back - Control flow](./Control-flow.md)