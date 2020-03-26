# Sets

`set`은 여러분들이 알고있는 집합과 동일하다고 보시면 됩니다. 다음의 특징을 살펴보도록 하죠.

- [Sets cannot have duplicate elements](#Sets-cannot-have-duplicate-elements)
- [Sets are unordered collection(data structure)](#Sets-are-unordered-collection(data-structure))
- [Sets are mutable](#Sets-are-mutable)
- [Sets cannot have mutable elements](#Sets-cannot-have-mutable-elements)
- [Sets are iterable](#Sets-are-iterable)
- [Sets' keywords and methods](#Sets'-keywords-and-methods)

## Sets cannot have duplicate elements

`set`은 수학에서 배웠던 것과 마찬가지로 중복된 element들을 허용하지 않습니다.

```python
data = {1,2,2,3}
print(data)
```

```python
# 출력 결과
{1,2,3}
```

위와 같이, `set`은 `{}`에 담고싶은 element를 넣어서 선언하게 됩니다. 그렇다면 수학에서 쓰이는 개념인 공집합(empty set)은 어떻게 선언할 수 있을까요?

```python
data = {}
```

상식선에선 이렇게 선언하는게 자연스럽지만, `dict`과 표현이 겹치기 때문에 다음과 같이 선언해야만 합니다.

```python
data = set()
```

## Sets are unordered collection(data structure)

set은 순서를 가질 수 없도록 구현되었기 때문에 다음과 같이 `[]`과 같은 `subscript operator`로 접근하지 못합니다.

```python
data = {1,2,3}
print(data[0])
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'set' object is not subscriptable
```

## Sets are mutable

`set` 또한 mutable한 성질을 지닙니다. mutable에 대한 성질을 [`Lists - Lists' are mutable`](./Lists.md#Lists'-are-mutabled)에서 확인 할 수 있습니다. `set`에도 물론 `copy()`을 지원합니다.

## Sets cannot have mutable elements

`set`은 mutable한 element를 담지 못합니다. `set`에 담긴 element들은 서로 달라야합니다. 즉 unique한 값을 지녀야합니다. 이러한 와중에 mutable한 `list`, `set`, `dict`이 `set`의 elements로 존재하다가 값이 변하여 우연히 다른 elements와 중복되면 안되겠죠?

## Sets are iterable

`set`은 순차적으로 접근이 가능합니다. 이 말이 헷갈리실 수 있을 것이라 됩니다만 다음의 예시를 보고 이해해보도록 합시다.

```python
data = {"apple","banana","cherry"}
for i in data:
    print(i)
```

```python
# 출력 결과
apple
cherry
banana
```

실제로 `for`문으로 순차적으로 `i`에 담겨 출력되는 것을 확인 할 수 있었지만 순서대로 나오는 것이 아니라 아무렇게 출력되는 것을 알 수 있습니다. 

## Sets' keywords and methods

`set`에서 지원하는 keywords와 methods(functions)가 있습니다. 아무래도 수학적인 개념이다 보니 당연히 수학적 연산을 지원합니다. 또한 추가,제거 등의 연산들도 지원합니다. `set`에서 지원하는 keywords 와 methods가 많기 때문에 하나하나 예시를 다루진 않겠습니다.

| Keywords/Methods                | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| `in`                            | Return True if the left operand is in the set(right operand) |
| `|`                             | Return the union of left operand and right operand           |
| `&`                             | Return the intersection of lefte operand and right operand   |
| `-`                             | Return the difference that are only in left operand not in right operand |
| `^`                             | Return the Symmetric difference that same as `A|B - A&B`     |
| `add()`                         | Add an element to the set                                    |
| `clear()`                       | Remove all elements from the set                             |
| `copy()`                        | Return a copy of the set                                     |
| `difference()`                  | Return the difference of two or more sets as a new set       |
| `difference_update()`           | Remove all elements of another set from this set             |
| `discard()`                     | Remove an element from the set if it is a member. (Do nothing if the element is not in set) |
| `intersection()`                | Returns the intersection of two sets as a new set            |
| `intersection_update()`         | Updates the set with the intersection of itself and another  |
| `isdisjoint()`                  | Returns `True` if two sets have a null intersection          |
| `issubset()`                    | Returns `True` if another set contains this set              |
| `issuperset()`                  | Returns `True` if this set contains another set              |
| `pop()`                         | Removes and returns an arbitary set element. Raise `KeyError` if the set is empty |
| `remove()`                      | Removes an element from the set. If the element is not a member, raise a `KeyError` |
| `symmetric_difference()`        | Returns the symmetric difference of two sets as a new set    |
| `symmetric_difference_update()` | Updates a set with the symmetric difference of itself and another |
| `union()`                       | Returns the union of sets in a new set                       |
| `update()`                      | Updates the set with the union of itself and others          |

---

[Back-Built-in Data structure](./Built-in-Data-structure.md)