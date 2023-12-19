---
description: REST API의 정의와 제약조건에 대해서 알아보자.
---

# 💡 2-1 REST API

### ✅ REST의 정의

* REST는 네트워크 아키텍처 원리의 모음을 말한다.  기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.
* 자원의 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미한다.

#### REST 구성요소

1. 자원(Resource) : HTTP URI
2. 자원에 대한 행위 : HTTP Method
3. 자원에 대한 행위의 내용 : HTTP Message Pay Load

### ✅ REST API

(Representational State Transfer API)

* REST 아키텍처 스타일의 디자인 원칙을 준수하는 API이다.
* 즉, RESTful API라고도 불린다.

### ✅ 정보은닉 (OOP의 핵심)

* 객체지향 언어적 요소를 활용하여 객체에 대한 구체적인 정보를 노출시키지 않도록 하는 기법이다.
* 주의 ) 캡슐화 == 정보은닉 은 아니다!!

### ✅ 캡슐화

* 정보들을 캡슐로 감싸서 안보이게 하는 정보은닉 개념 중 하나이다.
* 캡슐화는 코드나 api등을 단순하게 하고 재사용성을 높인다.
* **객체의 필드 및 메소드를 은닉**하는 것이 정보은닉과의 차이점이다.

### ✅ REST API 제약 조건

* Client-Server
* Stateless
* cache
* uniform interface
* layered system
* code-on-demad

### ☑️ Client - Server

* 클라이언트와 서버가 서로 의존하지 않고 별도로 진화할 수 있다.
  * 왜냐하면 , 클라이언트는 서버의 리소스 URI만 알고있으면 되기 때문이다.

### ☑️ Stateless

* 클라이언트에서 서버로의 각 요청에는 그 요청을 이해하는 데 필요한 모든 정보가 포함되어야 한다.
  * 예를 들면 , 로그인했다는 세션 유지가 필요하다면 그 정보 또한 Client가 해당 정보를 가지고 서버에 전달해줘야 한다.

### ☑️ Cacheable

* 요청에 대한 응답 내의 데이터에 해당 요청은 캐시가 가능한지 불가능 한지 명시해줘야 한다.
  * 응답을 캐시 할 수 있다면 클라이언트에서 동일한 요청이 왔을 때 응답 데이터를 재사용할 수 있어야 한다.

### ☑️ ⭐️ Uniform Interface

* 전체적인 시스템 아키텍처를 간단하고 잘 파악할 수 있도록 하기 위한 약속된 Interface이다.
  * **해당 규약을 REST 사용자들이 지킴으로써 추후에 사용하는 Client를 개발하는 사용자와 Server를 개발하는 사용자 간의 결합도가 낮아질 수 있다.**
* Uniform Interface가 잘 지켜지는지는 되돌아 볼 필요가 있다.

#### <mark style="color:yellow;">🌟 Uniform Interface 제약조건 🌟</mark>

* <mark style="color:blue;">**identification of resources**</mark>
  * 리소스가 URI로 식별되면 된다. (이 조건은 주로 잘 지켜진다.)
  * 각 URL이 단일 리소스에 매칭되어야 하며 이 리소스에 대한 모든 액세스는 해당 URL을 통해 수행된다.



* <mark style="color:blue;">**manipulation of resources thorough representations (표현을 통한 자원 조작)**</mark>
  * 특정 리소스를 나타내는 URL을 바꾸지 않고도 표현을 활용해서 리소스를 조작할 수 있다.
    * RESTful 애플리케이션은 동일한 URI에서 동일한 리소스의 두개 이상의 표현을 지원할 수 있다.
    * HTTP 메서드인 GET,POST,DELETE,PUT 등을 활용해서 리소스를 조작할 수 있다.



*   <mark style="color:blue;">**self-descriptive message**</mark>

    * 요청 , 응답과 같은 메시지는 메시지 그 자체만 보고 무슨 의미인지 파악 할 수 있을 정도로 정보가 담겨있어야 한다.
    * RESTful 시스템에서 제공하는 표현에는 클라이언트가 리소스를 이해하고 조치를 취하는 데 필요한 모든 데이터가 포함되어야 한다.
      * 추가 정보가 필요하지만 응답에 포함되지 않은 경우에는 , 해당 추가 정보를 가지고 있는 링크가 응답에 제공되어야한다.

    **\[예시]**
* <mark style="color:red;">**올바르지 않은 예시**</mark>

```
  GET / HTTP/1.1
```

```
  HTTP/1.1 200 OK
  [ { "op": "remove", "path": "/a/b/c" } ]
```

* <mark style="color:green;">**올바른 예시**</mark>

```
  GET / HTTP/1.1
  **Host: www.example.org**
```



*   <mark style="color:blue;">**HATEOAS**</mark>

    *   애플리케이션의 상태가 HyperLink를 이용해 전이되어야 한다. (거의 대부분 잘 안 지켜진다.)

        * 어디서 어디로 전이가 가능한지 미리 결정되지 않는다.
        * 어떤 상태로 전이가 완료되고 나서야 그 다음 전이 될 수 있는 상태가 결정된다. 쉽게 말해서 링크는 동적으로 변경될 수 있다.



    **\[HATEOAS의 장점]**

    * 요청 URI가 변경되더라도 클라이언트에서 동적으로 생성된 URI를 사용함으로써, 클라이언트가 URI 수정에 따른 코드를 변경하지 않아도 되는 편리함을 제공한다.
    * URI 정보를 통해 들어오는 요청을 예측할 수 있다.

&#x20;     \[예시]

* 게시글을 조회하는 URI가 있다고 가정해보겠다.

```
GET https://my-server.com/article
```

여기서 해당 글을 조회한 사용자는 다음 행동으로 어떤 행동을 하게 될까?

* 다음 게시글 조회 / 게시물을 내 피드에 저장 / 댓글 달기

\=> 이런 행동들이 상태 전이가 가능한 것들인데, 이 것들을 응답 본문에 넣어줘야 한다.

```json
{
  "data": {
    "id": 1000,
    "name": "게시글 1",
    "content": "HAL JSON을 이용한 예시 JSON",
    "self": "http://localhost:8080/api/article/1000", // 현재 api 주소
    "profile": "http://localhost:8080/docs#query-article", // 해당 api의 문서
    "next": "http://localhost:8080/api/article/1001", // 다음 article을 조회하는 URI
    "comment": "http://localhost:8080/api/article/comment", // article의 댓글 달기
    "save": "http://localhost:8080/api/feed/article/1000", // article을 내 피드로 저장
  },
}
```



### ☑️ **Layered System**

* 기존 HTTP만 사용해도 잘 지켜진다.



### ☑️ **Code on Demand (Optional)**

* 서버에서 코드를 클라이언트로 보내서 실행할 수 있어야한다.
