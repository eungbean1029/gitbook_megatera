# 💡 1-3 HTTP Server

### Java Server Socket

* ServerSocket 클래스 -> 서버 프로그램을 구현하는데 사용된다.

#### Socket 송수신 과정

STEP1 (서버) : 클라이언트의 요청을 받기 위한 준비를 한다. \[ServerSocket]

STEP2(클라이언트) : 서버에 접속 요청을 한다. \[Socket]

STEP3(서버) : 클라이언트의 요청을 받아 들인다. \[accept]

STEP4(클라이어트) : 서버에 메시지를 보낸다. \[BufferedWriter]

STEP5(서버) : 클라이언트가 보낸 데이터를 출력한다. \[BufferedReader]

STEP6(서버) : 클라이언트에 메시지를 보낸다. \[BufferedWriter]

STEP7(클라이언트) : 서버가 보낸 메시지를 출력한다. \[BufferedReader]

STEP8(서버,클라이언트) : 종료한다. \[socket.close()]

### Blocking / Non Blocking
