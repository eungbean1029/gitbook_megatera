# 💡 4-1 Layered Architecture

## ✅ Layered Architecture

### 1️⃣ 정의

<figure><img src="../.gitbook/assets/image (4).png" alt="" width="563"><figcaption></figcaption></figure>

#### 계층화 아키텍쳐는 소프트웨어 개발에서 가장 일반적으로 널리 사용되는 아키텍펴이다.  그리고 구성되는 계층의 숫자에 따라 N계층 아키텍쳐라고도 한다.

### 2️⃣ 특징

* 기능은 웹과 분리 될 수 있다.
* 전자는 Business Logic이라고 하고, 후자는 UI라고 한다.
* 웹은 UI Layer에서 다루고 Spring Web MVC의 Controller로 구현된다.

> ### 계층의 구조
>
> 🔹 <mark style="color:yellow;">**Presentation Layer**</mark>** -> **<mark style="color:purple;">**View,**</mark> <mark style="color:purple;">**Controller**</mark>
>
> * 화면 계층은 화면에 보여주는 기술을 사용하는 영역이다.
> * 소프트웨어 시스템과의 사용자 상호 작용을 담당한다.
>
>
>
> 🔹 <mark style="color:yellow;">**Application/Business Layer**</mark>** -> **<mark style="color:purple;">**Service**</mark>
>
> * 비즈니스 계층은 기능의 요구사항 충족과 관련된 일을 처리 하는 도메인 계층이다.
> * 고객이 원하는 요구 사항을 반영하는 계층이므로 고객의 요구사항과 정확히 일치하도록 설계해야하며 메서드 이름은 고객들이 사용하는 용어를 사용하는 것이 좋다.
> * Control Layer와 Persistence Layer를 연결한다.
>
>
>
> 🔹 <mark style="color:yellow;">**Persistence Layer**</mark>** -> **<mark style="color:purple;">**DAO(Repository)**</mark>
>
> * 영속 계층 , 데이터 계층이라고 한다.
> * 어떤 방식으로 데이터를 보관 혹은 사용하는가에 대한 설계가 들어가는 계층이다.
> * 영구 데이터를 추출하여 객체화 시키며 , DB 같은 곳에 데이터를 저장, 수정, 삭제하는 계층이다.
> * ❗️Repository와 DAO는 거의 같다고 봐도 무방하지만,&#x20;
>   * **Repository -> 엔티티 객체를 보관하는 저장소**
>   * **DAO -> 데이터에 접근하도록 DB 접근 관련 로직을 모아둔 객체**
>
>
>
> 🔹 <mark style="color:yellow;">**Database Layer**</mark>** -> **<mark style="color:purple;">**VO**</mark>
>
> * 관계형 데이터베이스의 엔티티와 비슷한 개념을 가지는 것으로 데이터 객체를 뜻한다.





## ✅ Identifier

### 1️⃣ 정의

* 어떤 데이터를 식별하는데 사용하는 이름을 말한다
* 주로 ID와 같은 값들을 UUID, ULID, TSID와 같은 것으로 생성한다.



## ✅ UUID

### 1️⃣ 정의

#### Universally Unique Identifier의 약어이고 범용 고유 식별자라고 한다. 주로 분산 컴퓨팅 환경에서 사용되는 식별자이다.

### 2️⃣ 특징

* UUID는 128비트의 숫자이며, 32자리의 16진수로 표현한다.
* 여기에 8-4-4-4-12 글자마다 하이픈을 집어넣어 5개의 그룹으로 구분한다.
* 주로 세션 식별자, 쿠키 값, 무작위 데이터베이스 키 등에 사용이 된다.

> #### <mark style="color:yellow;">EX )</mark> 550e8400-e29b-41d4-a716-446655440000

### 3️⃣ 사용 예시

```java
String id = UUID.randomUUID().toString().replace("-", "");
```

## ✅ ULID

### 1️⃣ 정의

#### Universally Unique Lexicographically Sortable Identifier의 약자로 대소문자를 구별하지 않는 시간을 나타내는 26글자와 16글자의 임의의 값으로 구성되어있다.&#x20;

### 2️⃣ 특징

* ULID는 생성 순서를 밀리세컨 단위로 기록할 수 있어서, 생성 순서대로 정렬을 할 때 편하다.

### 3️⃣ 사용 예시

```java
String id = UlidCreator.getUlid().toString();
```

### ✔ Reference

{% embed url="https://velog.io/@mstar228/UUID%EB%9E%80" %}

{% embed url="https://velog.io/@injoon2019/UUID-vs-ULID" %}
