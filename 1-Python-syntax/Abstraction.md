# Abstraction

이번 문서에서는 어떻게 추상적으로 구현할 수 있는지 자세하게 다루어 보도록 하겠습니다. 앞선 OOP에서는 object에 대한 이야기만 했었는데요. Class에 대해서 알아보도록 하겠습니다.

Object를 **`attribute`와 `behavior`의 집합체**라고 하였습니다. class는 이러한 object를 만들 때 필요한 **청사진**이라고 보시면 됩니다. 

현실적인 문제를 예로 들어 보겠습니다. 여러분들이 해결해야할 문제가 게시판을 만드는 것이라고 합시다. 게시판에는 게시물들이 여러개 있습니다. 그런데 각 게시물에는 공통적인 특징들이 있습니다.

- 제목
- 작성자
- 작성한 시각
- 내용

위와 같은 특성은 어느 게시물이든 공통적으로 가지고 있습니다. 여기서 게시물이란 object를 담는 list를 만들면 쉽게 게시판을 만들 수 있을 것 같습니다. 게시물이란 object는 어떻게 만들 수 있을까요? 

Object를 생성하기 앞서 "해당 object에는 ~~한 특성(`attribute`)와 행동(`behavior`)을 가질거야"라는 **청사진**의 역할을 하는 class를 선언할 필요가 있습니다. Python에서 class 선언은 다음과 같이 할 수 있습니다.

#### class statement

```python
class <class_name>:
    """ docstring """
    pass
```

마찬가지로 `<class_name>` 또한 [Variables - Variables Names](./Variables.md#Variables-Names)와 같이 4가지 규칙을 따라야합니다. `:`는 [Functions - Syntax of function](./Functions.md#Syntax-of-function)에서 배웠듯이 뒤에 `code block`이 시작될 것이라는 것을 알려주는 지시자로 보시면 됩니다. docstring에 해당하는 부분은 [OOP - Function](./Object-Oriented-Programming.md#Function)의 예시에서 보았던 것처럼, 해당 class를 설명하기 위한 부분이라 보시면 됩니다. 이를 예시에 맞게 다시 작성해주면 다음과 같습니다. 

```python
class post:
    """This is example of class"""
    pass
```

다음은 게시물의 공통적인 특성인 제목, 작성자, 작성한 시각, 내용들이 담겨져 있다는 것을 적어주면 되겠습니다.

#### class variable

```python
class post:
    """This is example of class"""
    title = "title"    # 이는 instance variable이 아니라 class variable입니다!
    author = "me"
    time = "now"
    content = "hello world"
```

위와 같이 정의를 마쳤으면 최종적으로 게시물(object)를 생성하기 위한 준비를 끝냈습니다. object는 다음과 같이 생성할 수 있습니다.

```python
var = <class_name>()
```

`()`을 붙여주셔야 object를 생성할 수 있습니다. 이렇게 생성된 object를 `instance`라고 합니다.

```python
a = post()
b = post()
print(a.title, a.author, a.time, a.content)
print(b.title, b.author, b.time, b.content)
```

```python
# 출력 결과
title me now hello world
title me now hello world
```

게시물은 만들었는데 object(instance)에 들어있는 값들이 전부 동일합니다. 게시물 마다 각각 다른 내용을 포함하면 좋을텐데 아쉽습니다. 이는 `instance variable`을 이용하면 해결할 수 있습니다.

> Tip👀
>
> class variable은 instance끼리 공유하는 변수입니다. 그렇기 때문에 다음과 같이 class로 직접 접근하여 바꾸면 모든 instance의 값도 변하게 됩니다.
>
> ```python
> post.title = "changed"
> print(a.title)
> print(b.title)
> ```
>
> ```python
> # 출력 결과
> changed
> changed
> ```

> Tip👀
>
> `(object).(something)`의 의미는 object안에 있는 something을 부르겠다는 의미입니다. 

#### instance variable

```python
class post:
    """This is example of class"""
    def __init__(self, title, author, time, content):
        self.title = title
        self.author = author
        self.time = time
        self.content = content
```

처음 보시는 것들이 보이실 것입니다. 차근차근 알아가보도록 합시다.

##### `__init__`

Python에서는 사전에 약속된 몇가지 method가 있습니다. 이들을 구분하는 구분자는 `__(something)__`처럼 양쪽에 밑줄 2개(underscore)로 구분하게 됩니다. 여기서 `__init__`은 initialize의 줄임말로서 instance를 생성할 때, 가장 먼저 실행되는 함수로 **`constructor`**라고도 불리웁니다. 이는 instance variable을 초기화할 때 사용됩니다.

##### `self`

class는 일종의 **청사진**이라고 하였습니다. class로부터 생성되는 instance가 여러개 생길 것을 예상하고 설계를 해야하는 과정에서 아직 생기지 않은 object(instance)의 값을 원활하게 다루기 위한 변수입니다. 변수라고 언급했던 것 처럼, self라는 단어 대신에 다른 언어를 사용해도 됩니다. 그러나 python에서는 self를 사용하는 것을 권장하고 있습니다. `self`에는 instance object가 대입됩니다.

`__init__`을 선언하면 어떻게 python에서 instance를 생성할 수 있는지 알아보도록 합시다.

```python
a = post("first post", "me", "yesterday", "this is first post")
b = post("second post", "you", "today", "this is second post")
print(a.title, a.author, a.time, a.content)
print(b.title, b.author, b.time, b.content)
```

```python
# 출력 결과
first post me yesterday this is first post
second post you today this is second post
```

다음과 같이 그냥 <class_name>의 `()`의 argument로 넘겨주면  `__init__`의 `()`안에 parameter를 대입한 것처럼 작동합니다.

여기까지 여러분은 class에서 `attribute`에 해당하는 내용을 배웠습니다. 다음은 class의 `behavior`에 해당하는 부분을 배워보도록 하겠습니다.

원활한 설명을 위해 post의 class에 좋아요 기능을 추가하도록 하겠습니다.

#### method

```python
class post:
    """This is example of class"""
    def __init__(self, title, author, time, content):
        self.title = title
        self.author = author
        self.time = time
        self.content = content
        self.likes = 0 # 꼭 parameter에서 받아서 초기화할 필요는 없습니다!
    
    def like_this_post(self):
        print("you like", self.title)
        self.likes += 1
```

class안에 함수 like가 정의 되어 있습니다. 함수와 동일하게 정의하지만 특별하게, class 안에서 정의된 함수를 **`method`**라고 부릅니다. 또한 `method`에는 첫번째 인자로 `self`가 필요합니다. 당연히 어떤 instance에서 실행되어야 하는 method인지 알아야 정상적으로 작동되겠죠?

위와 같이 정의 하였으면, 정상적으로 작동하는지 확인하여 봅시다.

```python
a = post("first post", "me", "yesterday", "this is first post")
b = post("second post", "you", "today", "this is second post")
a.like_this_post()
print(a.likes)
print(b.likes)
```

```python
# 출력 결과
you like first post
1
0
```

정상적으로 출력되지만 이해가 되지 않는 부분이 있습니다. 

```python
a.like_this_post()
```

이 부분의 `()`에는 어떠한 parameter가 들어가 있지 않음에도 불구하고 정상적으로 출력됩니다. 이는 자체적으로 `self`에 object를 넘겨주게 됩니다. 즉 다음의 코드로 자동으로 해석되어 실행됩니다.

```python
post.like_this_post(a)
```

## Namespace

class를 정의하면 class만의 namespace가, instance를 생성하면 instance 만의 namespace가 생깁니다.

```python
class post:
    """This is example of class"""
    title = "no title" # 이부분을 새롭게 추가했습니다! instance_var의 title과 겹쳐요!
    def __init__(self, title, author, time, content):
        self.title = title
        self.author = author
        self.time = time
        self.content = content
        self.likes = 0 # 꼭 parameter에서 받아서 초기화할 필요는 없습니다!
    
    def like_this_post(self):
        print("you like", self.title)
        self.likes += 1
                
a = post("first post", "me", "yesterday", "this is first post")
b = post("second post", "you", "today", "this is second post")
```

이런 식으로 1개의 class와 2개의 object를 만들었다고 합시다. 그렇다면 총 3개의 namespace가 만들어질 것입니다.(global, built-in 등을 제외하고) 이들을 확인하는 방법은 다음과 같습니다.

```python
print(post.__dict__)
```

```python
# 출력 결과
{'__module__': '__main__', '__doc__': 'This is example of class', 'title': 'no title', '__init__': <function post.__init__ at 0x0000021EC66BC4C8>, 'like_this_post': <function post.like_this_post at 0x0000021EC66BC558>, '__dict__': <attribute '__dict__' of 'post' objects>, '__weakref__': <attribute '__weakref__' of 'post' objects>}
```

```python
print(a.__dict__)
```

```python
# 출력결과
{'title': 'first post', 'author': 'me', 'time': 'yesterday', 'content': 'this is first post', 'likes': 0}
```

```python
print(b.__dict__)
```

```python
# 출력 결과
{'title': 'second post', 'author': 'you', 'time': 'today', 'content': 'this is second post', 'likes': 0}
```

위와 같이 각각의 namespace를 확인할 수 있습니다. 그런데 여기서 궁금한 점은 class variable을 instance에서 부르는 방법도 a.title이고, instance variable의 title을 부르는 방법도 a.title입니다. 과연 다음과 같은 상황에선 python은 어떤 값을 출력하게 될까요?

```python
print(a.title)
```

```python
# 출력 결과
first post
```

다음과 같이 먼저, instance의 namespace를 살펴보고 찾는 값이 있으면 해당 값을 들고오게 됩니다.

```python
del a.title
print(a.title)
```

```python
# 출력 결과
no title
```

a에 포함되어 있는 attribute를 지우고 다시 a.title을 부르게 되면 다음과 같이 class variable에 있는 값인 "no title"을 출력하게 됩니다.

## Attribute append/delete

방금 a에 있는 attribute를 지웠다고 했습니다. 이처럼 class나 instance의 namespace에 정의된 값을 지우는 것도, 추가하는 것도 가능합니다.

추가하기 전에 진짜로 a의 namespace에서 지워졌는지 확인해보도록 합시다.

```python
print(a.__dict__)
```

```python
# 출력 결과
{'author': 'me', 'time': 'yesterday', 'content': 'this is first post', 'likes': 0}
```

그리고 다시 a에게 title을 추가해 봅시다.

```python
a.title = "recoverd title"
print(a.__dict__)
```

```python
{'author': 'me', 'time': 'yesterday', 'content': 'this is first post', 'likes': 0, 'title': 'recoverd title'}
```

마지막에 새롭게 추가 된 것을 확인할 수 있습니다.

지우는 방법은 위에서 사용한 방법대로 `del` keyword를 사용하면 됩니다.

```python
del b.author
print(b.__dict__)
```

```python
# 출력 결과
{'title': 'second post', 'time': 'today', 'content': 'this is second post', 'likes': 0}
```

---

[Back - OOP](./Object-Oriented-Programming.md)