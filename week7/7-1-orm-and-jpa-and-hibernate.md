# 💡 7-1 ORM & JPA & Hibernate

## ✅ ORM & JPA

### 1️⃣ 정의

> #### JPA란 자바 ORM 기술에 대한 API 표준 명세를 의미한다.&#x20;
>
> #### JPA는 ORM을 사용하기 위한 인테페이스를 모아둔 것이며, JPA를 사용하기 위해서는 JPA를 구현한 Hibernate, EclipseLink, DatNucleus 같은 ORM 프레임워크를 사용해야 한다.

### 2️⃣ORM 정의 (Object-Relational Mapping)

#### ORM이란 객체와 데이터베이스의 테이블이 매핑을 이루는 것을 말한다. 즉, 객체가 테이블이 되도록 매핑 시켜주는 것을 말한다. ORM을 사용하면 SQL Query가 아닌 직관적인 코드로서 데이터를 조작할 수 있다.

<figure><img src="../.gitbook/assets/image (7).png" alt="" width="525"><figcaption></figcaption></figure>

### 2️⃣ JPA 정의

{% hint style="info" %}
#### <mark style="color:yellow;">JPA에 대해서는 따로</mark> <mark style="color:red;">Notion</mark><mark style="color:yellow;">에 정리를 해두었으니 참고하면 좋다.</mark>

[https://www.notion.so/JPA-0975ae1c77e3448e8543cb3c6781ef2f?pvs=4](https://www.notion.so/JPA-0975ae1c77e3448e8543cb3c6781ef2f?pvs=4)
{% endhint %}

* Java Persistence API로 자바 ORM기술에 대한 API 표준 명세이다.
* ORM을 사용하기 위한 인터페이스를 모아둔 것이다.
* 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다.

<figure><img src="../.gitbook/assets/image (9).png" alt="" width="563"><figcaption></figcaption></figure>

### 4️⃣ JPA 특징

* JPA는 애플리케이션과 JDBC 사이에서 동작한다.
* 개발자가 JPA를 사용하면 , JPA 내부에서 JDBC API를 사용하여 SQL을 호출하여 DB와 통신한다.
* 개발자가 직접 JDBC API를 사용할 필요가 없다.

## ✅ Hibernate

### 1️⃣ 정의

* Hibernate는 JPA라는 명세의 구현체이다.
* 영속성 엔티티매니저와 같은 인터페이스를 직접 구현한 라이브러리이다.
* JPA와 Hibernate는 마치 자바의 interface와 해당 interface를 구현한 클래스와 같은 관계이다.

### 2️⃣ 특징

* Hibernate의 작동 방식이 마음에 들지 않는다면 언제든지 DataNucleus, EclipseLink 등 다른 JPA 구현체를 사용해도 된다.

### 3️⃣ 구조

<figure><img src="../.gitbook/assets/image (10).png" alt="" width="563"><figcaption></figcaption></figure>

* 위와 같이 크게 SessionFactory, EntityManager, Transaction으로 구성되어있다.

> <mark style="color:red;">**참고사항**</mark>**: 먼저 Session 은 hibernate내에서 제공하는 api이고 EntityManger는 JPA의 표준화된 Api이다. 그래서 세션이 EntityManger가 Session을 wrap한다고 보면된다.**
