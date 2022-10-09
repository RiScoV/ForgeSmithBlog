---
title:  "Unity C# > 커스텀 이벤트 (UnityAction 과 Invoke)" 

categories:
  -  UnityDocs
tags:
  - [Game Engine, Unity]

toc: true
toc_sticky: true

date: 2022-10-02
last_modified_at: 2022-10-10
---

## UnityAction
```
필요헤더 : using UnityEngine.Events;
```

- 특정 기능을 담는 역할을 한다.
- C++ 등의 함수 포인터와 비슷한 역할을 하며, delegate 등의 대리자 역할을 한다.
- <> 연산자를 오버로딩하여, UnityAction<string> 등으로 매개변수 삽입이 가능하다.

- 단 기존 delegate 연산자와 다른 것은, UnityAction 클래스는 '체인 델리게이트'를 지원한다.
```
UnityAction func = () => { aaa... }
```
등으로 간단하게 람다식으로 표현되기도 하지만...
<br>
 ```
UnityAction func += () => { aaa... }
UnityAction func -= () => { aaa... }
```
로도 사용하여, 해당 클래스에 누적된 함수들을 순차적으로 호출시킬수 있다.
호출구문은, <u>func.Invoke();</u> 메서드를 호출하는 것으로 대리자를 호출시킨다.


## Invoke
- 반드시 MonoBehaviour 를 상속받아 사용해야한다. 즉, 유니티에서 지정하는 게임 오브젝트여야한다.
 - Invoke("함수명") 을 사용할수 있으며,
 - Invoke("함수명", n초) 등으로 n초 호출, 이렇게 사용이 가능하다.
 
하지만 "함수명" 이런식으로 넣으면 인텔리전스에서 탐색이 불가능하기 때문에 보통 nameof(함수명) 수식어를 사용하여 많이 사용한다.<br>
간단하게 해당 클래스에서 몇초후 호출시키고 싶다. 라는 기능을 원할떄 많이들 사용한다.
 
<br>


[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right}