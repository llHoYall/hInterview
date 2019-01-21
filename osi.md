# OSI 7 Layers (Open System Interconnection)

## Physical Layer

Network의 기본 network H/W 전송 기술을 이룬다. Network의 높은 수준의 기능의 논리 data 구조를 기초로 하는 필수 계층이다. 다양한 특징의 H/W 기술이 접목되어 있기에 OSI rchitecture에서 가장 복잡한 계층으로 간주된다.

전송 Cable, 주파수 등의 전기적, 물리적 특징이 정의되어 있다.

## Data Link Layer

P2P node간의 신뢰성있는 전송을 보장하기 위한 계층으로 CRC 기반의 오류 제어와 흐름 제어가 필요하다. Network 위의 개체들 간 data를 전달하고, 물리 계층에서 발생할 수 있는 오류를 찾아 내고, 수정하는 데 필요한 기능적, 절차적 수단을 제공한다.

주소 값은 물리적으로 할당 받는데, 이는 network card가 만들어질 때부터 MAC address가 정해져 있다는 뜻이다. 주소 체계는 계층이 없는 단일 구조이다.

데이터 링크 계층의 가장 잘 알려진 예는 ethernet이다. 이 외에도 HDLC나 ADCCP 같은 P2P protocol이나 packet switching network나 LLC, ALOHA 같은 근거리 network용 protocol이 있다. Network bridge나 Switch 등이 이 계층에서 동작하며, 직접 이어진 곳에만 연결할 수 있다.

## Network Layer

여러 개의 node를 거칠때마다 경로를 찾아주는 역할을 하는 계층으로 다양한 길이의 data를 network를 통해 전달하고, 그 과정에서 전송 계층이 요구하는 서비스 품질(QoS)을 제공하기 위한 기능적, 절차적 수단을 제공한다.

Network 계층은 routing, 흐름 제어, segmentation/desegmentation, 오류 제어, Internetworking 등을 수행한다. Router가 이 계층에서 동작하고 이 계층에서 동작하는 Switch도 있다.

Data를 network를 통해 전달함으로써 internet이 가능하게 만드는 계층이다. 논리적인 주소 구조(IP), 곧 network 관리자가 직접 주소를 할당하는 구조를 가지며, 계층적이다.

Subnet의 최상위 계층으로 경로를 설정하고, 청구 정보를 관리한다. 개방형 system들의 사이에서 network 연결을 설정, 유지, 해제하는 기능을 부여하고, 전송 계층 사이에 NSDU(Network Service Data Unit)을 교환하는 기능을 제공한다.

## Transport Layer

End-to-end의 사용자들이 신뢰성있는 data를 주고 받을 수 있도록 해 주어, 상위 계층들이 data 전달의 유효성이나 효율성을 생각하지 않도록 해준다.

Sequence number 기반의 오류 제어 방식을 사용한다. 전송 계층은 특정 연결의 유효성을 제어하고, 일부 protocol은 stateful하고, connection oriented이다. 이는 전송 계층이 packet들의 전송이 유효한지 확인하고 전송에 실패한 packet들을 다시 전송한다는 것을 뜻한다.

가장 잘 알려진 전송 계층의 예는 TCP이다.

End-to-end 통신을 다루는 최하위 계층으로 종단간 신뢰성 있고 효율적인 data를 전송하며, 기능은 오류 검출 및 복구와 흐름 제어, 중복 검사 등을 수행한다.

Data의 용량, 속도, 목적지 등을 다룬다.

## Session Layer

양 끝단의 응용 process가 통신을 관리하기 위한 방법을 제공하는 계층이다. Duplex, half duplex, full duplex의 통신과 함께, check pointing과 유휴, 종료, 다시 시작 과정 등을 수행한다.

이 계층은 TCP/IP session을 만들고 없애는 책임을 진다.

통신하는 사용자들을 동기화하고 오류 복구 명령들을 일괄적으로 다룬다.

설정, 조율 (응답 대기 시간), 종료 등의 기능을 정의한다.

## Presentation Layer

Code 간의 번역을 담당하여 사용자 system에서 data의 형식상 차이를 다루는 부담을 응용 계층으로부터 덜어 준다. MIME encoding이나 암호화/복호화 등의 동작이 이 계층에서 이루어진다. 예를 들면, EBCDIC로 encoding된 문서 file을 ASCII로 encoding된 file로 바꿔 주는 것이 표현 계층의 몫이다.

## Application Layer

응용 process와 직접 관계하여 일반적인 응용 service를 수행한다. 일반적인 응용 service는 관련된 응용 process들 사이의 전환을 제공한다.

응용 service의 예로, 가상 terminal(ex. telnet), "Job transfer and Manipulation protocol" (JTM, 표준 ISO/IEC 8832) 등이 있다.
