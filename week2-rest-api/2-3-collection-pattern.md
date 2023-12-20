# 💡 2-3 Collection Pattern

### ✅ Collection

* 문서,객테들의 집합이라고 볼 수 있다.
* 복수를 의미한다.
* 리소스라고 표현할 수 있으며 URI에 표현된다.
* <mark style="color:yellow;">ex) /members , /posts</mark>

### Collection Pattern을 쓰지 않은 경우

* /the-first-post
* /the-post

### Collection Pattern을 쓴 경우

* /posts
* /posts/the-first
* /posts/{id} , /posts/:id

### ✅ HTTP METHOD

* GET : 리소스를 조회한다.
* POST : 새로운 데이터를 서버에 보낸다.
* PUT/PATCH : 기존 데이터를 업데이트한다.
* DELETE : 데이터를 삭제한다.

### \[Example]

* <mark style="color:yellow;">**GET/books**</mark> - 책 목록 조회
* <mark style="color:yellow;">**POST /books**</mark> - 새 책 추가
* <mark style="color:yellow;">**PUT /books/:id**</mark> - 지정된 id로 전체 책 데이터 업데이트
* <mark style="color:yellow;">**PATCH /books/:id**</mark> - 책의 부분적인 변경 사항을 업데이트
* <mark style="color:yellow;">**DELETE /books/:id**</mark> - 지정된 id의 리소스 삭제



### ✅ CQS

* CQS는 디자인 패턴 중 하나이다.
* Command와 Query를 분리하자는 개념을 의미한다.
  * Command : 상태를 변경하는 메서드
  * Query : 상태를 반환하는 메서드
  *
* 객체의 모든 메서드를 Command와 Query 두가지로 구분한다.

#### \[CQS의 장점]

* 조회 , 수정 로직을 분리한다.
  * 이를 통해 성능 최적화, 유지 보수에 도움이 된다.





