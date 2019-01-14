# RESTful (REpresentational State Transfer)

## REST API

REST API는 다음과 같은 구성으로 이루어져 있다.

* Resource - URI
* Verb - HTTP Method
* Representations

REST API 설계 시 다음 2가지가 가장 중요하다.

* URI는 정보의 자원을 표현해야 한다.
* 자원에 대한 행위는 HTTP method (GET, POST, PUT, DELETE)로 표현한다.

## REST의 특징

### Uniform Interface

URI로 지정한 resource에 대한 조작을 통일되고 한정적인 interface로 수행하는 architecture style을 말한다.

### Statelessness

작업을 위한 상태정보를 따로 저장하고 관리하고 않는다. Session 정보나 cookie 정보를 별도로 저장하고 관리하지 않기 때문에 API server는 들어오는 요청만을 단순히 처리하면 된다. 때문에 service의 자유도가 높아지고 server에서 불필요한 정보를 관리하지 않음으로써 구현이 단순해진다.

### Cacheability

HTTP 표준에서 사용하는 `Last-Modified` tag나 `E-Tag`를 이용하여 caching 구현이 가능하다.

### Self-Descriptiveness

REST API message만 보고도 이를 쉽게 이해 할 수 있는 자체 표현 구조로 되어 있다.

### Client-Server Architecture

REST server는 API 제공, client는 사용자 인증이나 context(session, login 정보)등을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에 client와 server에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어들게 된다.

### Layered System

REST server는 다중 계층으로 구성될 수 있으며 보안, load balancing, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고 proxy, gateway 같은 network 기반의 중간 매체를 사용할 수 있게 한다.
