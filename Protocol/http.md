# HTTP (HyperText Transfer Protocol)

HTML과 같은, hyper-media 문서 전송을 위한 응용 계층 protocol이다.

HTTP는 web browser와 web server 사이의 통신을 위해 설계되었지만 다른 목적을 위해서도 사용될 수 있다.

이 protocol은 연결을 열고, 요청을 보낸 뒤 응답을 받을 때까지 대기하는 client를 이용하는 고전적인 client-server model을 따른다. 또한 무상태 protocol로, 이는 두 개의 요청 사이에 어떤 data(상태)도 server가 유지하지 않는다는 것을 의미한다. 대개 TCP/IP 계층을 기반으로 하지만, 모든 안정적인 전송 계층에서 사용할 수 있다. UDP처럼 message를 묵시적으로 손실하지 않는 protocol이다.
