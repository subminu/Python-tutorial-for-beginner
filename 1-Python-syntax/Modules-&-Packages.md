# Modules & Packages

이번 문서에서는 `module`과 `Package`가 무엇인지 알아보고 어떻게 만들고 활용할 수 있는지 알아보도록 합시다. 

## What is Modules

소규모의 프로젝트의 경우 python 파일 하나로 해결 할 수 있겠지만 몇 만줄의 코드를 작성해야하는 대규모 프로젝트일 경우, 파일 하나로 유지 보수를 하기에는 쉽지 않습니다. 그렇기 때문에 여러개의 파일을 나누어 사용할 수 있도록 만들어낸 개념이 **module** 입니다. 

## How to make modules

딱히 특별한 것은 없습니다. 일반적으로 python코드를 작성하고 저장하게되면 `.py`라는 확장자 명을 가진 파일하나가 생성되는 것을 볼 수 있습니다. 이 파일 자체가 module이 될 수 있습니다. 두개의 python 파일을 작성하였다고 봅시다.

###### test.py

```python
a = 10
b = "hello"

def hello():
    print("Hello World!")
    
def bye():
    print("Bye bye")

class A:
    def __init__():
        print("A instance was generated")
```

###### main.py

```python
print(a)
print(b)
hello()
bye()
instance = A()
```

`test.py`와 `main.py`를 작성하였습니다. 실제로 원하는 것은 `test.py`에 정의 된 값들을 `main.py`에서 사용하고 싶은 것입니다. 그러나 `main.py`를 실행시키려고 하면 정의되지 않은 값을 사용하려고 한다는 에러메시지와 함께 실행되지 않을 것입니다. 어떻게 외부의 다른 파일에 있는 값을 불러서 사용할 수 있을까요?

## How to use modules

외부의 다른 python 파일을 불러서 사용할 수 있는 keyword가 있습니다. 바로 `import`라는 키워드 입니다. 

###### main.py

```python
import test
print(test.a)
print(test.b)
test.hello()
test.bye()
instance = test.A()
```

`import test`가 추가되었습니다. 여기서 `import`뒤의 자신이 외부에서 참조하고자 하는 파일 명을 확장자 명(`.py`)을 빼고 선언하시면 됩니다. 그런데 실제 사용하는 것을 보면 test가 마치 object처럼 사용되는 것을 확인할 수 있습니다. 이와 같이 module이라는 것은 외부의 파일을 objest처럼 `.`을 이용하여 참조하여 접근할 수 있다는 점이 특징입니다.

### as

`test.py`에서 정의된 class, function, variable들을 부를 때마다 `test.~~`을 써주는 것이 귀찮습니다 이에 대해 import 할 때 test 대신에 다른 이름으로 사용할 수 있도록 해주는 keyword가 바로 `as`입니다.

###### main.py

```python
import test as t
print(t.a)
print(t.b)
t.hello()
t.bye()
instance = t.A()
```

### from

`test.py`에서 특정 method, variable 또는 class만 가져오고 싶을 때가 있습니다. 이때 사용하는 keyword가 `from`입니다.

###### main.py

```python
from test import a, hello, A
print(a)
hello()
instance = A()
```

이때, `from ~~ import ~~`으로 불러온 객체들은 따로 `test.~~`와 같이 붙여줄 필요없이 곧장 사용가능합니다. 만약 `test.~~`를 사용하지 않고 `test.py`에 있는 객체들을 전부 사용하고 싶으면 다음과 같이 선언해주면 됩니다.

###### main.py

```python
from test import *
print(a)
print(b)
hello()
bye()
instance = A()
```

`*`는 전부의 의미를 가지고 있다고 보시면 되겠습니다.

## What is packages

Package는 module들을 directory 구조처럼 구조화시킨 형태를 뜻합니다. 좀 더 직관적으로 표현하자면, module들을 담아둔 폴더 자체가 package가 되는 것입니다. 다음과 같이 파일 구조를 만들었다고 합시다.

```
DGIST/                       # package
	__init__.py
	E8/                      # subpackage
		__init__.py
		borrow.py            
		return.py
		study.py
	E7/                      # subpackage
		__init__.py
		research.py
	S1/                      # subpackage
		__init__.py
		exercising.py
```

그렇다면 DGIST 자체가 package가 되는 것입니다. 또한, package 안에 꼭 python파일 뿐만 아니라 package을 포함할 수 있습니다. 이러한 package를 sub-package라고 부릅니다. 

만약 exercising에 대한 변수, 함수, 클래스를 사용하고 싶다면 다음과 같이 import를 이용하면 됩니다.

###### DGIST/S1/exercising.py

```python
def test():
    print("exercising now")
```

###### main.py

```python
import DGIST.S1.exercising

DGIST.S1.exercising.test()
```

```python
# 출력 결과
exercising now
```

다음과 같이 package가 module에서 사용했던 것 처럼 `.`을 통해 접근할 수 있습니다. 

### `__init__.py`

예시에서 class에서 본듯한 생소한 파일이 보입니다. 바로 `__init__.py`입니다. python 버전 3.3 이전에는 해당 파일이 directory마다 하나씩 존재해야지만 python이 package로 인식할 수 있었습니다. 그러나 3.3 이후 버전부터는 생략이 가능합니다. 그렇기 때문에 `__init__.py` 안이 비워져 있어도 package로 인식은 가능합니다.

그렇다면 `__init__.py`의 역할은 무엇일까요? `import package`를 하였을 때 어떤 module 혹은subpackage를 불러올지 정의하는 역할을 합니다.

###### DGIST/\_\_init__.py

```python
from DGIST import E8, E7, S1
```

다음과 같이 `import DGIST`를 하였을때, 참조할 수 있는 module들을 정의할 수 있습니다. 

###### main.py

```python
import DGIST
DGIST.S1.exercising.test()
```

```python
# 출력 결과
exercising now
```

이것 이외에도 `from ~~ import *`을 실행할 때, 어떤 module을 불러 올 것인지 정의하는 역할을 합니다. 해당 구문은 `__all__`이라는 variable로 정의하게됩니다.

###### DGIST/E8/borrow.py

```python
def book():
    print("borrowed a book")
```

###### DGIST/E8/return.py

```python
def book():
    print("returned a book")
```

###### DGIST/E8/study.py

```python
def programming():
    print("studying python")
```

###### DGIST/E8/\_\_init\_\_.py

```python
__all__ = ['borrow', 'return']
```

각각의 파일을 위와 같이 정의하였다고 합시다.

###### main.py

```python
from DGIST.E8 import *

DGIST.E8.borrow.book()
DGIST.E8.return.book()
DGIST.E8.study.programming()
```

```python
# 출력 결과
borrowed a book
returned a book
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'study'
```

다음과 같이 `__all__`에서 정의하지 않았던 study는 참조되지 않았음을 알 수 있습니다.

---

[Go - New Chapter](../Virtual-enviroment(Anaconda)-&-Mange-package(PIP)/Basic-use-of-anaconda-prompt.md) 