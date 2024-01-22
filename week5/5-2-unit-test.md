# 💡 5-2 Unit Test

## ✅ Test Code

### 1️⃣ 정의

#### 테스트 코드는 소프트웨어의 기능과 동작을 테스트하는데 사용되는 코드이다.&#x20;

### 2️⃣ 특징

<figure><img src="../.gitbook/assets/image (4).png" alt="" width="375"><figcaption></figcaption></figure>

* 일반적으로 각 단계의 테스트 코드는 V 모델을 통해서 살펴 볼 수 있다.
* V모델은 소프트웨어 개발 생명 주기중 하나로, 시스템 개발 과정을 시각화한 모델이다.

### 1️⃣ 종류

* 단위 테스트(Unit Testing)
* 통합 테스트(Integration Testing)
* 시스템 테스트(System Testing

## ✅ TDD (테스트 주도 개발)

#### 테스트 케이스를 작성하고 소스코드가 이를 통과하는지 반복하여 확인하며 개발하는 것을 말한다. TDD는 기능의 구현 목표에 집중하여 개발 생산성을 높이고, 이후 리팩토링과 유지보수에 이점을 가져다준다.

## ✅ Unit Test

### 1️⃣ 정의

#### Unit Test는 프로그래밍을 할 떄 소스코드의 특정 모듈이 의도된 대로 정확히 작동하는지 검증하는 절차이다.  다시 말해 작성한 모든 메서드들에 대해서 테스트케이스를 작성하는 것을 의미한다.

### 2️⃣ 특징

* 하나의 기능을 독립적으로 테스트를 하며 코드 변경으로 인해 문제가 발생하여도 짧은 시간아네 해당 문제를 파악 할 수 있다.
* 리팩토링 시에 안정성을 확보할 수 있다.

## ✅ Unit Test Example

* Juit과 AssertJ 라이브러리를 많이 사용한다.

### 1️⃣ Unit Test 단계

1. given (준비) - 어떤 데이터가 준비되었을 때
2. when (실행) - 어떠한 함수를 실행하면 (조건을 지정)
3. then (검증) - 어떠한 결과 추출
4. verify - 메서드가 호출된 횟수, 타임아웃 시간 체크 검사

### 2️⃣ Example

```java
@Test
    void method1() {
        //given ( 멤버 생성 )이 주어졌을 때
        Member member = new Member(1L,"memberA",Grade.VIP);
        //when  ( 멤버를 회원가입 시킨 뒤, 멤버를 조회) 했을 때
        memberService.join(member);
        Member findMember = memberService.findMember(1L);
        //then   ( 아래 조건을 만족해야 한다. )
        Assertions.assertThat(member).isEqualTo(findMember);
    }
```

### 3️⃣ Annotaions

#### @Test

* 해당 메서드가 단위 테스트임을 명시하는 어노테이션이다.

#### @DisplayName("")

* 이 어노테이션 없이 실행하면 테스트 이름이 함수 이름이 default로 지정되는데, 지정해주면 읽기 좋은 다른 이름을 부여할 수 있다.

#### @BeforeEach, AfterEach

* 각 테스트 코드가 시작할 때, 끝날 때마다 동작하는 메서드
