# study-tcp-ip-network-essentials-for-beginners
인프런 외워서 끝내는 네트워크 핵심이론 - 기초 강의 정리

# 들어가기에 앞서...
## 수강 전에 알고 있다고 가정하는 것들
### 수강에 앞서
1. bit, byte 등 정보 표현 단위를 알고 있다.
2. 1 byte는 8bit임을 알고 있다.
3. bit 단위 논리연산 (AND, OR, XOR 등)을 할 수 있다.
4. 2진수를 16진수로 변관할 수 있다.
5. 1024MB가 1GB임을 알고 있다.
6. Process와 Program의 차이를 알고 있다.
7. OSI 7 layer라는 말을 알고 있다.
8. 범용 운영체제는 User mode와 Kernel mode가 존재한다는 것을 알고 있다.
9. Buffer의 의미를 알고 있다.
10. 개념(Abstraction)과 구현(Implementation)의 차이를 안다.


## Layer와 Layered 구조
위의 layer는 아래 layer에 의존적이다.

## 네트워크와 네트워킹 그리고 개념
Network = 상호작용  
의존적 관계가 성립되는 계층구조 

### 개념과 구현(혹은 실체)
연예인 (추상적 - 개념(요소)) - 박은빈 (구체적 - 구현)

## User mode와 Kernel mode
- Application : L7
- Presentation : L6
- Session : L5
- Transport : L4
- Network : L3
- Data Link : L2
- Physical : L1 (NIC)

# Internet 기반 네트워크 입문

## OSI 7 layer와 식별자
- Application : L7 - HTTP  
- Presentation : L6 - X 
- Session : L5 - SSL (TLS)
- Transport : L4 - TCP, UDP / 식별자 : Port 번호 (Process(L7) / Interface(L1) / Service(L4))
- Network : L3 - Internet / 식별자 : IP 주소 (host에 대한 식별자) 
- Data Link : L2 - Ethernet / 식별자 : MAC주소 (물리적 주소)
- Physical : L1 - X 

식별자를 잘 알아두기!!


## Host는 이렇게 외우자
Computer가 Network에 연결이 되어있으면 Host가 된다. (Host == Network에 연결된 Computer)
- **Switch** : Network 그 자체를 이루는 host (Network의 기능, Infrastructure) - ex) Router(L3 switch의 일종), IPS(보안 switch), Tab, Aggregation
- **End-point** : Network 인프라를 이용하는 이용주체 (단말기) - 대표적인 것 : Client, Server (단말기의 역할에 따라 구분), Peer(Client와 Server를 동시에)

## 스위치가 하는 일과 비용
### Switch가 하는 일
출발지 ~ 목적지 까지 가는 길에 경로 선택    
교차로가 Switch, 경로가 Interface, 경로선택은 Switching     
IP주소를 근거로 Switching 하면 L3 Switching (Router), 이정표는 Routing Table

만약에 MAC주소를 가지고 Switching 하면 L2 Switching,   
Port 번호로 Switching -> L4 Switch,    
HTTP 프로토콜로 Switching -> L7 Switch이다.

### 항상 고민해야 할 주제는 '비용'
Matric : 이동하는 데 드는 비용

# L2 수준에서 외울 것들

## NIC, L2 Frame, LAN카드 그리고 MAC 주소
### NIC + L2 Frame + LAN card + MAC
- NIC(Network Interface Card)는 흔히 LAN(Local Area Network) 카드이다.
- 유/무선 NIC이 있지만 굳이 구별하지 않고 NIC이라고 할 때가 많다.
- NIC은 H/W이며 MAC 주소를 갖는다.

Network의 규모 : WAN > MAN > LAN

Packet : L2에서 언급하는 인터넷에서의 단위
L2 수준에서의 단위 : Frame (데이터 유통단위)

## L2 스위치에 대해서
### L2 Access switch
- End-point와 직접 연결되는 스위치
- MAC주소를 근거로 스위칭
- Link up : L2 Access에 연결이 잘 되었다.
- Link down : L2 Access에 연결이 해제되었다. (케이블에 문제가 생겼거나 연결이 해제됨)

### L2 Distribution switch
- 쉽게 생각하면 L2 Access 스위치를 위한 스위치
- VLAN(Virtual LAN) 기능을 제공하는 것이 일반적

## LAN과 WAN의 경계 그리고 Broadcast
- Broadcast 범위를 생각해보자.
- Broadcast 주소라는 매우 특별한 주소가 존재한다. (MAC, IP 모두 존재)
- 논리적인 것인지 아니면 물리적인 것인지로 구분하는 것도 방법이다.
- 일단 MAN(Metropolitan Area Network)은 제외하자.

MAC - 48bit / FF == 11111111, (FF-FF-FF-FF-FF-FF) => 이 경우가 Broadcast
Broadcast는 최소화시키는 것이 효율적이다. (Broadcast 중에는 다른 통신을 할 수 없기 때문)
Physical(물리적, H/W)로 설명되는 부분이 LAN이라고 생각하면 된다.

# L3 수준에서 외울 것들

## IPv4 주소의 기본 구조
### IPv4 주소의 구조
- MAC주소는 L2계층에서 가장 중요한 식별자, 48bit 주소체계를 가진다.
- IP는 32bit 주소체계를 가진다. = 8bit * 4
- 2의 8승 == 256, 0000 0000 ~ 1111 1111(2) 까지 0~255
- IP주소는 Network ID와 Host ID로 구성된다.
- Network ID는 8bit씩 끊어서 세부분으로 나뉜다. 
![img.png](img.png)

## L3 IP Packet으로 외워라
### L3 Packet (단위 데이터)
- Packet이라는 말은 L3 IP Packet으로 외워라
- Header와 Payload로 나뉘며 이는 상대적인 분류이다.
- **최대 크기는 MTU** (중요!!) 보통 MTU는 1500byte정도임.
![img_1.png](img_1.png)
- Header가 실어나르는 대상이 Payload
- Header 정보에서 가장 중요한 정보 (Src(출발지) -> Dst(도착지))
- Network를 감청하는 프로그램 : Wireshark (Analyzer, Sniffer)

## Encapsulation과 Decapsulation
### Encapsulation
- 별것 아니다. 러시아 전통 목각인형인 마트료시카 인형을 떠올려라.
- 단위화하고 포장을 하는 것.

### En/Decapsulation
![img_2.png](img_2.png)
- 이 전체는 Frame (L2)
- 그 안은 IP Packet (L3), L2 Frame의 Payload
- 그 안은 TCP Segment (L4), L3 Packet의 Payload
- Encapsulation은 합치는 것
- Decapsulation은 분해하는 것

## 패킷의 생성, 전달
### 패킷의 생성, 전달, 소멸
Process가 어떤 데이터를 다른 Process에게 전달해야할 때
전달할 데이터를 Packet으로 만든다.
우리집(Host) 현관(Interface)에서 택배기사님(Gateway)에게 전달
처리 후 받을 Process의 Host에게 전달

### Process가 어떤 데이터를 인터넷을 통해 다른 Process에게 전달하는 과정
1. Data가 있다고 가정, Process와 Kernel을 이어주는 Tcp Socket(File의 일종, Kernel mode 프로토콜을 User mode Application Process가 접근할 수 있도록 추상화 시켜준 Interface)에 write(send)
2. Tcp 소켓에서 Data에 Tcp Header를 붙여서 Segment화 한다.
3. 한 층 더 내려가 IP Header가 또 붙는다.
4. 한 층 더 내려가면 Ethernet Frame Header가 붙는다.
5. Driver를 통해 L2 Access를 통해서 나가고 Router를 지나 인터넷으로 나간다.

## 계층별 데이터 단위
- Socket(L5 ~ L7) 수준 : Stream
- L4 : Segment [MSS (Maximun Segment Size)] - 최대 1460 byte
- L3 : Packet [MTU (Maximun Transmission Unit)] - 최대 1500 byte
- L1 ~ L2 : Frame

Stream의 특징 : 시작은 있으나 끝을 정의할 수 없다. Application 수준에서 끝을 정한다.
Stream이 Packet이나 Segment의 최대 크기보다 클 때 분할한다.

## 이해하면 인생이 바뀌는 TCP/IP 송수신 구조
### 파리에서 에펠탑을 택배로 보내려면 어떻게 해야할까?
1. 에펠탑을 분해 -> 크기 줄이기 - Packet (MTU 이하로) : 송신측
2. 운송
3. 조립 : 수신측

### TCP 연결이 되었다는 가정 하에 데이터를 송수신한다.
#### 송신하는 과정 (Encapsulation)
1. Process에서의 파일을 보낼 때 파일을 copy해서 Buffer에 올린다.
2. Socket에 I/O할 때 Buffer(메모리공간)가 존재, Socket의 Buffer에도 또 copy해서 올린다. (Process에서 Socket에 파일을 Send한다.)
3. User mode에서 Kernel로 넘어갈때 TCP로 갈 때 분해(Segmentation)가 일어난다. -> 이 때의 데이터 단위를 Stream이라고 한다.
4. TCP에서 분해된 개념이 Segment가 된다.
5. Segment화 된 데이터가 한 층을 더 내려간다(IP 층)
6. Segment를 박스(Packet) 속에 넣는다.
7. L2로 내려간다. 트럭(Frame)에 실려 전송된다.

#### 수신하는 과정 (Decapsulation)
1. L2수준에서 트럭(Frame)에 담긴 택배(Packet)가 올라간다.
2. L3에서 택배(Packet) 안에서 담긴 Segment를 꺼낸다.
3. L4수준에서 TCP에서 Socket의 I/O Buffer에 쌓는다.
4. Process의 Buffer에 Socket의 Buffer에 담겨있던 데이터를 담는다.
5. TCP의 Buffer에 저장될 때 송신하는 Process 쪽에 ACK를 보낸다. (1,2를 보냈을 때 ACK 3 + 여유공간의 크기를 보낸다.)  
Socket I/O Buffer의 여유공간 : Window Size라고 한다.

-> TCP 통신은 순서가 중요한 개념!! 

### Network 장애
1. Loss (Lost Segment) - Segment를 유실 : 100% Network 문제
2. Re-transmission (송신 측에서 데이터를 보낸 후 ACK를 기다리는데, 일정 시간 후 ACK가 오지 않으면 다시 데이터를 보낸다.) + ACK-Duplicate (ACK를 중복) : Network 일 수도 있고 End-point 간의 문제일 수 있다.
3. Out of order (순서대로 와야하는데 1,2가 온 후 3이 오지 않고 4가 오는 경우) : 거의 Network 문제
4. Zero window : End-point 단계에서 Application이 데이터를 빨리 안끌어간 것. (문제가 프로그램에 있음)

## IP 헤더 형식
### IPv4 Header 형식
IP Header는 20 byte가량 되고 Payload는 1480 byte정도 된다.
![img_3.png](img_3.png)
TTL(Time to Live) 값이 0이 되면 패킷은 버려진다.    
Protocol : 또 다른 Header가 올 때 그것에 대한 설명   
Header checksum : 네트워크에서 패킷이 송수신되는 중 데이터가 온전한지 검사한 검사합 값 

## 서브넷 마스크와 CIDR
### Subnet Mask
255(A class).255(B class).255(C class).0      
bit단위로 AND연산을 했을 때 Network ID가 나와 일치한다면 우리 Network로 오는 Packet인 것을 검증한다.

### CIDR (Classless Inter-Domain Routing)
ex) 192.168.0.10/24   
위와 같이 표현하는 표현방법

## Broadcast IP 주소
MAC 주소 : 48bit FF-FF-FF-FF-FF-FF
Network ID의 Host ID가 1111 1111일 때 해당 Network의 방송(Broadcast) 주소로 쓰인다.
![img_4.png](img_4.png)

Host ID로 쓸 수 없는 주소
- 0 : 서브넷 마스크로 쓰임
- 255 : Broadcast로 쓰임
- 1 : Gateway에 준다.

## Host 자신을 가리키는 IP주소
내 Process간에 접근, 접속해야할 때 => 127.0.0.1 : Loopback Address
IPC(Inter Process Communication)을 구현할 때 Socket을 이용해서 내가 나에게 접속하는 과정을 사용

## TTL과 단편화
### 인터넷은 라우터의 집합체라고 할 수있는 논리 네트워크이다.
Router는 L3 Switch이다.

#### 인터넷을 이루는 핵심요소 : Router + DNS

### TTL과 단편화
- Time To Live는 세포의 '텔로미어' 같은 역할을 한다. (세포가 복제가 일어나면 텔로미어 길이가 짧아지며 세포가 무한증식하는 것을 막는 것)
- 단편화(Packet을 한번 더 자르는 것)는 MTU 크기 차이로 발생한다.
- 보통 단편의 조립은 수신측 Host에서 이루어진다.

Packet이 인터넷을 돌아다니며 목적지까지 가야하는데 간혹 실패하는 경우가 있음.
-> 그럴때는 Packet을 폐기시켜야 한다. 그걸 막는 역할을 하는 것이 TTL

Router와 Router(홉)를 지날 때마다 TTL을 1씩 감소, TTL이 0이 되면 해당 Router가 해당 Packet을 폐기시킨다.

- 단편화는 가급적 발생되지 않는 것이 좋다.
- Router와 Router에서 Hop을 할 때 각 Router의 MTU가 일정해야 단편화가 일어나지 않는다.
- Router와 Router에서 Hop을 할 때, Packet의 크기는 1500인데, 1400인 Router를 거쳐가려고 할 때 Packet이 쪼개지는 단편화가 일어난다.
- 통상 조립은 수신측 End-point에서 한다.


단편화가 일어나는 예) VPN IPSec울 이용할 때

## 인터넷 설정 자동화를 위한 DHCP
### 인터넷 사용 전에 해야 할 설정
* L3 수준의 설정
  - IP주소 : IPv4 32bit의 주소값을 구매 (ISP - Inter Service Provider에게 구매)
  - Subnet mask
  - Gateway IP 주소
- DNS 주소

자동으로 IP 주소 받기 == DHCP를 활용하겠다.

### DHCP
- DHCP(Dynamic Host Configuration Protocol) 체계는 주소를 할당하는 서버와 할당 받으려는 클라이언트로 구성된다. - Configuration : IP주소 + Gateway + DNS + Subnet mast 등
- 복잡한 인터넷 설정을 자동으로 해준다고 볼 수 있는데 핵심은 내가 사용할 IP 주소를 서버가 알려준다는 것에 있다.

Dynamic은 Runtime과 비슷한 의미로 보면 된다.

1. IP를 할당받기 위해 해당 PC가 Broadcast를 한다.
2. DHCP는 IP Pool을 가지고 있어 할당받기를 원하는 PC들에게 IP를 설정해준다.

## ARP
### ARP(Address Resolution Protocol)
- ARP는 IP주소로 MAC주소를 알아내려 할 때 활용된다.
- 보통의 경우 PC를 부팅하면 Gateway의 MAC주소를 찾아내기 위해 ARP Request가 발생하며 이에 대응하는 Reply로 MAC 주소를 알 수 있다.

Address - IP주소(L3)와 MAC주소(L2)   

인터넷에 접속하는 과정
1. DHCP를 통해서 자신의 IP주소를 받는다. (Broadcast 발생)
2. DHCP가 나의 Gateway의 IP를 알려준다.
3. ARP Request를 Broadcast해서 DHCP가 알려준 Gateway의 IP주소를 보내 Gateway의 MAC주소를 찾는다.
4. Gateway가 자신의 MAC주소를 ARP Reply를 한다.

인터넷에 접속하려고 하면 Gateway의 MAC주소를 반드시 알아야 한다. (왜? Frame의 목적지가 Gateway의 MAC Address로 잡히기 때문)  
목적지의 MAC Address는 Gateway의 MAC Address로 잡힌다.  
네이버에 접속한다고 예를 들었을 때, IP Packet의 도착지는 네이버의 IP이지만, Frame의 도착지는 Gateway의 MAC Address이다.

## Ping과 RTT
- Ping 유틸리티(그냥 프로그램)는 특정 Host에 대한 RTT(Round Trip Time)을 측정할 목적으로 사용된다.
- ICMP(Internet Control Message Protocol) 프로토콜을 이용한다.
- Dos(Denial of Service) 공격용으로 악용되기도 한다.

서버와 회선의 연결 상태를 Ping 이라고 한다.   
게임의 서버를 동기화할 때 Round Trip Time을 동기화시킬 때 Ping을 사용한다.


# L4 수준 대표주자 TCP와 UDP

## TCP와 UDP 개요
### TCP와 UDP
- TCP에만 연결(Connection, Session) 개념이 있다. - 연결은 논리적(Virtual), circuit도 포함
- 연결은 결과적으로 순서번호로 구현된다.
- 연결은 '상태(전이)' 개념을 동반한다. (연결 전, 연결 후의 상태)
- TCP는 배려남, UDP는 (배려가 없는) 나쁜남자에 비유할 수 있다. - TCP는 상대가 데이터를 받을 준비가 되면 보냄, UDP는 상관 안함
- 둘의 가장 큰 차이 Connection Oriented냐 아니냐

TCP - Segment / UDP - Datagram / Socket - Stream

#### TCP의 Client / Server 연결과정
1. Server는 연결 대기
2. Client는 Process로 Socket을 Open, Kenel은 해당 Process에 PID를 부여
3. PID를 가진 Process가 Socket을 열면 운영체제가 해당 Socket에 TCP Port번호를 부여
4. TCP에서 Port번호가 열리면 
5. Server도 Socket을 생성 + 개방(Open), 연결 대기(LISTEN)상태의 Socket으로 연결

## TCP 연결 과정 (3-way handshaking)
![img_5.png](img_5.png)

Client Server   
RTT(Round Trip Time) - Client가 Server에 한 번 갔다가 오는 시간
1. 연결을 하려는 PC(Client)에서 연결요청을 SYN 한다. (Client에서 랜덤하게 뽑은 Sequence number를 같이 보낸다.) SYN(1000)
2. Server에서도 랜덤하게 만든 Sequence number를 생성, SYN(4000) + ACK(1001)을 보낸다.
3. Client에서 Server가 보낸 SYN + ACK을 확인 후 한번 더 ACK(4001)을 보낸다.

Sequence Number교환, 정책교환(MSS이 얼마인지 알려줌)이 이루어진다.
Server와 Client간의 연결에서 Maximum Segment Size를 교환하고, 한 쪽이 낮다면 다른 쪽이 거기에 맞춰주어 연결이 일어난다.

## TCP 연결종료 및 상태변화
### TCP 연결 종료 과정 (4-way handshaking)
![img_6.png](img_6.png)
특별한 이유가 없다면 Client가 활동이 Active하다.
연결을 시작하려는 것도, 연결을 종료하는 것도 Client 쪽이 보편적이다.

1. Client가 연결을 끊기 위해 FIN + ACK을 보낸다.
2. Server에서 ACK을 보낸다.
3. Server에서 FIN + ACK을 보낸다.
4. Client가 ACK을 보낸다.
5. Closed되면 Socket이 회수가 된다.

## TCP (연결) 상태 변화
![img_7.png](img_7.png)
ESTABLISHED가 되어야 연결이 완료된 것.


## TCP, UDP 헤더형식과 게임서버 특징
### TCP Header 형식
![img_8.png](img_8.png)
Window Size : TCP Buffer의 여유 공간
Checksum : 데이터 손상된 것이 없는지 계산할 때 쓰이는 검사값

### UDP Header 형식
![img_9.png](img_9.png)
혼잡제어 X, 게임서버는 UDP 형식을 지향

## TCP '연결'이라는 착각
### 파일 다운로드 중 LAN 케이블을 분리했다가 다시 연결하면 TCP 연결은 어떻게 될까?
TCP 연결은 유지된다. Process에서 TCP연결이 되어있는지 수시로 재확인(Heartbeat)한다.

### TCP 연결이라는 착각
- 재전송 타이머의 기본 근사 값은 대략 3초다. 하지만 대부분의 운영체제들은 1초 미만이다.
- 재전송 타이머 만료 후에도 확인 응답을 받지 못한 경우 세그먼트를 재전송하고 RTO(Retransmission Time-Out) 값은 두 배로 증가한다.
- 예를 들어 1초 > 2초 > 4초 > 8초 > 16초 간격으로 재전송한다.
- 보통 최대 5회 재전송을 시도하고 5회 이상 모두 실패할 경우 보통 전송 오류가 발생한다.

## TCP 연결과 게임버그
- 어떤 MMORPG 게임에서 아이템 복제 버그가 발생하였다.
- 이는 논리적 TCP 연결과 물리적 링크 간 차이를 이용한 시간차 공격이라 볼 수 있으며 연결이 사실은 End-point의 주관적 판단에 불과하다는 것을 보여준다.
연결 + 보안성(기밀, 무결, 가용)이 없다.

# 웹을 이루는 핵심기술

## 한 번에 끝내는 DNS
L1 ~ L4 : Infra구조   
L5 ~ : Application  

### DNS (도메인 이름으로 IPv4주소를 검색해서 알려주는 서버) 
- 분산 구조형 데이터베이스
  + 데이터베이스 시스템(DNS 네임서버)의 분산 구성
  + 데이터의 영역별 구분(Domain Zone) 및 분산관리
  + 도메인의 네임서버 및 도메인 데이터는 해당 관리주체에 의해 독립적으로 관리됨
- 트리(tree) 구조의 도메인 네임(Domain Name) 체계
  + Domain : 영역, 영토를 의미
  + 도메인 네임의 자율적 생성
  + 생성된 도메인 네임은 언제나 유일(Unique)하도록 네임 체계 구성

www.naver.com : www - Host Name / naver.com - Domain Name

#### https://www.naver.com를 입력했을 때 일어나는 일 
1. IP 서버 설정에 DNS주소가 포함되어 있음
2. 운영체제 내부에서 ISP를 통해 DNS에 "https://www.naver.com"의 IP를 알려달라고 질의를 한다.
3. 그 알아온 IP를 통해 naver에 접속

한 번이라도 어떤 사이트에 접속하게 되면 DNS Cache에 해당 도메인 이름과 아이피를 저장한다.

- DNS Cache
- Hosts 파일  

공유기가 DNS Forwarding을 이용해서 DNS가 하는 일을 대신 하는 경우도 있다.

## 웹 기술의 창시자와 대한민국 인터넷
### 웹 기술의 창시자 - 팀 버너스리
- CERN(입자물리연구소)에서 컨설턴트로 근무
- 정보검색 시스템 구축
- 이를 바탕으로 현재의 웹 기술을 창안
- HTML, HTTP의 창시자

HTML은 문서, HTTP는 HTML문서를 실어나르는 프로토콜

## URL과 URI
- Uniform Resource Locator (위치 지정자 - file의 저장된 위치) : File을 특정함
- Uniform Resource Identifier (식별자) : 포괄적 개념
- Protocol://Address:Portnumber/Path(or filename)?Parameter=value
- http://www.test.co.kr/course.do?cmd=search&search_keyword=Test
URI > URL

Web의 근간 -> HTML + HTTP
 / File이 Resource다.

### URI 구조
- URI = scheme ":" ["//" authority] path ["?" query] ["#" fragment]

## 굵고 짧게 살펴보는 HTTP
### HTTP
- HTTP는 HTML 문서를 전송 받기 위해 만들어진 응용 프로그램 계층 통신 프로토콜이다.
- 1996에 1.0 스펙이 발표됐으며 1996년 6월에 1.1이 발표됐다.
- 기본적으로 클라이언트의 요청에 대응하는 응답형식으로 작동한다.
- 헤더는 다음과 같이 분류된다.
  + 일반 헤더
  + 요청 헤더
  + 응답 헤더
  + 엔티티 헤더
- 요청에 사용되는 메서드는 주로 GET, POST이다.

### HTTP method
- GET : Download
- POST : Upload
- HEAD
- TRACE
- PUT : Resource 새로 업로드
- DELETE
- OPTIONS
- CONNECT

### HTTP 응답 코드
- 200 OK
  + 요청이 정상적으로 처리됨
- 201 Creat
  + 요청에 대한 새로운 자원을 생성하는데 성공함
- 301 Moved permanently
- 302 Found
- 400 Bad request
  + HTTP 규약에 맞지 않는 요청.
- 403 Forbidden
  + 권한이 없거나 잘못된 파일 실행 접근 시도.
- 404 Not found
- 500 Internal server error
  + 내부 오류때문에 요청을 처리할 수 없음.

## 그림 한 장으로 외워서 끝내는 웹 서비스 구조 기본이론
### 웹 서비스 기본 구조
Web Client와 Web Server는 TCP/IP 연결 아래 진행됨.
HTTP는 Socket 수준에서 이루어짐 -> Stream
1. TCP/IP 연결을 기반으로 HTTP 통신이 이루어짐
2. HTTP Request로 파일 Get 요청을 보냄
3. Response로 해당 HTML 문서를 보냄
4. 동적 문서에 대한 필요가 생김 -> script로 Mocha script(Live script -> JavaScript)가 생김.
5. 구문분석, 렌더링(css), JS엔진 까지 생기게 된다. 
6. 사용자의 반응에 따라 상호작용의 필요성이 커지게 됨 -> 방법론들이 등장
7. HTTP의 POST Request 등장 (양방향 상호작용 + 상태전이)
8. Client와 Server에서 상호작용의 상태를 기억하도록 기록할 필요성이 생김
9. Client - Cookie / Server - Database가 생기게 된다.
10. POST 요청 id=tester&pwd=1234 => 원격지 사용자 입력 : 검증 대상
11. WAS에서 처리를 담당

## WAS와 RESTful API 그리고 JVM
APM (Application Performance Management) - WAS와 DB사이에서 성능을 모니터링하는 시스템 ex) Scouter
JVM은 Java를 위해서 소프트웨어로 구현된 CPU   
서블릿 컨테이너를 다른 말로 WAS라고 함   
APM은 이 JVM을 모니터링한다.

12. UI와 Data 분리 -> 자료만 요청 -> xml, Json으로 응답
13. 클라이언트의 요청에 따라 CRUD를 각 함수로 만들고 그 함수를 Uri로 생성 : RESTful API 등장
