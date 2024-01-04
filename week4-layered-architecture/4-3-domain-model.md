# 💡 4-3 Domain Model

## ✅ DDD (Domain Driven Design)

#### :checkered\_flag: **핵심 목표**:checkered\_flag:

**"High Cohesion", "Loosly Coupling"으로 각각의 도메인은 서로 철저히 분리되고, 높은 응집력과 낮은 결합도로 변경과 확장에 용이한 설계를 얻는다.**

### 1️⃣ 정의

#### DDD(Domain Driven Design) 또는 도메인 주도 설계라고 부른다.  도메인 패턴을 중심에 놓고 설계하는 방식을 말한다.

* 데이터 중심의 접근법을 탈피해서 순수한 도메인의 모델과 로직에 집중하는 것을 말한다.

> #### <mark style="color:purple;">데이터 중심의 접근법</mark>
>
> 데이터에 초점을 두고 설계를 하는 방식을 말한다. 데이터 주도 설계에서는 객체 자신이 포함하고 있는 데이터를 조작하는데 필요한 행동들을 정의한다.



## ✅ Application Layer

### 1️⃣ 정의

* 비즈니스 로직을 정의하고 정상적으로 수행 될 수 있도록 도메인 계층과 인프라스트럭쳐 계층을 연결해주는 역할을 한다.
* 이 계층은 얇게 유지되며, 많은 정보를 가지고 있지 않게 유지하는 것이 중요하다.

### 2️⃣ 포함 기능

* 트랜잭션 단위
* DTO 변환
* 엔티티 조회/저장
* 사용자 인증/인가
* 파라미터 검증



### ✅ Domain Layer

### 1️⃣ 정의

#### 특정 도메인을 개념적으로 표현한 것으로, 도메인 모델을 사용하면 여러 관계자들이 동일한 모습으로 도메인을 이해하고 도메인 지식을 공유하는데 도움이 된다.

### 2️⃣ 특징

* 무엇보다 "행위"가 가장 중요하다.
* Unit Testing 하기에 적합하다.
* 시스템이 제공할 도메인 규칙 즉 기능을 구현한다.
* 서비스의 책임들이 도메인으로 분산되기 때문에 서비스의 메서드는 단순해진다.

{% hint style="info" %}
#### Domain Model은 쉽게 설명하자면 내가 알게 뭐야라는 마인드로 행위를 위임한다고 보면 된다. 즉 그 행위를 올바르게 하고 있는지 검증하기 위해서는 Unit Testing을 수행해주면 된다.
{% endhint %}

### 3️⃣ Reference

{% embed url="https://incheol-jung.gitbook.io/docs/q-and-a/architecture/ddd" %}

{% embed url="https://dev-coco.tistory.com/166" %}
