# Built-in Data structure

`Data structure`이라는 것은 무엇일까요? 먼저 데이터 하나를 저장하려면 어떻게 하면 됐었는지 떠올려 봅시다.([Variables](./Variables.md)에도 나와있습니다!)

```python
a = 3
```

딱히 구조라고 할 것이 없습니다. 관리할 데이터가 하나밖에 없으니까요. 그렇다면 데이터 여러개를 하나의 변수에 담아 두려면 어떻게 해야할까요?

```python
a = [1,2,3] # list
b = (1,2,3) # tuple
c = {"first" : 1, "second" : 2, "third" : 3} # dictionary
d = {1, 2, 3} # set
```

담는 방식이 각각 다르다는 것을 볼 수 있습니다. 이는 각 `Data structure`들이 다른 구조를 가지고 있기 때문인데요. 이들의 구조를 한 문서 안에서 다루는 것은 힘들기 때문에 따로 보도록 하죠.

- [`Lists`](./Lists.md)
- [`Tuples`](./Tuples.md)
- [`Sets`](./Sets.md)
- [`Dictionaries`](./Dictionaries.md)

## Type convention(Typecasting)

위의 문서들을 전부 읽어 오셨으리라 생각하고 어떻게 서로간에 형변환이 가능한지 알아보도록 하겠습니다.

### Lists ↔ Tuples

이들 둘의 차이는 `Data structure`에 들어있는 data을 바꿀 수 있느냐의 차이밖에 없습니다. 그렇기 때문에 이 둘간의 Typecasting은 비교적 간단합니다.

```python
list_to_tuple = tuple([1,2,3]) # list to tuple
tuple_to_list = list((1,2,3)) # tuple to list
print("list_to_tuple")
print("type:", type(list_to_tuple), "content:", list_to_tuple)
print("tuple_to_list")
print("type:", type(tuple_to_list), "content:", tuple_to_list)
```

```python
# 출력 결과
list_to_tuple
type: <class 'tuple'> content: (1,2,3)
tuple_to_list
type: <class 'list'> content: [1,2,3]
```

### Lists ↔ Sets

`set` 의 경우 중복을 허용하지 않습니다! 그렇기 때문에 `list`에서 `set`로 형변환 시킬때, 정보의 손실이 일어 날 수 있습니다.

```python
set_to_list = list({1,2,3})
list_to_set = set([1,2,3,3]) # 3 이 중복된다
print("set_to_list")
print("type:", type(set_to_list), "content:", set_to_list)
print("list_to_set")
print("type:", type(list_to_set), "content:", list_to_set)
```

```python
# 출력 결과
set_to_list
type: <class 'list'> content: [1,2,3] # 순서는 바뀔 수 있다
list_to_set
type: <class 'set'> content: {1,2,3} # 중복된 3이 하나로 줄어들었다
```

### Tuple ↔ Sets

`list`와 동일하게, `tuple`에서 `set`으로 변환될 때, 정보의 손실이 일어날 수 있습니다.

```python
set_to_tuple = tuple({1,2,3})
tuple_to_set = set((1,2,3,3)) # 3 이 중복된다
print("set_to_tuple")
print("type:", type(set_to_tuple), "content:", set_to_tuple)
print("tuple_to_set")
print("type:", type(tuple_to_set), "content:", tuple_to_set)
```

```python
# 출력 결과
set_to_tuple
type: <class 'tuple'> content: (1,2,3)
tuple_to_set
type: <class 'set'> content: {1,2,3} # 중복된 3이 하나로 줄어들었다
```

---

### Dictionaries ↔ Lists

여기서 부터는 조금 다릅니다. `dict`의 핵심 구조라고 할 수 있는 `key`와 `value`때문에 서로간의 형변환에 차이가 있습니다.

```python
dict_to_list = list({'a' : 1, 'b' : 2, 'c' : 3}) 
list_to_dict = dict([('a', 1), ['b', 2], {'c', 3}])
print("dict_to_list")
print("type:", type(dict_to_list), "content:", dict_to_list)
print("list_to_dict")
print("type:", type(list_to_dict), "content:", list_to_dict)
```

```python
# 출력 결과
dict_to_list
type: <class 'list'> content: ['a', 'b', 'c'] # key 값들만 저장 되었다.
list_to_dict
type: <class 'dict'> content: {'a' : 1, 'b' : 2, 3 : 'c'} # set은 순서가 바뀔 수 있다
```

`dict`에서 `list`로 바꿀때 정보의 손실이 일어나게 됩니다. 예시에서 볼 수 있듯이, **`dict`에서 `key`에 해당하는 값만 `list`로 저장되고 `value`는 저장되지 않았음을 확인 할 수 있습니다.**

`list`에서 `dict`로 형변환이 일어날때는 `dict`에 필요한 `key`와 `value`을 알아볼 수 있게 감싸주어야 합니다. 그렇기 때문에 `key`에 매칭되는 값 하나, `value`에 매칭되는 값 하나로 총 두 개의 elements로 이루어진 data structure이어야 합니다. 

> Tip👀
>
> `set`으로 감싸진 element(`{'c' , 3}`)의 경우 순서가 없기 때문에 자신이 원하는 `key`와 `value`값 대로 저장되지 않을 수 있습니다. 그럴 수 있다는 것만 알아두시고 그렇게 쓰는 일은 없도록 합시다.

### Dictionaries ↔ Tuples

`list`와 `tuple`은 구조적인 차이가 없어 "[]"을 "()"로 바꾸어도 똑같이 작동합니다.

```python
dict_to_tuple = tuple({'a' : 1, 'b' : 2, 'c' : 3})
tuple_to_dict = dict((('a', 1), ['b', 2], {'c', 3}))
print("dict_to_list")
print("type:", type(dict_to_tuple), "content:", dict_to_tuple)
print("tuple_to_dict")
print("type:", type(tuple_to_dict), "content:", tuple_to_dict)
```

```python
# 출력 결과
dict_to_tuple
type: <class 'tuple'> content: ('a', 'b', 'c')
list_to_dict
type: <class 'dict'> content: {'a' : 1, 'b' : 2, 'c' : 3} # set은 순서가 바뀔 수 있다
```

### Dictionaries ↔ Sets

`set`에는 `tuple`과 `list`와 달리 elements간에 우선순위(순서)가 없기 때문에 결과가 다르게 나올 수 있습니다.

```python
dict_to_set = set({'a' : 1, 'b' : 2, 'c' : 3})
set_to_dict = dict({('a', 1), ('b', 2), ('c', 3)}) # mutable한 값은 set에 담지 못한다.
print("dict_to_set")
print("type:", type(dict_to_set), "content:", dict_to_set)
print("set_to_dict")
print("type:", type(set_to_dict), "content:", set_to_dict)
```

```python
# 출력 결과
dict_to_set
type: <class 'set'> content: {'b', 'c', 'a'} # 순서가 없어 출력 결과가 다를 수 있다.
set_to_dict
type: <class 'dict'> content: {'a' : 1, 'c' : 3, 'b' : 2} # 순서가 없어 출력 결과가 다를 수 있다.
```

이렇게 하여 python이 제공하는 대부분의 data structure들의 개념 및 conversion에 대해 배웠습니다. 다음에는 본격적인 코딩을 위한 Control flow에 대해 알아 보도록 하겠습니다.

---

[Next-Control flow](./Control-flow.md)