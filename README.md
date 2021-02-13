# Python_Study

- python을 조금 더 깊게 공부하고 알고리즘을 공부하며 알게된 Python 관련 기술들을 정리해 둡니다. 

## 목차 
1. [파이썬언어에 대해 깊게 알기](#파이썬언어에-대해-깊게-알기)
2. [알고리즘에서 알면 좋은 기술들](#알고리즘에서-알면-좋은-기술들)
3. [클린 파이썬](#클린-파이썬)
4. [디자인패턴](#디자인패턴)
5. [Pythonic한 사고](#pythonic한-사고)

<!-- 
<details markdown="1">
<summary></summary>

<br>
<pre>

</pre>

</details>
-->

---
## 파이썬언어에 대해 깊게 알기
<details markdown="1">
<summary>함수의 기본인자로 mutable을 주게되면 어떤일이 벌어질까</summary>

<br>
<pre>
이건 진짜 헷갈렸던 부분인데 python 함수가 어떻게 초기화되는지를 알아야한다. 
먼저 왜 이러면 안되냐면 
def foo(bar = []) : 
    bar.append("baz")
    return(bar) 
이렇게 선언한 뒤 foo()를 세번 반복하면 기본값인 []로 초기화가 안되기때문에 ["baz","baz","baz"]가 되버린다. 
함수도 파이썬에서는 일급객체이기 때문에 기본값이 mutable로 들어오게 되면 메모리 주소로 저장되기 때문에 
파이썬 함수의 디폴트 매개변수는 호출 시점을 따르지 않는다.
해결방법은
1. 함수의 기본인자로 다른 함수의 결과나 mutable 자료형을 설정하지 않는 것이다. 
2. 함수 호출마다 지금 서버의 시간을 입력해야할 필요가 있을 수 있는데 그럴때는 이렇게 사용한다. 
       def foo(bar=None):
           if not bar:
               bar = 함수() 혹은 mutable
           동작
       이러면 None이 mutable이 아니므로 id를 참조하지 않아 bar를 정상적으로 사용할 수 있다.
       PEP 505 -- None-aware operators에 따르면 if not bar : bar = []를 간단하게 bar??=[]로 줄일 수 있다. 
</pre>
</details>

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

<details markdown="1">
<summary>다중할당(Multiple Assingment)</summary>

<br>
<li> 파이썬만의 특별한 할당방법이다.
<br>예를 들면 a, b = 1, 2 이렇게 할당하는데 매우 매우 편리하다. 
<br>특히, python은 C와 달리 = 연산자는 해당 객체를 참조하므로 
<br>a = 2, b=4 일 때
<br>a = b-2
<br>b = 10 한 뒤 a를 출력해보면 결과가 8이 나온다. 앞서 말했듯이 
<br>단순한 값을 주소에 저장한게 아니라 객체를 참조하기 때문인데 다중 할당을 이용해 
<br>a, b = b-2, 10 이렇게 입력하면 a는 2가 된다. 
<br>포인터개념이 없다보니 a=b 이러면 단순한 값에 의한 호출로 오해하기 쉬운데 다중할당을 이용해 오류를 줄여주자 
<br> 
<br>또한, Swap()을 편리하게 할 수 있다.
<br>다른 언어에서 일반적인 swap은 temp라는 빈 변수를 추가해 temp=a  ->  a=b  -> b=temp 이렇게 중계하는데 
<br>Python에서는 다중할당을 이용해 a, b = b, a 한줄로 표현이 가능하며 가독성 또한 높다. (성능차이는 없다고한다.)
<br>이러한 다중할당을 이용하지 않으면서 따로 변수를 선언하지 않아도 swap할 수 있는 방법이 있는데 
<br>a+=b ==> b = a-b ==> a-=b 이렇게 사용하면 숫자를 기준으로 메모리 손실없이 swap이 가능하다. (Python에서는 객체참조때문에 불가) 

</details>

---
## 알고리즘에서 알면 좋은 기술들 
<details markdown="1">
<summary>collecitons 모듈</summary>

<br><ul>
  <li> Counter 객체 
    <br>아이템에 대한 갯수를 계산해 Dictionary로 리턴한다.<br>
    a = [1,2,2,3,3,3,4,4,5]<br>
    b = collecitons.Counter(a)<br>
    print(b)<br>
    Counter({2: 2, 3: 3, 5: 1, 4: 2, 1: 1}) <br>
      
  <li> OrderedDict 객체<br>
    dictionary는 다른 언어에서 Hash Table에 해당되는데 3.6 이하 버젼에서는 
    <br>Python에서도 마찬가지로 입력 순서가 유지되지 않았다.
    <br>이를 위한 OrderedDict 객체를 이용하면 순서가 유지된 OrderedDict 객체를 반환한다.
    <br>collection.OrderedDict(dict) <br>
  
  <li> deque 객체 <br>
    python에서 스택이나 큐는 보통 list로 다 처리된다. 그러나 list.pop(0)의 시간복잡도는 O(n)으로 (뒤에 꺼를 앞으로 맞춰야함) 
    <br> pop(0)를 써야할 상황이면 차라리 deque로 활용하자 
    <br>queue = collecitons.deque()
    <br> 데크의 경우 list의 pop(0)함수를 deque.popleft()로 지원하며 연결리스트와 마찬가지로 시간복잡도는 O(1)이다.
</details>


<details markdown="1">
<summary>투포인터(+런너방식)</summary>

<br>
투포인터는 완전탐색에서 주로 쓰이는 기술로 주로 정렬되어있는 리스트에서 강력한 방법이다. <br><br>
<li> <b>런너방식</b><br>
  - 런너는 투포인트를 활용한 기술로 주로 연결리스트에서 사용된다.<br>
  - 두칸씩 순회하는 fast와 한칸씩 순회하는 slow를 동시에 출발시켜 fast가 순회를 끝내면 slow는 자동으로 
    <br>연결리스트의 중앙에 위치하게 된다. 이를 활용해 팬림드롬 등의 문자열 문제를 해결하기 쉽다.

</details>

<details markdown="1">
<summary>함수를 다루는 함수 functools</summary>

<br>
<pre>
functools.reduce() 함수는 두 인수의 함수를 누적적용하는 메쏘드이다. 
[1,2,3,4,5]의 리스트를 다 더하는 함수는 for문으로 쉽게 계산할 수 있지만 pythonic하게 풀어보려면
functools 모듈을 쓸 수 있다. import functools (Leetcode는 이미 되어있음) 후
functools.reduce(labmda x,y : x + y, [1,2,3,4,5])   
앞서 두인수를 누적적용한다 했으므로 [1,2,3,4,5]에 더하기 함수를 중복 적용하는 셈이다.
from operator import add 를 사용하면 굳이 람다로 구현하지 않고 
functools.reduce(add, [1,2,3,4,5])로 사용할 수 있다.
</pre>
</details>
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

