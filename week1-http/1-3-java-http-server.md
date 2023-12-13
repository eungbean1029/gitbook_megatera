# 💡 1-3 Java HTTP Server

{% hint style="info" %}
#### 해당 정리는 코드의 주석으로 정리해보았으니 , 주석을 참고하길 바란다.
{% endhint %}

> ### App.java

```java
public class App {
    public static void main(String[] args) throws IOException {
        App app = new App();
        app.run();
    }

    private void run() throws IOException {
        //서버 생성
        InetSocketAddress address = new InetSocketAddress(8080);
        HttpServer httpServer = HttpServer.create(address , 0);
        System.out.println("Listening on port " + address + " ...");

        //예시 1) "/" 호출
        //추가 알아두기 : 인터페이스인테 메서드 1개 -> 람다식으로 구현
        httpServer.createContext("/", exchange -> {
            //1. Request 매서드 호출
            request(exchange);
            //2. Response Body 작성
            String content = "Hello, world!\n My name is Eunbin\n";
            //3. Response Body 쓰는 메서드 호출
            response(exchange , content);
        });

        //예시2) "/hi" 호출
        httpServer.createContext("/hi", exchange -> {

            request(exchange);
            String content = "Hi, world!\n";
            response(exchange , content);
        });

        httpServer.start();
    }
```

> ### request 메서드

```java
    private static void request(HttpExchange exchange) throws IOException {

        String method = exchange.getRequestMethod();
        System.out.println("Method: " + method); //GET

        URI uri = exchange.getRequestURI();
        String path = uri.getPath();
        System.out.println("Paht:" + path); //"/"

        //Header값 가져오기
        exchange.getRequestHeaders().forEach((key, value) -> {
            System.out.println("Headers:" + key + ": " + value);
        });

        //RequestBody값 가져오기
        InputStream inputStream = exchange.getRequestBody();
        String body = new String(inputStream.readAllBytes());
        System.out.println("Body:" + body);
        
    }
```

> ### response 메서드

```java
    private static void response(HttpExchange exchange,String content) throws IOException {

        //Response Body 쓰기
        byte[] contentBytes = content.getBytes();

        //Response Header 작성
        exchange.sendResponseHeaders(200, contentBytes.length);

        //Response Body 작성
        OutputStream outputStream = exchange.getResponseBody();
        outputStream.write(contentBytes);
        outputStream.flush();
    }
```
