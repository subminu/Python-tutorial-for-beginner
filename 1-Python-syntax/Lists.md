# Lists

`list`는 여러개의 데이터들을 하나로 모아주는 `data structures`중 하나입니다.  이 `list`에는 어떠한 특성이 있는지 알아보죠.

- [Lists' elements can take any types](#Lists'-elements-can-take-any-types)
- [Lists have order itself](#Lists-have-order-itself)
- [Lists' elements are changeable](#Lists'-elements-are-changeable)
- [Lists allow duplicate elements](#Lists-allow-duplicate-elements)
- [Lists are iterable](#Lists-are-iterable)
- [Lists are mutable](#Lists-are-mutable)

특성 이외에 `list`에서 지원하는 몇가지 기능들이 있습니다.

- [Lists' method and operators](#Lists'-method-and-operators)

## Lists' elements can take any types

먼저, 어떻게 `list`로 변수에 담을 수 있을지 살펴봅시다. 이미 여러분들은 꽤 보셨을 것입니다.

```python
data = [1, "two", True]
print(data)
```

```python
# 출력 결과
[1, 'two', True]
```

여기서 잠깐 보자면, `list`안에 한 요소인 element에는 어떠한 type이어도 됩니다. 보시는 바와 같이 `int`, `str`, `bool` 의 자료형이 정상적으로 리스트에 담겨지고 출력되는 것을 볼 수 있습니다.

> Tip👀
>
> `list`의 element에는 무슨 type이든지 담을 수 있습니다. `list`안에 `list`가 있을 수도 있고, 다른 `data structure`들도 들어갈 수 있습니다! 좀 더 자세한 예시를 보고 싶으시다면 [Bulit-in Data structure](./Built-in-Data-structure.md)의 예시를 참고해 주세요!

## Lists have order itself

`list`에는 순서가 있기 때문에 다음과 같이 `[]`와 같은 `subscipt operator`를 이용하여 원하는 element에 접근할 수 있습니다. 또한 `[]`에 들어가는 **정수**를 `index`라고 합니다.(실수는 안됩니다.)

```python
data = [0,1,2,3,4,5,6,7,8,9,10]
print(data[0])
print(data[-1])
print(data[-11])
```

```python
# 출력 결과
0
10
0
```

음수를 넣게 되면, -1이 마지막 element인 10에서 mapping 되길 시작으로, -11는 0까지 mapping 되게 됩니다. 또한 순서가 있기 때문에 다음과 같은 일도 할 수 있습니다.

```python
data = [0,1,2,3,4,5,6,7,8,9,10]
print(data[0:11:2])
```

```python
# 출력 결과
[0,2,4,6,8,10]
```

[ `start = 0` : `end = list_size` : `step = 1` ]

`start` 번째 부터 `end`-1 번째까지 `step` 간격으로 새롭게 list를 만들어 줍니다. 각각은 생략 가능합니다. 각각을 생략하게 되면 `start`는 처음 부터, `end`는 마지막 element까지, `step`은 한 개씩 가져오게 되는겁니다.

각각에 음수도 넣을 수 있습니다. 음수를 쓰게 되면 다음과 같이 거꾸로 출력도 가능합니다.

```python
print(data[-1:-12:-2])
```

```python
# 출력 결과
[10, 8, 6, 4, 2, 0]
```

### range()

`list`를 사용할때, 단순히 순서대로 나열된 정수들을 만들어야 할 때가 많습니다. (for문을 사용할 때 특히 자주 사용할 것입니다. 지금은 for 문을 몰라도 됩니다.) 예를 들어 봅시다.

```python
data = [0,1,2, ..., 99] # 실행되지 않습니다! "..." 이란 구문은 list에서 지원하지 않아요!
```

위는 0부터 99까지 순서대로 나열된 정수를 `list`로 담은 모습입니다. 실제로 실행되진 않습니다. `list`에는 `...`이라는 말을 이해하지 못합니다. 이처럼 단순한 `list`를 편하게 만들때 필요한 것이 `range()`입니다.

```python
data = range(100)
print(data)
print(type(data))
```

```python
# 출력 결과
range(0,100)
<class, 'range'>
```

0부터 100까지 순서대로 나열된 정수를 순차적으로 접근할 수 있는 `range` type으로 나오게 됩니다.

> Tip👀
>
> 왜  `list`가 아니라 `range`라는 type으로 반환이 되나요?  
>
> 이는 매우 심화 내용으로 읽고 싶으신 분만 읽으시면 됩니다. 처음 python을 접하시는 분들은 나중에 [for](./for.md)에서 어떻게 사용되는지만 확인하시면 됩니다.
>
> 어떤 변수나 객체를 선언할 때, 해당 값들이 memory 어딘가에 저장되어야만 사용할 수 있습니다. 그러한 면에서 range(10**10)이란 큰 숫자가 [0,1,...,10\*\*10]까지 한꺼번에 memory에 저장한다고 생각해 보세요. 
>
> 그렇게 된다면 많은 양의 data가 memory에 담기게 될 것입니다.  만약 memory가 저장해야할 data 보다 부족하면 프로그램은 정상적으로 실행 될 수가 없겠죠? 많은 양의 data를 저장할 수 있는 용량이 되더라도 느릴 수 있다는 단점이 생깁니다. 
>
> 이러한 점을 보완하기 위해 직접 필요하다고 요구될때 까지 계산되지 않는 `lazy sequence(range)` 를 반환합니다. 여기서 `lazy sequence`는 순차적으로 접근 할 수 있지만 직접 요구 될 때까지 계산되지 않는 성질을 가진 `sequence`라 보시면 됩니다.(한꺼번에 memory에 저장하는 것이 아니라 필요할 때 꺼내서 사용한다는 소립니다.)
>
> ```python
> data = range(100)
> print(data[50])
> ```
>
> ```python
> # 출력 결과
> 49 # 0부터 시작하니까 50 - 1인 49가 나옵니다.
> ```
>
> 위의 예시에서 data에는 바로 [0, ... ,99]를 data에 저장하지 않습니다. 그냥 range라는 data type의 값으로 저장이 됩니다. 직접 요구 되는 `data[50]`를 명령했을 때, 그제서야 50번째의 숫자를 계산하기 시작합니다.
>
> 이와 비슷한 이야기를 전에도 하였습니다. `lazy evaluation`을 아시나요? [Operators-Logical operators](./Operators.md#Logical-operators)에서 다뤘었던 내용입니다. `and`와 `or`연산자에서 첫 번째 operand에서 이미 결과값이 결정 될때, 굳이 두 번째 operand의 값은 계산하지 않았습니다. 그것처럼 `lazy sequence` 도 필요할때만 계산되고 나머지의 경우 `range`라는 data type로 남아 있는 것입니다.
>
> 여기까지 읽으셨으면 대단하신 분이십니다. 실제로 어떻게 구현되는지는 memory의 구조,  pointer, iterator에 대한 기본적인 지식이 필요합니다. 이를 python에서 배우는 것은 비효율적일 뿐더러 기초에서 벗어나는 것이라 생각됩니다. 

```python
for i in range(5,10,2):
    print(i)
```

```python
# 출력 결과
5
7
9
```

range( `start`, `end`, `step ` )

range에도 `start`부터 `end-1`까지 `step`으로 좀 더 간편하게 원하는 `list(lazy sequence)`를 만들 수 있습니다. 좀 더 다양한 예시는 [for](./for.md)에서 다루도록 하겠습니다.

## Lists' elements are changeable

`list`안의 element들은 처음 선언한 뒤에도 값이 바뀔 수 있습니다.

```python
data = [0,1,2,3,4]
data[2] = "two"
print(data)
```

```python
# 출력 결과
[0,1,'two',3,4]
```

## Lists allow duplicate elements

`list`의 element는 중복 될 수 있습니다.

```python
data = [1,1,1,1]
print(data)
```

```python
# 출력 결과
[1,1,1,1]
```

## Lists are iterable

for 문에서 다뤄지면 좋은 소재이지만 `list`의 특성이기 때문에 다루도록 하겠습니다. for문에 대해 모르시더라도 직관적으로 이해할 수 있으니까 걱정하지 않아도 됩니다.

```python
for i in ["you","me","him","her"]:
    print(i)
```

```python
# 출력 결과
you
me
him
her
```

`iterable`이라는 것은 **순차적으로 접근할 수 있는** 성질입니다. for문을 잘 모르지만 "you"부터 차례대로 하나하나씩 출력된 것을 볼 수 있습니다. (사실 for문의 전부 이긴 합니다..)

## Lists are mutable

아직 [Function](./Function.md)에 대해 배운게 없으신 분은 읽지 않는 것을 추천드립니다. 이 부분은 적어도 scope에 대해 알아야 이해가 가능한 부분입니다. 일단 예시를 mutable이란 특성은 이 무엇인지 알아 보도록 하겠습니다.

### Lists can be changed regardless of scope

```python
def change_var(a):
    var = a
def change_data(a):
    data[0] = a
```

위와 같이 함수를 정의하였다고 해보죠.

```python
data = [1,2,3]
var = 4
```

그리고 위같이 변수를 정했다고 칩시다.

```python
change_var(100)
change_data(100)
print(var)
print(data)
```

위와 같은 명령문을 통해 얻을 수 있는 예상 출력 결과는 함수가 어떻게 정의 되었든 상관없이, Scope에 의해 아무런 영향을 받지 않을 것입니다. 출력 결과를 보도록 하죠.

```python
# 출력 결과
4
[100,2,3]
```

예상이랑 결과가 다릅니다! data type이 `int`인 경우는 그대로 값을 가지지만 `list`의 경우는 첫번째 값이 함수 내에서 할당된 값인 100으로 바뀌어져 있습니다. 이처럼 scope와 관계없이 변할 수 있는 성질을 mutable이라고 합니다.

### Lists can be changed by copied lists

왜 이렇게 되는지 이해를 하기위해서는 적어도 [Classes/Objects](./Class/Objects.md)를 알아야합니다. 지금은 아 그렇구나 하고 넘어가시는 것을 추천합니다.

```python
origin = 1
copied = origin
print(copied)
```

```python
# 출력 결과
1
```

다음과 같이 "origin"에 1을 할당하고, "copied"에 "origin"을 할당시키면 다음과 같이 "origin"안에 있던 1이 복제 되었다는 것을 알 수 있습니다. 이 상태에서 "copied"에 담긴 1을 2로 바꾼 후, "origin"값이 바뀌었는지 확인해 보겠습니다.

```python
copied = 2
print(copied)
print(origin)
```

```
# 출력 결과
2
1
```

"copied"가 2로 바뀌었음에도 불구하고 "origin"의 값은 변하지 않았습니다. 다음은 `list`을 보도록 해봅시다.

```python
origin = [1,2,3]
copied = origin
print(copied)
```

```python
# 출력 결과
[1,2,3]
```

정상적으로 복제되었음을 확인 할 수 있습니다. 다음 단계로 넘어가 보도록 하죠.

```python
copied[2] = 100
print(copied)
print(origin)
```

```python
# 출력 결과
[1,2,100]
[1,2,100]
```

복제된 "copied"의 값을 변형시켰는데 "origin"값 또한 "copied"와 동일하게 바뀌었습니다. 이처럼 복제된 `list`에 의해 본래 `list`의 값이 변하는 성질을 mutable이라고 합니다.

> Tip👀
>
> 우리가 원하는 것은 저렇게 둘 다 변하는게 아니라 "copied"의 element만 변하게 하고 싶습니다. 그러한 경우를 위해 python에서는 다음의 명령어를 지원합니다.
>
> ```python
> origin = ['a','b','c']
> copied = origin.copy()
> copied[2] = 'z'
> print(copied)
> print(origin)
> ```
>
> ```python
> # 출력 결과
> ['a','b','z']
> ['a','b','c']
> ```

## Lists' operators and methods

`list`에서 지원하는 다양한 operators가 존재합니다. 예를 보시면 다음과 같습니다.

```python
data = [1,2,3]
print("apple" in ["fruit", "plant", "iphone"])
print([1,2,3] + [4,5,6])
del 
```

~~~python
# 출력 결과
False
[1,2,3,4,5,6]
~~~

`in`은 [Operators-Membership operators](./Operators.md#Membership-operators)에서 봤었던 것이니 쉬울 것이니 쉬울 것입니다. `+`의 경우에도 left operand의 끝에 right operand를 이어 붙인다는 것을 직관적으로 이해할 수 있으실 겁니다.

이외에 list를 지원하는 다양한 method(function)들이 있습니다.  이를 정리한 표는 다음과 같습니다.

| Method        | Description                                                  | Example          |
| ------------- | ------------------------------------------------------------ | ---------------- |
| `append(x)`   | Adds `x` at the end of the list                              | data.append(x)   |
| `clear()`     | Removes all the elements from the list                       | data.clear(x)    |
| `copy()`      | Returns a copy of the list                                   | data.copy(x)     |
| `count(x)`    | Counts how many `x`s are in the list                         | data.count(x)    |
| `extend(x)`   | Add the elements of a `x`{list (or any iterable)}, to the end of the current list | data.extend(x)   |
| `index(x)`    | Same as data[`x`]\(data is `list`)                           | data.index(x)    |
| `insert(x,y)` | Adds `y` at the specified position(`x`)                      | data.insert(x,y) |
| `pop(x = -1)` | Same as del data[`x`]                                        | data.pop(x)      |
| `remove(x)`   | Removes the item with the specified value                    | data.remove(x)   |
| `reverse()`   | Reverses the order of the list                               | data.reverse()   |
| `sort()`      | Sorts the list                                               | data.sort()      |

이에 해당하는 모든 예시를 한 문서에서 다루기에는 너무 길어질 것 같습니다😥. 해당 자료에 대한 예시가 인터넷에 많이 있으니 참고하시면 좋을 것 같습니다.

---

[Back-Built-in Data structure](./Built-in-Data-structure.md)

