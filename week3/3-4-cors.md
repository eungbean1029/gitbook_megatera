# 💡 3-4 CORS

### ✅ CORS란?

> 브라우저에서는 보안적인 이유로 cross-origin HTTP 요청들을 제한한다.&#x20;
>
> 그래서 cross-origin요청을 하려면 서버의 동의가 필요로한다. 만약 서버가 동의한다면 브라우저에서는 요청을 허락하고, 동의하지 않는다면 브라우저에서 거절하게 된다.

#### 즉, 위에서 말한 허락을 구하고 거절하는 메커니즘을 HTTP-header를 이용해서 가능한데 이를 <mark style="color:red;">CORS</mark>라고 한다.

* 출처가 다른 자원들을 공유한다는 뜻으로, 한 출처에 있는 자원에서 다른 출처에 있는 자원에 접근하도록 하는 개념이다.

{% hint style="info" %}
#### 출처란?

아래 구성요소 중에서 Protocol + Host + Port 3가지가 같으면 동일 출처(Origin)이라고 한다.

## ![](<../.gitbook/assets/image (3).png>)
{% endhint %}



### CROSS-ORIGIN 다른 경우

1. **프로토콜 다른 경우**
   1. &#x20;http 와 https는 프로토콜이 다릅니다.
2. **도메인 다른 경우**
   1. http://example.com
   2. http://www.example.com
3. **Port 번호가 다른 경우**
   1. http://example.com
   2. http://example.com:8080

<mark style="color:blue;">**아래와 같이 에러가 발생한다.**</mark>

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### ✅ CORS가 필요한 이유?

* CORS가 없이 모든 곳에서 데이터를 요청 할 수 있게 되면 , 다른 사이트에서 원래 사이트를 흉내 낼 수 있기 때문에 예를 들어 사용자가 로그인을 하고 그 로그인했던 세션을 탈취하여 악의적으로 정보를 추출할 수 도 있는 공격을 당할 수 있기 때문이다.



### ✅ CORS 기본 동작방식

1. 클라이언트에서 HTTP 요청 헤더에 Origin을 담아 전달한다.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt="" width="375"><figcaption></figcaption></figure>

2. 서버는 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달한다.
   1. 이후에 서버가 이 요청에 대한 응답을 할 떄 응답 헤더에 Access-Control-Allow-Origin이라는 필드를 추가하고 값으로 <mark style="color:orange;">**"이 리소스를 접근하는 것이 허용된 출처 url"**</mark>을 내려보낸다.
3. 클라이언트에서 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교한다.
   1. 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin과 서버가 보내준 응답의 Access-Control-Allow-Origin을 비교해본 후 차단할지 말지 결정한다.
   2. 만약 유효하지 않다면 그 앙답을 사용하지 않고 버린다. ==> <mark style="color:red;">**CORS 에러 발생**</mark>

> #### 즉, CORS의 해결책은 <mark style="color:blue;">서버의 허용</mark>이 필요하다.
>
> **서버에서 Access-Control-Allow-Origin 헤더에 허용할 출처를 기재해서 클라이언트에 응답하면 된다.**



### ✅ Spring Web MVC의 CORS 설정

1. <mark style="color:yellow;">**@CrossOrigin**</mark> Annotation 사용

```java
@CrossOrigin("http://localhost:3000")
```

2. Global Configuration 설정

```java
@Bean
public WebMvcConfigurer webMvcConfigurer() {
	return new WebMvcConfigurer() {
		
	@Override
	public void addCorsMappings(CorsRegistry registry) {
		registry.addMapping("/**")
			.allowedMethods("GET", "POST", "PATCH", "DELETE", "OPTIONS")
			.allowedOrigins("http://localhost:3000");
		}
	};
}
```



