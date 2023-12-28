# 💡 3-2 Serialization

### ✅ Serialization (직렬화)&#x20;

* 어떤 환경의 데이터 구조를 다른 환경에 전송 및 저장하기 위해 나중에 재구성할 수 있는 바이트의 포맷으로 변환하는 과정을 뜻한다.
* 응용 프로그램에서 쓰는 데이터를 네트워크를 통해 전송하거나 DB 또는 파일에 저장 가능한 형식으로 바꾸는 프로세스이다/

{% hint style="info" %}
#### DeSerialization(역직렬화)

반대로, 일련의 바이트로부터 데이터 구조를 추출하는 일은 역직렬화라고 한다.
{% endhint %}

### ✅ 직렬화의 조건

* java.io.Serializable 인터페이스를 상속받은 객체는 직렬화 할 수 있다.

### ✅ JSON (JavaScript Object Notation)

* Douglas Crockford가 만든 데이터 포맷이다.
* 사람이 읽기 쉽고, 기계도 해석 또는 생성하기 쉽다.
* 기본적으로 key-value 쌍이다.
  * **생성 : DTO (Java 세계) -> 변환기 -> JSON 문자열**
  * **해석 : JSON 문자열 -> 변환기 ->  DTO (Java 세계)**
* 변환할 때에는 getter를 사용한다.
* <mark style="color:green;">**@JsonProperty**</mark>로 속성이름(key)를 지정 할 수 있다.
