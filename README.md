# Python_Study

- python을 조금 더 깊게 공부하고 알고리즘을 공부하며 알게된 Python 관련 기술들을 정리해 둡니다. 

## 목차 
1. [파이썬언어에 대해 깊게 알기](#파이썬언어에-대해-깊게-알기)
2. [알고리즘에서 알면 좋은 기술들](#알고리즘에서-알면-좋은-기술들)
3. [클린 파이썬](#클린-파이썬)
4. [디자인패턴](#디자인패턴)
5. [Pythonic한 사고](#pythonic한-사고)


<details markdown="1">
<summary></summary>


</details>

---
## 파이썬언어에 대해 깊게 알기
<details markdown="1">
<summary>Python의 정렬알고리즘 : Sort()</summary>

<ul>
  <br>
  <li> 파이썬에서는 quick sort가 아니라 Tim sort 방식을 사용한다.
  <li> quick sort는 최악케이스에서 O(n^2)의 시간복잡도를 가지지만 Tim sort는 일반적으로 O(nlogn)을 보장한다.
  <li> Merge sort와 insert sort의 조합으로 만든 알고리즘이라는데 추후 스터디를 더 해보고 싶다.
</ul>
</details>

<details markdown="1">
<summary>Python의 imutable과 mutable </summary>


</details>


<details markdown="1">
<summary>Python의 int는 왜 모든 수를 다룰 수 있을까?</summary>

<br>
<ul>
  <li> 다른 언어와 달리 쓸 때 정말 편리했고 변수를 초기화할 떄 따로 자료형을 지정하지 않는 python의 특성상 굉장히 편리한 기술이라고 생각되었다.
     하지만 그러면서도 int가 4바이트 long이 8바이트인 C언어와 달리 모든 숫자를 int하나에 다 넣을 수 있는 Python이 메모리를 관리하는데
     매우 불리하지 않을까 하는 고민을 했다.
<li>Python에서 int의 방식은 임의 정밀도라 불린다. 정수를 숫자의 배열로 간주하는 것인데 자릿수 단위로 쪼개어 배열형태로 표현한다.
<li>자세한 방법은 추가로 알아보자 
</details>


<details markdown="1">
<summary>Python과 C++의 참조 방식 차이</summary>

<br>
<ul>
  <li> C++에서는 참조를 할때 주소를 참조하지만 Python은 주소참조가 아닌 객체를 참조한다. 
  <li>Python에서는 모든 것이 객체이다. 단순한 숫자들 5,7,19.. 등도 특정 ID를 가지고 있으며 <br>
    a = 10 이런식으로 지정하면 a의 주소에 10을 넣는 c/c++방식이 아닌 10의 주소를 참조한다. <br>
    만약 a=8로 다시 변경하게 되면 c에서의 &a는 변함이 없고 안의 내용만 바뀌지만 python에서 id(a)는 id(8)로 변경된다.<br>
  <li>따라서, mutable 자료형을 다룰 때 특히 주의해야한다. C/C++ 같은 방식으로 접근하면 값이 바뀔 수 있으므로 <br>
    pythonic한 사고가 필요하다. 
</ul>
</details>



---
## 알고리즘에서 알면 좋은 기술들 
---
## 클린 파이썬
---
## 디자인패턴
---
## Pythonic한 사고 
- Tim sort를 만든 팀 피터스가 정의한 내용이다. 한번씩 보고 자자 

```python
import this
"""
Beautiful is better than ugly. 아름다움이 못생긴 것보다 낫다
Explicit is better than implicit. 명시가 암시보다 낫다
Simple is better than complex. 단순함이 복잡함보다 낫다
Complex is better than complicated. 복잡함이 꼬인 것보다 낫다
Flat is better than nested. 수평이 계층보다 낫다
Sparse is better than dense. 여유가 빡빡한 것보다 낫다
Readability counts. 가독성이 중요
Special cases aren't special enough to break the rules. 특별한 경우도 규칙을 어길 정도로 충분히 특별하지 않다
Although practicality beats purity. 실용성이 순수성보다 중요할지라도
Errors should never pass silently. 에러들은 조용하게 보내지마라 
Unless explicitly silenced. 적어도 명시적으로 에러를 다루는게 아니라면 
In the face of ambiguity, refuse the temptation to guess. 모호함을 직면할 때에 추측하겠다는 유혹을 거부해라
There should be one-- and preferably only one --obvious way to do it. 바람직하고 유일한 명확한 하나의 길이 존재할 것 이다
Although that way may not be obvious at first unless you're Dutch. 네덜란드 사람이 아니라면(?) 그 방법은 명확하지 않을 수 있다
Now is better than never. 지금하는게 아무것도 안하는 것보다 훨씬 낫다.
Although never is often better than *right* now. 아무것도 안하는 것이 종종 '당장' 하는 것보다 나을 지라도 당장하자
If the implementation is hard to explain, it's a bad idea. 만약 구현이 설명하기 어렵다면 그것은 나쁜 아이디어이다.
If the implementation is easy to explain, it may be a good idea. 만약 구현이 설명하기 쉽다면 그것은 좋은 아이디어이다.
Namespaces are one honking great idea -- let's do more of those! 
"""
```

