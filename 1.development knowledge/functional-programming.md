**함수형 프로그래밍**은 자료 처리를 수학적 함수의 계산으로 취급하고 <br/>
상태와 가변 데이터를 멀리하는 프로그래밍 패다임의 하나이다.

명령형 프로그래밍에서는 상태를 바꾸는 것을 강조하는 것과는 달리, 함수형 프로그래밍은 함수의 응용을 강조한다. <br/>
다수의 함수형 프로그래밍 언어들은 람다 연산을 발전시킨 것으로 볼 수 있다.

<hr/>

#### 함수형프로그래밍에서 함수의 특징

##### 고계 함수
> 함수를 다루는 함수를 뜻한다. 사실 함수형 언어에서는 함수도 '값(value)'으로 취급한다. 그러므로 정수 1이나 인수를 제곱하는 함수나 동등한 입장에서 다룰 수 있다. 정수를 함수의 인수로 전달할 수 있듯이 어떤 함수도 다른 함수의 인수로 전달할 수 있다. 마찬가지로 함수의 결과 값으로 정수를 반환할 수 있듯이 함수를 반환할 수도 있다.

##### 익명 함수 
> 익명 함수(anonymous function)란, 이름이 없는 함수를 뜻한다. 전통적인 명령형 언어에서는 모든 함수에 이름이 부여되어야만 한다.


##### 순수한 함수
> 순수한 함수(pure function)란, 부작용(side-effect)이 없는 함수, 즉, 함수의 실행이 외부에 영향을 끼치지 않는 함수를 뜻한다. 따라서 순수한 함수는 스레드 안전하고, 병렬적인 계산이 가능하다.


<hr/>

#### 함수형프로그래밍의 특징

1. 변경 가능한 상태를 불변상태(Immutab)로 만들어 SideEffect이 줄어든다.
2. 코드를 간결하게 하고 가독성을 높여 구현할 로직에 집중할 수 있다.
3. 동시성작업을 좀 더 쉽고 안전하게 구현할 수 있다.
4. 쓰레드 safe 하다.


<hr/>

#### 실전 예상 질문

1. 함수형프로그래밍을 쓰면서 어떤 이점을 얻을 수 있으셨나요?
```
   함수의 실행이 외부에 영향을 받지 않기때문에 외부인자변화에 따른 사이드이펙
   함수도 객체이기때문에 함수가 값으로 전달가능해 지면서, 그동안 사용중인 Java 진영 디자인패턴 대체가 가능
```
2. 함수형프로그래밍이 장점들이 많은데, 단점은 뭐가 있을까요?
```
   정말코어로직에서는 함수형보다는 속도가 더 빠른 절차형으로 구현하는게 더 좋을 수 있다.
```

3. for문 vs forEach(함수형) 속도차이, 무엇이 더 빠를까?
```
   속도는 단순 for문이 빠르다. 
   함수형에서는 input으로 받은인자로 새로운 값을 생성해서 가공후 리턴해주는 작업이 계속 반복된다.
   시간뿐만아니라 공간적으로도 단순 절차형 for문보다 자원소비가 많다.
   but, 요즘 장비가 좋아져 이러한 함수형사용으로 인한 속도/메모리 낭비측면보다 함수형사용으로 얻는 이점들이 훨씬 더 많다.
   또, 멀티코어 환경에서는 병렬처리로 들어가면 함수형프로그래밍이 병렬처리에 대한 구현부분 고민없이 바로 사용이 가능하기 때문에
   더욱 큰 이점을 갖는다.
```