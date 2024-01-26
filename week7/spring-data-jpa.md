# 💡 Spring Data JPA

## ✅ Spring Data JPA

### 1️⃣ 정의

* JPA에서 Repository를 제작할 때마다 반복적으로 작성되는 CRUD 메서드가 존재한다.
* 이처럼 반복 작성되는 메서드를 자동화하여 기본적인 CRUD메서드를 제공하는 라이브러리다.

<figure><img src="../.gitbook/assets/image (12).png" alt="" width="563"><figcaption></figcaption></figure>

### 2️⃣ 사용 방법

1. 사용할 Repository를 인터페이스로 선언하고 다음과 같이 JpaRepository를 상속받는다.

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface DataJpaRepository extends JpaRepository<Type, Id> {}
```

> #### <mark style="color:yellow;">Type</mark> : 사용할 Repository의 기준이 되는 Entity의 이름을 기입한다.
>
> #### <mark style="color:yellow;">ID</mark> : 기입된 Entity의 PK 자료형을 기입한다.

* JpaRepository 안에는 일반적으로 개발자가 생각할 수 있는 기본적인 CRUD 기능은 모두 있다.
* 자동적으로 Entity를 관리하는데 필요한 메서드를 Spring Data JPA에서 알아서 제공해준다

2. 메서드 선언

* Spring Data JPA는 알아서 구현체를 만들어준다.
* 메서드 이름을 작명하는 규칙이 있어서 메서드 이름을 기반으로 메서드의 구현체를 알아서 만들어준다.

```java
# 예를 들어, findByUserNmae() 이라는 메서드를 선언하려고한다.
public interface OrderRepository extends JpaRepository<Order, Long> {

   List<Order> findByUserName(String userName);

}
```

