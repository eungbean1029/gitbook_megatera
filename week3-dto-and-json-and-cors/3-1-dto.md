# 💡 3-1 DTO

* RPC ,RMI
* DTO
  * setter, getter로 이루어짐
  * java bean 형태랑 가깝다.
* Tier간 통신
  * f/e b/e 사이
    * dto를 그대로 전송할 수는 없고 직렬화를 통해야 한다.
      * json형식
  * b/e db사이
    * Transger Object라고 정정함
