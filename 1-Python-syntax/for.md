# for

Python은 2가지 형태의 반복문을 지원합니다. 그 중 한가지가 바로 `for`문입니다. 주로, **정해진 반복 횟수**가 있을 때 사용됩니다.

```python
for <parameter> in <iterable>:
    pass
```

`<iterable>`에는 **순차적으로 접근 가능한 자료형**이라면 전부 대입가능합니다. 순차적으로 하나의 요소(element)에 접근했다면, 해당 요소를 `<parameter>`에 저장하게 됩니다. 

```python
for i in range(3):
    print(i)
```

```python
# 출력 결과
0
1
2
```

`<parameter>`가 꼭 하나일 필요는 없습니다. `<iterable>`의 한 element가 여러개의 data들로 packing 되어 있다면, unpacking을 통해 여러 `<parameter>`에 할당할 수 있습니다.

```python
collection = [("A",12),("B",8),("C",23)]
for name, age in collection:
    print(name, age)
```

```python
# 출력 결과
A 12
B 8
C 23
```

> Tip👀
>
> Python에서 지원하는 built-in function이 있습니다. 다음의 예시를 통해 어떠한 것들이 어떻게 이용되는지 알아봅시다.(`[]`안의 parameter은 생략 가능하다는 의미이며 `=`은 생략했을 시 할당 되는 값을 나타내기 위함입니다.)
>
> 1. enumerate(iterable[, start = 0])
>
> ```python
> data = ['a','b','c']
> for i, val in enumerate(data):
>     print(i,val)
> ```
>
> ```python
> # 출력 결과
> 0 a
> 1 b
> 2 c
> ```
>
> `enumerate`는 start부터 시작하는 숫자를 차례로 각 element와 매칭시키는 역할을 합니다. start가 0부터 시작한다면 값(val)와 index를 동시에 출력을 할 수 있습니다. 여기서 마찬가지로 `iterable`은 순차적으로 접근 가능하여야 합니다.
>
> 2. zip(*iterables)
>
> `*`은 [`unpacking`](./Tuples.md#unpacking)에서 다루었지만 간단히 언급만 하자면 parameter 개수에 상관없이 여러개 받을 수 있다는 의미입니다.
>
> ```python
> names = ['A','B','C']
> ages = [12,8,23]
> sexs = ['male','female','male']
> for name,age,sex in zip(names,ages,sexs):
>     print(name, age, sex)
> ```
>
> ```python
> # 출력 결과
> A 12 male
> B 8 female
> C 23 male
> ```
> `zip`은 예시와 같이, 길이가 같은 `iterables`끼리 묶어주는 역할을 합니다. 

## continue/break 

loop문을 효율적으로 다룰 수 있는 두가지 keywords가 있습니다. 바로 continue와 break인데요. 이는 주로 `if`문과 함께 사용됩니다.

### continue

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

```python
# 출력 결과
0
1
3
4
```

continue를 만나면 해당 keyword 아래 구문들은 실행하지 않고 다음 반복으로 넘어갑니다.

### break

```python
for i in range(5):
    if i == 2:
        break
    print(i)
```

```python
# 출력 결과
0
1
```

break를 만나면 loop문을 빠져나오게 됩니다. 

---

[Back - Control flow](./Control-flow.md)