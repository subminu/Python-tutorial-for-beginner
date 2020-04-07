# Functions

드디어 `function`에 대해 배우게 되는 시간입니다. 도대체 `function`이 무엇이고, 어떻게 만들고 사용할 수 있는지 알아보도록 합시다.

## What is a function

`function`은 어떠한 기능을 수행하기 위한 command들의 집합입니다. 수학에서의 function과 비슷한 것 같지만 조금 다릅니다. input과 output이 꼭 존재할 필요는 없기 때문입니다. 

## Syntax of function

그렇다면 어떻게 `function`을 만들 수 있을까요? 이미 이전 문서의 예시에서 많이 보셨을 것이라 생각됩니다.

```python
def <func_name>(<parameters>): # def header:
    """docstring"""            #     code block
    <commands>
    return <anything>
```

`def`는 앞으로  `interpreter`에게 함수를 정의(define)하겠다는 것을 알려주는 역할을 합니다. 또한 `def`는 함수의 `header`가 시작함을 알려주는 keyword이기도 합니다. 있는 줄의 마지막을 보시면 `:`가 있습니다. 이는 함수의 `header`이 끝나고, 다음에 `code block`이 올 것이라는 것을 알려주는 역할을 합니다. 사실, `:`은 [Control flow](./Control-flow.md)에서 보았듯이 `code block`이 시작하기 전에 항상 붙어있음을 확인할 수 있습니다.

### func_name

`<func_name>`의 경우 본인이 원하는 함수의 이름을 선언하면 됩니다. 이때, [Variables - Variables Names](./Variable.md#Variables-Names)에서 언급했던 것과 마찬가지로 룰이 적용됩니다. 편의를 위해 다시 언급하자면 다음과 같습니다.

1. `<func_name>`의 첫 글자는 무조건 문자 혹은 "_"로 시작한다.
2. `<func_name>`의 첫 글자는 숫자로 시작할 수 없다.
3. `<func_name>`은 알파벳과 숫자, "_"로만 이루어져야 한다.
4. `<func_name>`은 소문자와 대문자를 구별한다.

### parameters(arguments)

매개변수라는 의미로 함수 내에서 사용할 변수를 외부에서 가져올때 필요로 하게됩니다. 앞서 언급한대로 input에 해당하는 부분이며 생략이 가능합니다.

주의해야 할 점이 있습니다.  자신이 정의한 parameter의 개수와 다시 사용할 때 전달 해줄 인자의 개수가 같아야합니다.

```python
def arg_3(a,b,c):
    pass

arg_3(1,2)
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: arg_3() missing 1 required positional argument: 'c'
```

다음과 같이 c에 대한 **positional argument**가 하나 부족하다는 에러가 출력됩니다. 여기서 말하는 **positional argument**라는 것은 다음과 같습니다.

#### positional argument

```python
def pos_arg(a,b):
    print(a)
    print(b)

pos_arg(21,7)
```

```python
# 출력 결과
21
7
```

다음과 같이 a와 b가 각각 순서대로 21, 7로 할당되어 출력된것을 알 수 있습니다.

#### keyword arguement

위치에 따라 할당하는 법이 있다면, 직접 인자를 언급하여 할당하는 법도 있습니다.

```python
def key_arg(a,b):
    print(a)
    print(b)
    
key_arg(b=21, a=7)
```

```python
# 출력 결과
21
7
```

위와 같이 같은 순서(21,7 순)으로 대입하였지만 각각에 인자를 직접 언급하여 할당시켰기 때문에 같은 출력 결과가 나온다는 것을 확인할 수 있습니다.

#### variable argument

여태까지 인자의 개수가 정해진 함수를 보았다면 이번에는 함수의 인자의 개수가 정해지지 않은 경우를 알아보도록 합시다. 가변 인자를 가지는 함수 중 대표적인 것으로 `print()`가 있습니다.

```python
print(1,"hello",3,True)
```

```python
# 출력 결과
1 hello 3 True
```

위와 같이 print에는 type에 상관없이 여러개의 인자를 받아 출력할 수 있습니다. 선언하는 방법은 다음과 같습니다.

```python
def var_arg(*arg):
    for i in arg:
        print(i)
        
var_arg(1,2,3)
```

```python
# 출력 결과
1
2
3
```

사실 이러한 예시는 이미 [Tuples - packing/unpacking](./Tuples.md#packing/unpacking)에서 한번 다루었던 내용입니다. 혹시 까먹으셨다면 읽어 보시는 것을 추천드립니다.

### commands

함수에도 어디까지가 함수인지 `interpreter`에게 알려주어야 합니다. 알려주기 위해서 [Control flow - code block](./Control-flow.md#code-block)에서 배웠던 들여쓰기를 해야합니다. python에서 권장하는 들여쓰기는 space bar 4회입니다.

### return

함수의 결과를 반환하는 statement입니다. output에 해당하는 부분이며, 앞서 언급한대로 생략이 가능합니다. return 뒤에 오는 `<anything>`은 **무엇이든** 반환할 수 있다는  말입니다.

```python
def literal():
    return 1 

def variable():
    a = "hello"
    return a

def function():
    return variable()

print(literal())
print(variable())
print(fucntion())
```

```python
# 출력 결과
1
hello
hello
```

다음과 같이 값 자체를 반환할 수 있으며, 변수는 물론 함수에서 다른 함수의 반환값도 반환할 수 있습니다.

한 가지 주의해야할 점이 있다면, return 구문을 통해 반환이 되면 return 이후의 명령은 실행되지 d않는 다는 점입니다.

```python
def caution():
    return 1
    print("hello")
caution()
```

위의 구문을 실행하면 "hello"가 출력되지 않습니다.

### docstring

해당 함수가 어떠한 역할을 하는지 설명하는, 일종의 문서화에 필요한 문구이며 생략이 가능합니다.

---

[Go - Scope & Namesapce](./Scope-&-Namespace.md)

