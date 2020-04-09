# Inheritance

이번 문서에서는 상속(inheritance)란 무엇이고, 왜 필요한지, 또 어떻게 사용되는지 알아보도록 합시다. 먼저 상속이라고 하면 부모로부터 물려받는 이미지가 떠오릅니다. 이와 비슷하게, class도 부모 class와 자식 class가 존재합니다. 이들 각각을 `base(parent) class`와 `derived(child) class`라고 합니다.

## What is inheritance

```python
class Shape: # base class
    pass

class Rectangle(Shape): # derived class
    pass
```

위와 같이 코드가 있을때, Rectangle class는 Shape class로부터 상속받았다라고 합니다. 이처럼 parent class의 특성과 행동을 참조하는 행위를 inheritance라고 합니다. 그렇다면 이러한 inheritance는 왜 사용하는 것일까요?? 

## Why inheritance need

inheritance가 없다고 해서 본래 문제를 풀지 못하는 것은 아닙니다. 하지만 parent class를 참조하여 편하게 코딩을 할 수 있다는 점에서 사용되는데요. 다음의 예시를 봅시다.

```python
class Rectangle:
    def __init__(self, height, width):
        self.height = height
        self.width = width
    
    def get_area(self):
        return self.height * self width

class Triangle:
    def __init__(self, height, width):
        self.height = height
        self.width = width
    
    def get_area(self):
        return self.height * self width
```

위의 예시를 보시면, Rectangle과 Triangle에 필요한 특성(높이, 너비)와 함수(넓이 구하기)가 서로 겹칩니다. 실행 자체에는 전혀 문제가 없지만 나중에 이러한 class들이 다수 생기게 된다면, 유지 보수 면에서 매우 불편해질 것입니다. 가령 각 class에 동일하게 새로운 특성 값을 새롭게 만들고 싶다면 모든 class에 대해 일일이 복사/붙여넣기를 해야할 것입니다.

그러나 공통적인 특성을 base(parent) class를 만들어 두고, 이를 derived(child) class가 참조할 수 있도록 해두면 다음과 같이 코드를 작성할 수 있습니다.

```python
class Shape:
    def __init__(self, height, width):
        self.height = height
        self.width = width
    
    def get_area(self):
        return self.height * self width

class Rectangle(Shape):
    def __init__(self, height, width):
        Shape.__init__(self, height, width)

class Triangle(Shape):
    def __init__(self, height, width):
        Shape.__init__(self, height, width)
```

이렇게 정의를 해둔다면 다음과 같이 사용할 수 있습니다.

```python
rec = Rectangle(4,5)
tri = Triangle(3,4)
print(rec.get_area())
print(tri.get_area())
```

```python
# 출력 결과
20
12
```

실제 각각의 child class에는 get_area() method가 정의 되지 않았지만. parent class의 get_area()를 참조하여 마치 해당 함수의 코드가 복사/붙여넣기되어 정의된 것 마냥 사용할 수 있습니다. 그런데 상속받은 child class에서 `__init__()`를 보시면 instance 변수를 익숙하지 않은 방법으로 사용하는 것을 볼 수 있습니다.

`Shape.__init__(self, height, width)`

해당 구문은 Shape에 있는 `__init__`함수를 불러와서 각각의 parameter을 넘겨주게 됩니다. 이처럼 parent class에 있는 constructor을 직접 불러서 초기화를 해줄 수 있습니다. Python에서는 위와 같은 구문을 좀 더 편하게 사용할 수 있도록 다음의 함수를 지원합니다.

#### super()

`super().__init__(height, width)`

해당 구문도 위의 구문과 동일하게 구현됩니다.

## Apply inheritance

여태까지 예시들은 참조만하고 기능을 확장하지 않았는데요, 상속을 받은 뒤에 추가적으로 기능을 확장시킬 수도 있습니다. 다음은 좀 더 일반적인 상속의 예시입니다.

### Multilevel inheritance

상속을 여러 단계로 받아서 기능을 확장해 나갈 수 있습니다.

```python
class Animal:
    def __init__(self, name):
        self.name = name
        
    def eat(self):
        print("eating now")
        
    def sleep(self):
        print("sleeping now")
        
class Human(Animal):
    def __init__(self, name):
        super().__init__(name)
        
    def talk(self):
        print("bla bla")
        
class Student(Human):
    def __init__(self, name, st_num):
        super().__init__(name)
        self.st_num = st_num
        
    def study(self):
        print("studying")
```

```python
a = Student("Alex", 202011113)
a.eat()
a.sleep()
a.talk()
a.study()
```

Student class가 Animal class를 직접 참조하지 않았지만 Human이 Animal class를 참조 하였기 때문에 Student에서도 `eat()`, `sleep()` 함수가 실행이 됩니다.

### Multiple inheritance

상속을 받을 때, 여러개의 base class로부터 상속을 받을 수도 있습니다. 

```python
class Camera:
    def __init__(self,num):
        self.camera_Num = num
        
    def take_a_picture(self):
        print("A picture was taken")
        
class Speaker:
    def __init__(self, num):
        self.speaker_num = num
        
    def make_sound(self):
        print("BBIP")
        
class Display:
    def __init__(self, num):
        self.display_num = num
        
    def display_something(self):
        print("displaying")
        
class Cellphone(Camera, Speaker, Display):
    def __init__(self, n1, n2, n3):
        Camera.__init__(self, n1)
        Speaker.__init__(self, n2)
        Display.__init__(self, n3)
```

단, `super()`은 사용하지 못합니다. 정확하게 어떤 base class인지 명확하지 않기 때문입니다.

---

[Back - OOP](./Object-Oriented-Programming.md)