# 💡 1-2 HTTP Client / Server

### TCP/IP 통신

* 인터넷 프로토콜 스위트(Internet Protocol Suite)는 인터넷에서 컴퓨터들이 서로 정보를 주고받을 때 쓰는 프로토콜의 모음이다.
  * 그 중에서, TCP와 IP가 가장 많이 쓰인다.
* TCP/IP는 패킷 통신 방식의 인터넷 프로토콜인 IP와 전송 조절 프로토콜인 TCP로 이루어져있다.

{% hint style="info" %}
#### TCP/IP를 말한다?

송신자가 수신자에게 IP주소를 사용하여 데이터를 전달하고 그 데이터가 제대로 갔는지, 너무 빠르지는 않는지, 제대로 받았다고 응답이 오는지에 대한 이야기를 하는 것이다.
{% endhint %}

### Socket(소켓)

* 소켓은 네트워크 상에서 돌아가는 두 개의 프로그램 간 양방향 통신의 하나의 엔드 포인트를 말한다.
* 일반적으로, 파일(file)이라고 생각하면 이해하기 쉽다.

{% hint style="info" %}
#### 엔드 포인트란?

아이피 주소와 포트 번호의 조합을 의미한다. 모든 TCP 연결은 2개의 엔트 포인트로 유일하게 식별되어질 수 있다.
{% endhint %}

> ### **소켓 종류**

#### TCP(스트림)

* 데이터 전달 보증 및 순서 보장한다.
* 연결 지향성이다.
* 소량 데이터보다 대량의 데이터 전송에 적합하다.

#### UDP(데이터그램)

* 데이터 전달 및 순서를 보장하지 않는다.
* 비연결형 소켓이다.
* 데이터의 크기에 제한이 있다.



### Socket 통신

* 일반적으로 서버는 특정 포트가 바인딩된 소켓을 가지고 특정 컴퓨터 위에서 돌아간다.
* 즉, 해당 서버는 클라이언트의 연결 요청을 소켓을 통해 리스닝하면서 기다린다.

### TCP 통신 순서

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Server(서버)

* 클라이언트 소켓의 연결 요청을 대기하고, 연결 요청이 오면 클라이언트 소켓을 생성하여 통신이 가능하게 한다.

#### Client(클라이언트)

* 실제로 데이터 송수신이 일어나는 것은 클라이언트 소켓이다.

STEP1 (<mark style="color:red;">서버</mark>) : 클라이언트의 요청을 받기 위한 준비를 한다.&#x20;

STEP2(<mark style="color:blue;">클라이언트</mark>) - Socket : 서버에 접속 요청을 한다.&#x20;

STEP3(<mark style="color:red;">서버</mark>) - accept : 클라이언트의 요청을 받아 들인다.&#x20;

STEP4(<mark style="color:blue;">클라이어트</mark>) - BufferedWriter : 서버에 메시지를 보낸다.&#x20;

STEP5(<mark style="color:red;">서버</mark>) - BufferedReader : 클라이언트가 보낸 데이터를 출력한다.

STEP6(<mark style="color:red;">서버</mark>) - BufferedWriter: 클라이언트에 메시지를 보낸다.

STEP7(<mark style="color:blue;">클라이언트</mark>) - BufferedReader: 서버가 보낸 메시지를 출력한다.&#x20;

STEP8(<mark style="color:red;">서버</mark>,<mark style="color:blue;">클라이언트</mark>) - socket.close() : 종료한다.&#x20;

###

## 🌟 Client 소켓 구현하기

### 1. Connect

* 호스트는 IP 또는 도메인 이름을 사용할 수 있다.

```
String host = "example.eungbean";
```

```
int port = 80;
```

* IP 주소와 포트 번호로 서버에 접속한다.

```
Socket socket = new Socket(host , port);
```



### 2. Request

* 요청 메시지를 만들고 , TCP로 전송한다.
  * 단 , 마지막에 빈줄을 넣는 걸 잊지말아야한다.

```java
GET http://example.com/ HTTP/1.1
(빈 줄)
```

```java
GET / HTTP/1.1
Host: example.com
(빈 줄)
```

#### 예시

```java
String message = """
	GET / HTTP/1.1
	Host: example.com

	""";
	
또는

String message = "" +
	"GET / HTTP/1.1\n" +
	"Host: example.com\n" +
	"\n";
```

* 소켓에서 Output Stream을 얻어서 사용한다.

```java
OutputStream outputStream = socket.getOutputStream();
outputStream.write(message.getBytes());
```

* 만약, 문자열을 직접 전송하고 싶다면 Writer을 사용하는 것을 추천한다.

<mark style="color:red;">!! 주의 !!</mark> 내부적으로 버퍼가 있기 때문에 flush을 얻어서 쓸 수 있다.

```java
OutputStreamWriter writer = new OutputStreamWriter(socket.getOutputStream());

writer.write(message);
writer.flush();
```

### 3. Response

* 소켓에서 Input Stream을 얻어서 사용 할 수 있다.

```java
InputStream inputStream = socket.getInputStream();
```

*   Byte 배열로 데이터를 읽어온다.

    * 만약, 응답 데이터가 준비한 배열보다 클 경우에는 반복해서 여러번 읽는 작업을 수행해줘야 한다.

    &#x20;      이 경우엔 준비한 배열이 Chunk(한번에 처리하는 단위)가 된다.

```java
byte[] bytes = new byte[1_000_000];
int size = inputStream.read(bytes);
```

* 실제 응답 데이터 크기만큼 Byte 배열을 자르고, 문자열로 변환해 출력한다.

```java
byte[] data = Arrays.copyOf(bytes, size);
String text = new String(data);

System.out.println(text);
```

* 요청과 마찬가지로 Reder를 사용하는 것을 추천한다.

<mark style="color:red;">!! 주의 !!</mark> CharBuffer에서 읽기 전에 flip을 잊지 않아야 한다.

```java
InputStreamReader reader = new InputStreamReader(socket.getInputStream());

CharBuffer charBuffer = CharBuffer.allocate(1_000_000);

reader.read(charBuffer);

charBuffer.flip();

System.out.println(charBuffer.toString());
```

### 4. Clear

* 마지막으로, 소켓을 종료한다.

```java
socket.close();
```



## 🌟 Server 소켓 구현하기

### 1. Listen

* 다른 곳에 접속하는 게 아니라 포트 번호만 정하면 된다.

```java
int port = 8080;
```

* JAVA에서는 ServerSocket이라는 별도 클래스를 사용한다.

```java
ServerSocket listener = new ServerSocket(port);
```

* 클라이언트의 접속을 기다리고 클라이언트가 접속하면 통신용 소켓을 따로 만들어서 돌려준다.
* I/O에서 클라이언트를 기다리는 것을 BLOCKING이라고 한다.
  * TCP통신에서는 네트워크 상태 같은 요인에 의해 크게 지연될 수 있다.
  * 또는 , accept처럼 상대방의 요청이 없으면 영원히 기다리는 일이 발생 할 수 있다.

```java
Socket socket = listener.accept();
```

## 2. Request

* 서버는 요청을 하는게 아니라 , 받는 것이기에 먼저 읽어야 한다.  코드는 위에서 작성한 것이랑 동일하다.

## 3. Response&#x20;

* 클라이언트 요청과 마찬가지로, 응답 메시지를 만들어서 전송한다.
  * 서버 또한 마지막 줄에 "\n"을 잊지말아야 한다.

```java
String message = """
	HTTP/1.1 200 OK
	
	Hello, world!
	""";
	
또는

String message = "" +
	"HTTP/1.1 200 OK\n" +
	"\n" +
	"Hello, world!\n";
```

* Content-Type과 Content-Length를 추가해주는 것이 좋다.

```java
String body = "Hello, world!";
byte[] bytes = body.getBytes();
String message = "" +
	"HTTP/1.1 200 OK\n" +
	"Content-Type: text/html; charset=UTF-8\n" +
	"Content-Length: " + bytes.length + "\n" +
	"\n" +
	body;
```

***

> #### 다음 1-3 Java HTTP Server에서는 직접 작성해 전체코드 설명으로 정리해보겠다.
