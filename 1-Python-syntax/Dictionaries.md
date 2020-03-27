# Dictionaries

`dict`에서 가장 두드러진 구조라고 할 수 있는 것은 `key`와 `value`가 쌍으로 있어야한다는 점이라고 볼 수 있습니다. 여태 배운 것을 기준으로 말씀 드리면 `list`는 `index`가 `int`이지만 `dict`의 `index`는 `key`라고 말씀드릴 수 있겠네요. 다음의 특징들을 통해 좀 더 자세히 알아 보도록 하겠습니다.

- [Dictionaries are unordered collection of key-value pairs](#Dictionaries-are-unordered-collection-of-key-value-pairs)

## Dictionaries are unordered collection of key-value pairs

`dict`은 `set`과 마찬가지로 순서를 가지지 않습니다. 순서를 가지지 않는다는 말은 [Lists - Lists are ordered collection](./Lists.md#Lists-are-ordered-collection)에서 [`start`:`end`:`step`]과 같이 처음과 끝, 간격만으로 원하는 element를 들고 오지 못한다는 말입니다.

그렇다면 다음의 예시를 통해 통해 key,value가 각각 무엇인지 살펴보도록 합시다.

```python
data = {'a':1, 'b':2, 'c':3}
```

'a','b','c'를 `key`라고 하고 1,2,3을 `value`라고 합니다. 그 사이에 있는 `:`은 key와 value를 구분하는 구분자로 불립니다. `key`와 `value`는 항상 쌍으로 존재해야하며 둘 중에 하나만 존재하는 일은 없습니다.

### keys should be unique

`dict`의 `key`는 유일해야합니다. 그도 당연할 것이 `key`자체가 `dict`의 `index`가 되어야하기 때문입니다. 그렇게 때문에 mutable한 data type은 `key`가 될 수 없습니다.

```python
data = {[1,2,3]:6}
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

```python
data = {"apple":1, "cherry":2, "cherry":3 }
print(data)
```

```python
# 출력 결과
{"apple":1, "cherry":3 }
```

만약 중복되는 key가 있다고 하면 나중에 선언된 key와 value를 저장하게 됩니다.

### values can have any types

반대로 `value`에는 어떠한 type이 와도 상관없습니다. 단순하게 값만 저장을 해도 되고,  다른 collection을 담을 수도 있습니다.

```python
data = {"lang":["python","C/C++"], "level":{"python":"beginner", "C/C++":"immediate"}}
print(data["level"]["python"])
```

```python
# 출력 결과
'beginner'
```

## Dictionaries are mutable

`dict`도 `list`, `set`과 동일하게 mutable합니다. 그렇다고 해서 `key`를 바꿀 수 있는 것은 아닙니다. 

```python
data = {'a':1}
data['b'] = 2 # dict 은 다음과 같이 key와 value를 쌍으로 추가 할 수 있습니다.
data1 = data
data1['b'] = 100
print(data)
```

```python
# 출력 결과
{'a':1, 'b':100}
```

`dict`에서도 `copy()`를 지원합니다.

```python
data = {'a':1}
data['b'] = 2 # dict 은 다음과 같이 key와 value를 쌍으로 추가 할 수 있습니다.
data1 = data.copy()
data1['b'] = 100
print(data)
print(data1)
```

```python
# 출력 결과
{'a':1, 'b':2}
{'a':1, 'b':100}
```

## Dictionaries are iterable

`dict`또한 순차적으로 접근이 가능합니다. 하지만 `dict`의 `key`값만 순차적으로 접근하게됩니다. 

```python
data = {'a':1, 'b':2, 'c':3}
for i in data:
    print(i)
```

```python
# 출력 결과
a
b
c
```

이와 같은 문제에 대한 해결하기 위해서는 [Built-in Data structure - Dictionaries ↔ Lists](./Built-in-Data-structure.md#Dictionaries-↔-Lists)에서 배운, `dict`을 `list`로 형변환 시킬 수 있는 methods를 이용하면 됩니다.

```python
data = {'a':1, 'b':2, 'c':3}
for i in data.keys():
    print(i,end=" ")
print("")
for i in data.values():
    print(i, end=" ")
```

```python
# 출력 결과
a b c
1 2 3
```

`items()`의 경우는 조금 다릅니다. [Tuples - paking/unpacking](./Tuples.md#packing/unpacking)을 알고계셔야 이해가 갈 것입니다.

```python
for k, v in data.items():
    print(k, v)
```

```python
# 출력 결과
a 1
b 2
c 3
```

`items()`가 반환되는 구조를 보면 한 element당 (key, value)로 packing된 상태로 `list`를 반환합니다. 그렇기 때문에 이를 k와 v로 unpacking하여서 사용하셔야 각각 따로 쓸 수 있습니다.

## Dictionaries' keywords and methods

종류가 많기 때문에 예시들을 전부들 순 없습니다만 필요할 때마다 검색을 통해 사용법을 학습할 수 있습니다.

| Keywords/Methods | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| `in`             | Return `True` if the dict's `key`s contains left operand     |
| `clear()`        | Remove all the elements from the dictionary                  |
| `copy()`         | Return a copy of the dictionary                              |
| `fromkeys()`     | Return a dictionary with the specified keys and value        |
| `get()`          | same as indexing with `[]`                                   |
| `items()`        | Return `list` of the keys-values from `dict`                 |
| `keys()`         | Return `list` of the keys from `dict`                        |
| `pop()`          | Remove the element with the specified key                    |
| `popitem()`      | Remove the last inserted key-value pair                      |
| `setdefault()`   | Return the value of the specified key. If the key does not exist: insert the key, with the specified value |
| `update()`       | Update the dictionary with the specified key-value pairs     |
| `values()`       | Return `list` of the values from `dict`                      |

---

[Back-Built-in Data structure](./Built-in-Data-structure.md)