# 💡 7-2 Embedable

## ✅ @Embedded, @Embeddable

### 임베디드 타입

### 1️⃣ 정의

#### 임베디드 타입은 복합 값 타입으로 불리며 새로운 값 타입을 직접 정의해서 사용하는 JPA 방법을 의미한다.

### 2️⃣ 특징

* 임베디드 타입을 적용하려면 새로은 Class를 만들고 해당 클래스에 임베디드 타입으로 묶으려던 Attribute들을 넣어준 뒤 @Embedable를 붙여줘야한다.
* <mark style="color:orange;">**사용 방법**</mark>
  * `@Embeddable` : 값 타입을 정의하는 곳에 표시
  * `@Embedded` : 값 타입을 사용하는 곳에 표시

```java
// user.java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @NonNull
    private String name;

    @NonNull
    private String email;


    @Enumerated(value = EnumType.STRING)
    private Gender gender;
    
    @Embedded
    private Address address;

}
```



## ✅ @AttributeOverride : 속성명 재정의

### 1️⃣ 특징

* 같은 종류의 Attribute에 대해서 중복된 코드를 적을 필요 없이 간단하고 직관성있게 선언 가능하다.
* 예시로는 회사의 주소, 집 주소의 주소 형태는 시, 구, 상세주소, 우편번호로 동일하다. 이러한 경우 @Embedded와 `@AttributeOverrides`, `@AttributeOverride`를 통해 하나의 class를 사용해 여러 표현을 할 수 있습니다. (객체의 재활용)

### 🚨 주의할 점

* 아래 코드와 같이 하나의 class를 통해 여러개의 정보를 만들고 싶은데 위와 같이 `@AttributeOverrides`, `@AttributeOverride`를 통해 column명을 재정의해주지 않으면 아래와 같이 Repeated column in mapping for entity 에러가 나오니 꼭 column명을 재정의해줘서 사용해야한다.

```java
@Entity
public class User {

.....

    @Embedded
    @AttributeOverrides({
            @AttributeOverride(name = "city", column = @Column(name = "home_city")), // city를 home_city라는 column명으로 사용
            @AttributeOverride(name = "district", column = @Column(name = "home_district")),
            @AttributeOverride(name = "detail", column = @Column(name = "home_address_detail")),
            @AttributeOverride(name = "zipCode", column = @Column(name = "home_zipCode"))
    })
    private Address homeAddress;

    @Embedded
    @AttributeOverrides({
            @AttributeOverride(name = "city", column = @Column(name = "company_city")),
            @AttributeOverride(name = "district", column = @Column(name = "company_district")),
            @AttributeOverride(name = "detail", column = @Column(name = "company_address_detail")),
            @AttributeOverride(name = "zipCode", column = @Column(name = "company_zipCode"))
    })
    private Address companyAddress;
   
   	.....
}
```
