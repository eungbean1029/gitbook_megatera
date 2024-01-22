# 💡 6-2 JDBC

## ✅ JDBC

### 1️⃣ 정의

#### JDBC는 Java 기반 애플리케이션의 데이터를 데이터베이스에 저장 및 업데이트하거나, 데이터베이스에 저장된 데이터를 Java에서 사용할 수 있도록 하는 자바 API이다.

### 2️⃣ 특징

* JDBC는 Java 애플리케이션에서 데이터베이스에 접근하기 위해 JDBC API를 사용하여 데이터베이스에 연동할 수 있다.
* 데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법을 제공한다.

<figure><img src="../.gitbook/assets/image.png" alt="" width="456"><figcaption></figcaption></figure>

> * **java.sql.Connection : 연결**
> * **java.sql.Statement : SQL을 담은 내용**
> * **java.sql.ResultSet : SQL 요청 응답**

### 3️⃣ 동작 흐름

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="563"><figcaption></figcaption></figure>

\-> JDBC는 Java 애플리케이션 내에서 JDBC API를 사용하여 데이터베이스에 접근하는 단순한 구조이다.

&#x20;   JDBC API를 사용하기 위해서는 JDBC 드라이버를 먼저 로딩한 후 데이터베이스와 연결하게 된다.

#### <mark style="color:yellow;">JDBC 드라이버</mark>

* 데이터베이스와의 통신을 담당하는 인터페이스이다.
* Oracle, MS SQL, MySQL 등과 같은 데이터베이스에 알맞은 JDBC 드라이버를 구현하여 제공한다.

#### 🔹 JDBC API 동작 흐름

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="413"><figcaption></figcaption></figure>

> 1. JDBC 드라이버 로딩 : 사용하고자 하는 JDBC 드라이버를 로딩한다. --> DriverManager 클래스를 통해 로딩된다.
> 2. Connection 객체 생성 : JDBC 드라이버가 정상적으로 로딩되면 DriverManager를 통해 데이터베이스와 연결되는 세션인 Connection 객체를 생성한다.
> 3. Statement 객체 생성 : Statement 객체는 작성된 SQL 쿼리문을 실행하기 위한 객체로 정적 SQL 쿼리 문자열을 입력으로 가진다.
> 4. Query 실행 : 생성된 Statement 객체를 이용하여 입력한 SQL 쿼리를 실행한다.
> 5. ResultSet 객체로부터 데이터 조회 : 실행된 SQL 쿼리문에 대할 결과 데이터 셋이다.
> 6. ResultSet, Statement, Connection 객체들의 Close : JDBC API를 통해 사용된 객체들은 생성된 객체들을 사용한 순서의 역순으로 Close한다.
