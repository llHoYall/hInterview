# Bluetooth Low Energy

## Communication

### Advertise Mode (Broadcast Mode)

* Advertiser (Broadcaster)
	+ Non-Connectable Advertising Packet을 주기적으로 보내는 device.
* Observer
	+ Advertiser가 보내는 Non-Connectable Advertising Packet을 수신하기 위해 주기적으로 Scanning하는 device.

### Connection Mode

* Central (Master)
	+ Central device는 다른 device와 Connection을 맺기 위해, Connectable Advertising Signal을 주기적으로 scan하다가, 적절한 device에 연결을 요청한다. 연결이 되고 나면, Central device는 timing을 설정하고 주기적인 데이터 교환을 주도한다. 여기서 timing이란, 두 device가 매번 같은 channel에서 data를 주고 받기 위해 정하는 hopping 규칙이라고 생각하면 된다.
* Peripheral (Slave)
	+ Peripheral device는 다른 device와 Connection을 맺기 위해, Connectable Advertising Signal을 주기적으로 보낸다. 이를 수신한 Central device가 Connection Request를 보내면, 이를 수락하여 Connection을 맺는다. Connection을 맺고 나면 Central device가 지정한 timing에 맞춰 channel을 같이 hopping을 하면서 주기적으로 data를 교환한다.

## Protocol Stack

### Physical Layer

* 총 40개의 channel로 나누어 통신을 한다.
	+ 37, 38, 39 3개의 channel은 Advertising Channel이다.
	+ 나머지 37개의 channel은 Data Channel이다.

### Link Layer

#### Role

* Master
	+ 연결을 시도하고, 연결 후에 전체 connection을 관리하는 역할.
* Slave
	+ Master의 연결 요청을 받고, Master의 timing 규약을 따르는 역할.
* Advertiser
	+ Advertising Packet을 보내는 역할.
* Scanner
	+ Advertising Packet을 Scanning하는 역할. Scanner는 아래와 같은 2가지 Scanning mode가 있다.
		- Passive Scanning : Scanner는 Advertising Packet을 받고 이에 대해 따로 응답을 보내지 않는다. 따라서 해당 packet을 보낸 advertiser는 scanner가 packet을 수신했는지에 대해서 알지 못한다.
		- Active Scanning : Advertising Packet을 받은 Scanner는 Advertiser에게 추가적인 data를 요구하기 위해 Scan Request를 보낸다. 이를 받은 Advertiser는 Scan Response로 응답한다.

### Generic Access Profile (GAP)

GAP는 서로 다른 제조사가 만든 BLE device들끼리 서로 호환되어 통신할 수 있도록 해주는 주춧돌 역할을 한다. 즉, 어떻게 device간에 서로를 인지하고, Data를 Advertising하고, Connection을 맺을지에 대한 framework를 제공한다.

#### Role

* Broadcaster
* Observer
* Central
* Peripheral

### Generic Attribute Profile (GATT)

BLE Data 교환을 관리하는 GATT는 device들이 data를 발견하고, 읽고, 쓰는 것을 가능하게 하는 기초적인 data model과 procedure를 정의한다. Device간에 low-level에서의 모든 interaction을 정의하는 GAP와는 달리, GATT는 오직 data의 format 및 전달에 대해서만 처리한다. Connection Mode일 때, GATT Service와 Characteristic을 이용하여 양방향 통신을 하게 된다.

#### Role

* Server
	+ Client에게 request를 받으면 response를 보낸다. 또한, client가 사용할 수 있는 user data를 생성하고 저장하는 역할을 한다.
* Client
	+ Server에게 data를 요청한다. 처음에는 server에 대해 아는 것이 없기 때문에 Service Discovery를 수행한다. 이후, server에서 전송된 response, indication, notification을 수신할 수 있다.
