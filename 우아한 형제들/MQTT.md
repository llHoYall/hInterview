# MQTT (Message Queue for Telemetry Transport)

M2M 또는 IoT 기기와 G/W의 연동을 위해 정의된 protocol이며, 경량 protocol로 저전력 장비에서도 운용 가능하며 network bandwidth가 작은 곳에서도 충분히 운용 가능하도록 설계된 protocol이다.

* Connection Oriented
	+ MQTT broker와 연결을 요청하는 client는 TCP/IP socket 연결을 한 후 명시적으로 종료하거나 network 사정에 의해 연결이 끊어질 때까지 연결 상태를 유지한다.
	+ Topic에 발행된 message와 연결상태 확인을 위한 live(heart-beat)를 항상 유지된 연결을 통해 전달하게 된다.
	+ 연결 상태를 유지하는 것은 물론이고 연결이 끊어진 경우 재접속 등의 지원을 위한 자체 기능을 보유하고 있다.
* Topic 그리고 발행(publication) / 구독(subscription)
	+ 개설된 Topic에 message를 발행하면 해당 Topic을 구독하는 client 들에게 message를 전송한다다.
	+ 따라서 one to multi 또는 one to one message 전송을 모두 지원할 수 있다.
* QoS(Quality of Service)는 0, 1, 2 세단계를 지원
	+ 0 : 최대 1회 전송. Topic을 통해 message를 전송할 뿐 꼭 받으리라는 보장은 안해준다.
	+ 1 : 최소 1회 전송. 혹시 구독하는 client가 message를 받았는지 불확실하면 정해진 횟수만큼 재전송합니다.
	+ 2 : 등록된 client는 요구된 message를 정확히 한 번 수신할 수 있도록 보장한다.
* 다양한 개발언어의 다양한 client가 지원
	+ C는 물론이며 JAVA, Node.js, Python 등등 여러 종류의 개발언어로 Broker/Client Library가 존재한다.
	+ 대부분 유료의 경우 QoS-2까지 지원하고 보통은 QoS-1까지 지원한다.
* 각각의 Action에 따른 Notification
	+ Client의 연결, 연결해제, 구독, 발행 등등의 event에 대해서 MQTT broker가 대응할 수 있도록 해준다.
