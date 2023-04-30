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
