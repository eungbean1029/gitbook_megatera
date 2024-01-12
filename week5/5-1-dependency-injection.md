# 💡 5-1 Dependency Injection

## ✅ Factory

### 1️⃣ 정의

> #### 객체 생성을 처리하는 방법을 추상화하여, 클라이언트 코드에서 구체적인 클래스의 인스턴스 생성을 캡슐화하는 데 사용된다.&#x20;

간단히 요약하면, 생성할 객체에 대한 구체적인 정보를 추상화 해놓고 이를 overriding한 서브 클래스에서 어떤 class의 객체인지를 명시하고 해당 객체를 반환해서 사용하는 패턴을 말한다.

\-> Client 측에서 객체의 class에 대해 명시적으로 알 필요가 없으며 interface를 통해 객체를 생성, 사용할 수 있다.



### 2️⃣ Example

### <mark style="color:purple;">Student interface</mark>

학생의 정보와 학생이 갖고있는 기능에 대해서 명시한 Interface

```java
public interface Student {
    void enroll();
}
```

### <mark style="color:purple;">Student 구현체</mark>

각각 학생을 상속받아 구현된 구현체이다.

```java
public class InhaStudent implements Student {
    @Override
    public void enroll() {
        System.out.println("인하대학교 학생입니다.");
    }
}

public class SeoulStudent implements Student {
    @Override
    public void enroll() {
        System.out.println("서울대학교 학생입니다.");
    }
}
```

### <mark style="color:purple;">StudentFactory Abstract Class</mark>

학생을 생성하고 학교에 등록시켜서 해당 학생을 반환한다.

```java
public abstract class StudentFactory {
    public Student newInstance() {
        Student student = createStudent();
        student.enroll();
        return student;
    }
    protected abstract Student createStudent();
}
```

### <mark style="color:purple;">StudentFactory 구현체</mark>

```java
public class InhaStudentFactory extends StudentFactory {
    @Override
    protected Student createStudent() {
        return new InhaStudent();
    }
}

public class SeoulStudentFactory extends StudentFactory {
    @Override
    protected Student createStudent() {
        return new SeoulStudent();
    }
}
```

### <mark style="color:purple;">Client</mark>

```java
// 어떤 학교에 학생을 등록할지 모름
StudentFactory studentFactory = new InhaStudentFactory();
//StudentFactory studentFactory = new SeoulStudentFactory(); // 다른 학생 팩토리도 생성가능
        
// 학생 팩토리에서 생성한 학생, client는 어떤 학교에 학생이 등록되는지 모름.
Student student = studentFactory.newInstance();
```



## ✅ IOC (Inversion of Control)

### 1️⃣ IOC 정의

#### IOC란 객체의 생성, 생명주기의 관리까지 모든 객체에 대한 제어권이 바뀌었다는 것을 말한다.

### 2️⃣ IOC Container 정의

#### 스프링 프레임워크도 객체에 대한 생성 및 생명주기를 관리할 수 있는 기능을 제공한다. 즉, IOC 컨테이너 기능을 제공한다.

### 2️⃣-1️⃣ 특징

* IOC 컨테이너는 객체의 생성을 책임지고, 의존성을 관리한다.
* POJO의 생성, 초기화, 서비스, 소멸에 대한 권한을 가진다.

{% hint style="info" %}
### POJO란?

Plain Old Java Object, 간단히 POJO는 말 그대로 해석을 하면 오래된 방식의 간단한 자바 오브젝트라는 말로서 Java EE 등의 중량 프레임워크들을 사용하게 되면서 해당 프레임워크에 종속된 "무거운" 객체를 만들게 된 것에 반발해서 사용되게 된 용어이다.
{% endhint %}

### 3️⃣ IOC 분류

1. **DL**
   * 저장소에 저장되어 있는 Bean에 접근하기 위해 컨테이너가 제공하는 API를 이용하여 Bean을 LookUp하는 것을 말한다.
2. **DI**
   * 각 틀래스간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것을 말한다.
     1. <mark style="color:yellow;">**Setter Injection**</mark>
     2. <mark style="color:yellow;">**Constructor Injection**</mark>
     3. <mark style="color:yellow;">**Method Injection**</mark>

## ✅ DI (Dependency Injection)

### 1️⃣ DI 정의

#### 각 클래스간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것을 말한다.

* 개발자들은 단지 빈 설정파일에서 의존관계가 필요하다는 정보를 추가하면 된다.
* 객체 레퍼런스를 컨테이너로부터 주입 받아서, 실행 시에 동적으로 의존관계가 생성된다.
* 컨테이너가 흐름의 주체가 되어 애플리케이션 코드에 의존관계를 주입해 주는 것이다.

### 2️⃣ DI 유형

1. <mark style="color:yellow;">**Setter Injection (Setter 메서드를 이용한 의존성 삽입)**</mark>
   1. 의존성을 입력 받는 setter 메서드를 만들고 이를 통해 의존성을 주입한다.
2. <mark style="color:yellow;">**Constructor Injection (생성자를 이용한 의존성 삽입)**</mark>
   1. 필요한 의존성을 포함하는 클래스의 생성자를 만들고 이를 통해 의존성을 주입한다.
3. <mark style="color:yellow;">**Method Injection (일반 메서드를 이용한 의존성 삽입)**</mark>
   1. 의존성을 입력 받는 일반 메서드를 만들고 이를 통해 의존성을 주입한다.

### 3️⃣ DI Example

> #### ⭐️ 스프링 빈으로 등록하면 싱글톤 패턴으로 해당 객체를 관리하도록 할 수 있게 하고, 빈으로 등록된 객체에 한해 아주 쉽게 의존성을 주입할 수 있는 방법을 제공한다. ⭐️

```java
@Component
public class Car {

    private String name;

    private Company company;

    public Car() {
    }

    public Car(String name, Company company) {
        this.name = name;
        this.company = company;
    }
  ...
}

@Configuration
@ComponentScan(basePackageClasses = Car.class)
public class AppConfig {
    @Bean
    public Company getCompany() {
        return new Company("BMW");
    }
}

```

### 4️⃣ 의존성 주입 방법

#### 1. 필드 주입

```java
@Service
public class UserService {

    @Autowired 
    private UserRepository userRepository;
    
}
```

#### 2. Setter Method 기반 의존성 주입

```java
@Service
public class UserService {

    private UserRepository userRepository;

    @Autowired
    public void setUserRepository(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

}
```

* setter 기반 의존성 주입은 주로 optional 하게 의존성 주입을 해주어야 할 경우 사용한다.
* 의존 대상 객체가 null이어도 서비스 구동에 문제가 없기 때문에, 런타입에 NullPointException이 발생 할 수 있다.

#### 3. 생성자 기반 의존성 주입

#### ⭐️ 스프링은 생성자 기반 의존성 주입을 더 추천한다.  그 이유는 Bean 때문이다.

* 의존 객체를 불변 객체로 생성 가능 <mark style="color:green;">**(final 객체)**</mark>
* 순환 참조 사전 감지
* 의존 객체 <mark style="color:red;">**NullPointException**</mark> 방지

```java
@Service
public class UserService {

    private UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```
