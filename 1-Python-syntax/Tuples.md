## Tuples

`tuple`은 `list`와 구조적인 측면에선 거의 차이가 없습니다. 다음과 같은 특성은 `tuple`에서도 그대로 적용됩니다.

- Tuples' elements can take any types
- Tuples have order itself
- Tuples allow duplicate elements
- Tuples are iterable

```python
data = (1, "banana", False) # Tuples' elements can take any types
print(data[-2])    # Tuples have order itself
print(data[1:])    
data = (1,1,1,1)    # Tuples allow duplicate elements
for i in data:    # Tuples are iterable
    print(i)
```

```python
# 출력 결과
banana
(banana, False)
1
1
1
1
```

그렇다면 다른 점은 무엇일까요?

## Tuples' elements are *unchangeable*

`tuple`에 있는 element들은 변하지 못하도록 되어있습니다. 

```python
data = (1,2,3)
data[0] = 100
```

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

위와 같은 에러가 뜨게 됩니다. 

> Tip👀
>
>`tuple`을 선언할 때 `()`을 생략해도 됩니다.
>
>```python
>data = 1,2,3
>print(type(data))
>```
>
>```python
># 출력 결과
><class 'tuple'>
>```

> Tip👀
>
> `tuple`에 값을 하나만 넣고 싶다면 다음과 같이 마지막에 `,`을 꼭 붙여 줘야 합니다.
>
> ```python
> data = 1, # 또는 (1,)
> ```

## packing/unpacking

[Variable-Assign values to multiple variables](./Variables.md#Assign-values-to-multiple-variables)에서 잠깐 언급 되었습니다. 예시를 통해 각각이 무엇인지 알아보도록 합시다.

### packing

```python
data = 1,2,3
```

사실 다른 것은 없고 한 variable내에 여러 data를 담을 때를 packing이라고 보시면 됩니다. 그렇게 치면 `list`도 한 variable내에 여러 data를 담으니 packing이라고 볼 수 있겠습니다.

### unpacking

```python
x, y, z = data
```

unpacking은 packing된 variable을 풀어서 여러값으로 전달할 때를 unpacking이라 할 수 있습니다. `list`도 packing, upacking을 지원합니다. 

> Tip👀
>
> packing과 unpacking은 주로 parameter를 주고 받을 때 자주 쓰입니다.
>
> ```python
> def print_all(*args):
>     print(args)
>         
> print_all(1)
> print_all(1,2) 
> print_all(1,2,3)
> ```
>
> ```python
> # 출력 결과
> (1,)
> (1,2)
> (1,2,3)
> ```
>
> 위에서 `*`는 args 라는 parameter는 packing되는 것이라는 것을 미리 컴퓨터에게 알려주는 용도로 보시면 되겠습니다. 원래 parameter 개수와 입력 받는 parameter 개수는 같아야 하지만 packing을 사용하면 입력 받는 parameter 개수를 자유롭게 관리 할 수 있습니다.

## Tuples' methods and keyword

`tuple`에도 `list`와 같이 `tuple`을 위한 methods, keywords가 있습니다. element를 변화 시키지 못하니 지원하는 게 많지는 않습니다.

| methods/keyword | description                       | example       |
| --------------- | --------------------------------- | ------------- |
| `del`           | Delete the tuple                  | del data      |
| `+`             | Join two or more tuples           | data1 + data2 |
| `count(x)`      | Return how many `x`s are in tuple | data.count(x) |
| `index(x)`      | Same as data[x]                   | data.index(x) |

---

[Back-Built-in Data structure](./Built-in-Data-structure.md)