# 💡 3-3 Jackson ObjectMapper

### ✅ ObjectMapper란?

* JSON 컨텐츠를 JAVA 객체로 deserialization 하거나 Java객체를 JSON으로 serialization 할 때 사용하는 Jackson 라이브러리의 클래스이다.

### ✅ ObjectMapper를 이용한 Serialize(직렬화)

* 객체로부터 JSON형테의 문자열을 만들어내는 것을 말한다.
* 주로 @ResponseBody, @RestController, @ResponseEntitiy등을 사용하는 경우에 처리된다.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

#### 아래와 같이 writeValueAsString 메서드가 사용된다.

```java
String jsonResult = objectMapper.writeValueAsString(myDTO());
```

* 객체로부터 JSON문자열을 만들기 위해서는 필드 값을 알아야한다.
* ObjectMapper의 기본 설정으로는 public필드 또는 public형태의 getter만 접근이 가능하다.



### ✅ ObjectMapper를 이용한 Deserialize(역직렬화)

* JSON문자열로부터 객체를 만들어내는 것을 말한다.
* Spring에서 @RequestBody로 JSON문자열을 객체로 받아올 때 역직렬화가 처리된다.
* 주로, <mark style="color:blue;">**기본 생성자로 객체를 생성**</mark>하거나 <mark style="color:blue;">**필드값을 찾아서 값을 바인딩**</mark> 해줄때 처리된다.

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

