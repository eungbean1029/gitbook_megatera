# 💡 2-2 URI & MIME type

* 식별자(identifier)
* URI (Uniform Resource ID)
* URL -> Locator (리소스 위치) - 위치 변경에 취약
* URN -> Name (유니크한 이름)
* MIME Type (Content Type)
  * text/plain , text/html 등등..

### ✅ URI란?

<figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

* URI는 Uniform Resource Identifier 즉 통합 자원 식별자의 줄임말이다.
* URI는 인터넷의 자원을 식별할 수 있는 문자열을 의미한다.
* 그 중, URL이라는 URN이라는 하위 개념을 만들어서 특별히 어떤 표준을 지켜서 자원을 식별하는 것이다.



### ✅ URL이란?

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

* URL은 Uniform Resource Locator의 줄임말이다.
* URL은 네트워크 상에서 웹페이지, 이미지, 동영상 등의 파일이 위치한 정보를 나타낸다.
* URL은 웹 상의 주소를 나타내는 문자열이기 때문에 더 효율적으로 리소스에 접근하기 위한 방법론들이 생겼는데 REST API도 그 중 하나이다.

### ✅ URN이란?

* URN은 Uniform Resource Name의 줄임말이다.
* URI의 표준 포맷 중 하나로, 이름으로 리소스를 특정하는 URI이다.
* URN은 리소스를 영구적이고 유일하게 식별 할 수 있는 URI이다.

### ✅ URL / URN 차이점

* URL은 어떻게 리소스를 얻을 것이고 어디에서 가져와야하는지 명시하는 URI이다.
* URN은 리소스를 어떻게 접근할 것인지 명시하지 않고 경로와 리소스 자체를 특정하는 것을 목표로하는 URI이다.

### ✅ MIME TYPE (Multipurpose Internet Mail Extensions)

* MIME TYPE은 인터넷에서 전송되는 다양한 종류의 데이터를 식별하기 위한 형식을 말한다.
* 주로 웹 브라우저가 웹 서버로부터 받은 데이터를 해석할 때 사용된다.
* 바이너리 테이터를 ASCII 텍스트 형식으로 변환하기 위한 방법을 정의한다.

#### \[사용 이유]

* MIME을 사용하기 전에는 UUEncode 방식을 이요하고 있었는데 이 방식의 단점을 보강하여 새로운 인코딩 방식으로 등장하게 된 것이다.
  * 예를 들면, 바이너리 파일들을 시스템에서 문제 없이 전달하기 위해서 텍스트 파일로 변환이 필요한 경우가 있다.

{% hint style="info" %}
#### 텍스트 파일로 변환을 <mark style="color:blue;">인코딩(Encoding)</mark>이라고 하며, 텍스트 파일을 바이너리 파일로 변환하는 과정을&#x20;

#### <mark style="color:blue;">디코딩(Decoding)</mark>이라고 한다.
{% endhint %}

#### \[타입 알려주는 방식]

* MIME으로 인코딩 한 파일은 데이터의 종류를 알려주는 Content-Type 정보를 파일 앞부분에 담는다.
* 브라우저의 경우 -> 응답/요청시 HTTP 메시지의 헤더에 정보를 담아서 보내게 되는데 이 헤더에                   Content-Type  정보를 담아서 어떤 데이터 종류인지 명시한다.

### \[예시]

```
텍스트
text/plain, text/csv, text/html

영상 및 이미지
image/jpeg, image/png, image/svg+xml

멀티파트(다양한 데이터 타입을 한 번에 보내는 경우)
multipart/form-data, multipart/byteranges

```

### ✅ Content-Type

* Content-Type은 HTTP헤더에 존재하는 매개변수로 어떤 유형의 데이터가 전송되는지 웹 클라이언트 또는 웹 서버에 알리는 역할을 한다.
* 웹 클라이언트가 text/html을 요청하는 경우 웹 서버는 요청에 대한 응답에 content-Type:text/html 을 포함한다.
* MIME TYPE의 하위개념이다.



