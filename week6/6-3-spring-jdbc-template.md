# 💡 6-3 Spring JDBC Template

## ✅ JDBC Template

### 1️⃣ 정의

#### JDBC Template은 JDBC 코어 패키지의 중앙 클래스로 JDBC의 사용을 단순화하고 일반적인 오류를 방지하는데 도움이 된다. 개발자가 JDBC를 직접 사용할 때 발생하는 다음과 같은 반복 작업을 대신 처리해준다.

* 커넥션 획득
* Statement를 준비하고 실행
*  결과를 반복하도록 루프 실행
* 커넥션 종료, Statement 및 resultSet 종료

### 2️⃣ JDBC Template 사용법

1. JDBC Template 설정

```gradle
//JdbcTemplate 추가
implementation 'org.springframework.boot:spring-boot-starter-jdbc'
```

2. DataSource 주입

```java
private final JdbcTemplate jdbcTemplate;

public JdbcTemplateItemRepository(DataSource dataSource) {
	this.jdbcTemplate = new JdbcTemplate(dataSource);
}
```

3. 쿼리 작성 및 실행

```java
@Override
public void run(String... args) throws Exception {
	String sql = "SELECT name FROM people";
		
	jdbcTemplate.query(sql, resultSet -> {
		while (resultSet.next()) {
			String name = resultSet.getString("name");
			System.out.println(name);
		}
	});
}
```
