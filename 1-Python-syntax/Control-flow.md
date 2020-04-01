# Control flow

여태까지 단순한 data들만 학습하였다면 이제부터는 data를 가지고 활용하는 방법들에 대해서 알아보도록 합시다.

Programming language를 배우다 보면 꼭 마주치게 될 두가지 구문이 있습니다. 바로 반복문과 조건문인데요. 이들 둘의 개념을 잘 알아두면 다른 언어를 학습할 때 도움이 될 것 입니다. python에서는 다음과 같은 구문을 제공하고 있습니다.

- [`if-else`](./if-else.md)
- [`for`](./for.md)
- [`while`](./while.md)

Control flow라는 것은 다른 것이 아니고, 어떠한 코드를 작성할 때, 항상 위에서 아래, 좌에서 우로 읽어가면서 실행되는 흐름이 일반적인 흐름이라면, 그 흐름을 제어하는 것을 이야기 합니다. 

```python
# 통장에서 돈을 빼내는 프로그램
balance = 0
withdraw = input("how much do you want?")
balance -= withdraw # 통장 잔액이 없어도 출금해준다.
print("here it is:", withdraw)
```

해당 코드는 아무런 control flow가 없이 진행되는 코드입니다. 읽다보면 뭔가 이상한 점을 발견 할 수 있을텐데요. 통장 잔액이 0원이지만 그래도 출금해주는 코드임을 알 수 있습니다. 

자신이 적은 코드가 순서대로 진행되는건 좋지만 어떨 때는 실행되지 않았으면 좋겠습니다. 여기서 말하는 "어떨 때"는 출금하려는 금액이 잔고보다 많을 때가 되겠군요.

```python
# 통장에서 돈을 빼내는 프로그램
balance = 0
withdraw = input("how much do you want?")
if balance >= withdraw: # 수정된 부분
balance -= withdraw # 실행 되어야 하는 부분
print("here it is:", withdraw) # 실행 되어야 하는 부분
```

`if`문은 해당 조건이 만족되었을 때만 실행시켜주니 어느정도 해결한 것 같습니다만 if문이 실행되면 어느 구문이 실행되어야 하는지 정해지지 않았습니다. 즉 실행시키고픈 구문을 `interperter`는 알지 못합니다.

```python
# 통장에서 돈을 빼내는 프로그램
balance = 0
withdraw = input("how much do you want?")
if balance >= withdraw: # 수정된 부분
    balance -= withdraw # 실행 되어야 하는 부분
    print("here it is:", withdraw) # 실행 되어야 하는 부분
```

위와 같이 실행 시키고 싶은 구문을 다른 구문과 다르게 **들여쓰기**하여 표현했습니다. 이처럼 Control flow에서 순서대로 진행되는 것이 아닌 코드의 부분을 묶어주어 표현된 것을 **`code block`**이라고 합니다.

`code block`을 표현하는 방법은 언어마다 각기 다릅니다. Python에서는 다음과 같이 **들여쓰기**를 통해 구분합니다. 일반적으로 들여쓰기는 `Tab`키로 알고 있겠지만 python에서 권장하는 **들여쓰기**는 **space bar 4**번을 권장합니다. (`Tab`는 권장하지 않습니다.)

해당 예시는 `if`을 가지고 설명을 드렸지만 **들여쓰기**의 경우 `for`, `while`에서도 동일하며, 앞으로 배울 `function`, `class`에서도 동일하게 적용됩니다.

이처럼 각 언어에서 권장하는 `convention`이 있기 마련입니다. 처음 들어보셨을 수도 있지만, 프로그래밍 언어에 철학이 담겨 있다는 소리를 들어보셨을 것입니다. Python에도 자신 만의 철학을 가지고 만들어진 언어이기 때문에 문법이 조금씩 다르며 권장하는 coding style도 다릅니다.

그렇다고 꼭 python 철학을 알아야하고 coding style을 따라야할 의무는 없습니다. 그래도 알아두면 조금씩 도움이 될 것입니다.

원문

- [Python pilosophy](https://www.python.org/dev/peps/pep-0020/)
- [Python coding style guide](https://www.python.org/dev/peps/pep-0008/)

번역

- [Python pilosophy](https://brunch.co.kr/@lkj28/101)
- [Python coding style guide](https://spoqa.github.io/2012/08/03/about-python-coding-convention.html)

---

[Go - Functions](./Functions.md)