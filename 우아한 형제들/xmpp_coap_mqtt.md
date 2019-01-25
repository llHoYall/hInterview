# [XMPP](#XMPP-(eXtensible-Messaging-and-Presence-Protocol)) vs [CoAP](#CoAP-(Constrained-Application-Protocol)) vs [MQTT](#MQTT-(Message-Queue-Telemetry-Transport))

## XMPP (eXtensible Messaging and Presence Protocol)

XMPP는 2인 이상의 참여자 간에 구조적 data를 거의 실시간에 가깝게 교환할 수 있게 해주는 XML 기반 TCP communication protocol이다.

XMPP의 기능들 중에는 대화 참여자 정보를 보여주는 것과 연락처 list 관리 기능이 있다. 두 기능 모두 instant messaging을 위해 제작된 것이었지만 IoT에도 적용할 수 있다.

XML 재단과 XMPP자체의 열려 있는 성질 때문에 XMPP는 publish/subscribe system에도 사용되고 있다. XMPP가 IoT application과 찰떡 궁합인 또 하나의 이유다.

IoT communication protocol로 XMPP를 사용하는 것에는 여러 가지 큰 장점이 있다. 우선 XMPP의 분산화된 성격이 큰 장점이다. XMPP의 작동 방식은 e-mail과 비슷하다. CoAP나 MQTT처럼 하나의 중앙 server나 broker에 의지하기보다는 여러 transfer agents에 걸쳐 작동하는 것이 특징이다.

E-mail과 마찬가지로 누구나 자신의 XMPP server를 운영할 수 있어 기기 제조업체나 API operator가 자신만의 기기 network를 형성하고 관리할 수 있다. 또한 누구나 server를 운영할 수 있기 때문에 보안이 요구되는 경우 내장 TLS 암호화를 사용해 회사 intranet에서 안전한 인증 protocol을 이용해 고립시킬 수 있다.

물론 XMPP에는 단점도 있다. 가장 큰 단점은 바로 `end-to-end 암호화가 안 된다`는 것이다. 물론 암호화가 굳이 필요하지 않은 경우도 있지만, 대부분 IoT 기기들은 암호화를 필요로 한다. End-to-end 암호화가 안 된다는 것은 IoT 기기에 있어서는 큰 단점이 아닐 수 없다.

또 다른 단점은 `QoS의 부재`다. Message가 제대로 전달 되었는지 확실히 하는 것은 instant message를 보낼 때도 중요하지만 IoT에서는 더더욱 중요하다. 예를 들어 아침에 깨워달라는 message가 alarm system에 제대로 전달되지 않는다면 고대하던 휴가를 망쳐버릴 수도 있다.

## CoAP (Constrained Application Protocol)

CoAP는 resource 제약이 있는 기기들이 internet 상에서 TCP 대신 UDP를 사용해 communication 할 수 있도록 개발됐다. 개발자들은 전통적인 방식의 REST 기반 API를 사용하는 여느 기기와 마찬가지로 CoAP 기기를 다룰 수 있다. CoAP는 특히 internet을 통해 control 해야 하는 저출력 sensor 및 기기와 communication 하는데 유용하다.

CoAP는 단순한 request/response protocol로(REST와 매우 비슷하다) 전통적인 client/server model을 따르고 있다. Client는 GET, PUT, POST, DELETE 요청을 할 수 있다. CoAP packet은 bitfields를 이용해 memory 효율을 극대화 하고 data packet을 on-device로 transport 할 수 있을 정도로 작게 유지하기 위해 strings to integers mapping을 광범위하게 사용한다.

매우 작은 packet size 외에 CoAP의 또 다른 장점은 바로 UDP의 사용이다. datagram을 사용하기 때문에 SMS같은 packet 기반 technology보다 성능이 뛰어나다.

모든 CoAP message는 ‘확인 가능’ 또는 ‘확인 불가능’으로 표시될 수 있어 application level의 QoS로 행동할 수 있다. SSL/TLS 암호화가 UDP에서는 불가능 하지만 CoAP는 TLS의 TCP버전과 비슷한 DTLS(Datagram Transport Layer Security)를 사용한다.

Default 암호화 level은 3,072-bits RSA 키와 동등하다. 그럼에도 불구하고 CoAP는 10KB 정도의 아주 작은 RAM이 장착된 micro controller에서 작동하도록 설계됐다.

CoAP의 단점 중 하나는 `one-to-one protocol`이라는 점이다. Group broadcast를 가능하게 한 확장을 이용할 수도 있지만 broadcast 기능은 one-to-one protocol에 내재적인 것이 아니다. 게다가 더 큰 단점은 `publish/subscribe message queue`의 부재다.

## MQTT (Message Queue Telemetry Transport)

MQTT는 publish/subscribe messaging protocol로, CoAP와 마찬가지로 자원 제약이 있는 기기를 target으로 개발됐다. MQTT는 memory 및 전력 이용을 효율화하기 위한 가벼운 packet 구조를 채택하고 있으며, 여기에 연결된 기기는 MQTT broker 상에 hosting 되는 topic에 인용된다. 어떠한 기기나 service가 data를 topic에 발행하면, 여기에 인용된 모든 기기들은 자동적으로 갱신된 정보를 획득하게 된다.

MQTT의 주된 장점으로는 `publish/subscribe message queue`와 `다-대-다 송출 기능`이 이야기된다. MQTT broker에 수명이 긴 방출 TCP 연결을 이용하고 제한된 대역폭의 message를 전후방으로 전송함으로써 MQTT는 간결함과 직관성을 보장한다.

하지만 이처럼 항시 연결을 유지하는 구조는 기기의 휴식 시간을 제한한다는 단점을 지니기도 하는데, MQTT는 기기의 대부분이 휴식하는 시점에도 다른 MQTT 프로토콜인 MQTT-SN(TCP가 아닌 UDP와 동작한다)를 활용함으로써 이러한 문제를 방지한다.
