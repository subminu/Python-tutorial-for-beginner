# Encapsulation

이번 문서에서는 `encapsulation`의 개념과 python에서는 해당 개념을 어떻게 구현할 수 있는지 알아보도록 하겠습니다. Python에서 해당 개념을 완벽히 설명드리는 것은 굉장히 비효율적이라고 생각됩니다. 이해를 돕기위해 python 코드로 설명을 드릴 것이지만, 개념적인 내용을 설명하기위한 수단일 뿐이기 때문에 실제 python코드를 실행하면 개념과 내용이 틀릴 수 있습니다.

## What is encapsulation

Encapsulation를 개념적으로 설명하자면 object의 attribute와 behavior을 하나의 캡슐로 저장해 두겠다는 것입니다. 좀 더 와닿게 설명하자면 외부에서 object의 attribute나 behavior을 함부러 접근하지 못하도록 하겠다는 것입니다.

## Access modifier

그렇다고 모든 variable과 method에 접근하지 못하도록 막는다는 이야기가 아니라 사용자가 접근할 수 있는 variable과 method를 제한해두자는 것입니다. 접근을 제어하는 방식에는 `public`, `private`, `protected`가 있습니다. 그리고 이들 각각을 접근제어자(`Access modifier`)이라고 합니다. 

그러나 python에서는 encapsulation을 제대로 지원하는 것이 아니기때문에 python을 통해 설명드리면 오히려 더 헷갈릴 것이라 생각합니다. 그렇기 때문에 다음의 표를 보고 이해하는 것을 추천드립니다.

| Access Modifier | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| public          | 어디서든 접근 가능                                           |
| private         | class의 code block내에서 호출할 때만 접근 가능               |
| protected       | 자기 자신의 class를 포함하고, 자식 class의 code block 내에서 호출할 때만 접근 가능 |

### Public

특정 제한없이 마음대로 부르고 수정할 수 있습니다. 특별한 키워드 없이 그냥 class를 구현하시면 전부 public으로 실행됩니다.

```python
class Foo:
    def __init__(self,a,b):
        self.a = a
        self.a = b
    def method(self):
        print("done")

inst = foo(1,2)
print(inst.a)
inst.b = 10
print(inst.b)
inst.method()
```

```python
# 출력 결과
1
10
done
```

### Private

오직 class 내부에서만 접근할 수 있도록 하겠다는 말입니다. python에서는 변수나 함수앞에 underscore 2개(`__`)로 설정할 수 있습니다.

```python
class Foo:
    def __init__(self,a,b):
        self.__a = a
        self.a = b
    def get_a(self):
        return self.__a

inst = Foo(1,2)
print(inst.__a)
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'foo' object has no attribute '__a'
```

다음과 같이 해당 attribute를 가지고 있지 않다고 error를 내보냅니다. 하지만 내장된 `get_a()`를 통해 값을 들고 올 수 있습니다.

```python
print(inst.get_a())
```

```python
# 출력 결과
1
```

private method도 동일하게 class 내부에서만 사용될 수 있습니다.

```python
class PasswordDecoder:
    def __init__(self):
        pass
    
    def __secret(self,password):
        return "".join([chr(ord(x)+1) for x in password]) # 이해 안하셔도 됩니다!
    
    def decoder(self,password):
        return self.__secret(password)
```

```python
pd = PasswordDecoder()
print(pd.__secret('Gdkkn\x1fVnqkc'))
```

```python
# 출력 결과
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'PasswordDecoder' object has no attribute '__secret'
```

마찬가지로 외부에선 부를 수 없습니다.

```python
print(pd.decoder('Gdkkn\x1fVnqkc'))
```

```python
Hello World
```

### Protected

python에서는 protected를 지원하지 않기 때문에 아래 예제를 실행하더라도 개념에 대한 설명처럼 error를 띄우지 않습니다. 개념을 이해하는 것에 의의를 두도록 하겠습니다.

protected는 private와 크게 다르지 않습니다. 외부에서는 접근할 수 없도록 되어 있는데요. 한가지 예외 상황을 둡니다. 바로 [상속(inheritance)](./Inheritance.md)을 받은 자식 class는 부모 class의 protected var과 method에 접근할 수 있도록 하는 것입니다.

```python
class Shape:
    def __init__(self, width, height):
        self._width = width
        self._height = height
    
class Rectangle(Shape):
    def __init__(self, width, height):
        Shape.__init__(self, width, height)
    def _area(self):
        return self._width * self._height
    def get_area(self):
        return self._area()
```

다음과 같이 Shape를 상속받은 Rectangle이 정의 되었다고 합시다. 그렇다면 protected에 의해 다음의 명령어는 실행되지 않습니다.

```python
a = Shape(3,4)
print(a._width)
print(a._height)
```

위의 두 명령어는 class 내부에서가 아닌 외부에서 부르기 때문에 실행되지 않습니다. 그렇지만 python에서는 protected를 지원하지 않기 때문에 출력은 다음과 같이 나옵니다.

```python
# 출력 결과
3
4
```

다음은 Rectangle에서 instance를 만들어 출력 해보도록 하겠습니다.

```python
b = Rectangle(4,5)
print(b._width)
print(b._height)
print(b._area())
```

```python
# 출력 결과
4
5
20
```

이들 또한 출력은 되지만 개념상으로는 출력 되지 않는 것이 protected의 개념입니다.

```python
print(b.get_area())
```

```python
# 출력결과
20
```

다음과 같이 자식 class 내부의 method를 통해 protected var/method를 접근할 수 있는 권한을 protected라고 합니다.

---

[Back - OOP](./Object-Oriented-Programming.md)