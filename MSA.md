## MSA가 뭔가요?

Microservice Architecture는 작고 독립적으로 배포 가능한 각각의 서비스들로 이루어진 프레임워크라고 할 수 있습니다.  
MSA는 서비스의 부분적인 장애가 서비스 전체 장애로 퍼지는 것을 방지하기 위해,  
서비스의 변경을 용이하도록 하기 위해 만들어졌으며,  
각 서비스가 RPC나 message stream 등을 이용해서 통신할 수 있도록 구성되어 있는 것이 일반적이라고 할 수 있습니다.

<br>

## gRPC가 무엇인가요?

gRPC는 Google에서 만든 Remote Procedure Call이며, 특히 MSA 환경에서 많이 사용되고 있습니다.  
최신 버전의 IDL로 proto3를 사용하기 때문에 Java, JavaScript, C++, Ruby, Python 등 다양한 언어를 지원합니다.  
그리고 gRPC의 핵심적인 부분은 HTTP 2.0과 Protocl Buffer를 사용한다는 점입니다.  
HTTP 2.0은 HTTP 1.1에 비해서 한 connection으로 동시에 여러 개의 메시지를 주고 받으며,  
header를 압축하여 중복을 제거한 뒤 보내기 때문에 훨씬 더 효율적인 버전입니다.  
그리고 Protocol Buffer는 Google 사에서 개발한 데이터 직렬화 기법으로,  
기존의 text 기반의 JSON에 비해 데이터 표현을 byte 단위로 변환하는 작업에서 훨씬 더 적은 byte를 사용하도록 해줍니다.

- Reference 1 : [gPRC란?](https://chacha95.github.io/2020-06-15-gRPC1/)
- Reference 2 : [시대의 흐름, gRPC 깊게 파고들기](https://medium.com/naver-cloud-platform/nbp-%EA%B8%B0%EC%88%A0-%EA%B2%BD%ED%97%98-%EC%8B%9C%EB%8C%80%EC%9D%98-%ED%9D%90%EB%A6%84-grpc-%EA%B9%8A%EA%B2%8C-%ED%8C%8C%EA%B3%A0%EB%93%A4%EA%B8%B0-1-39e97cb3460)

<br>

## gRPC에는 어떤 장단점이 있나요?

우선 장점으로는 HTTP/2를 사용하기 때문에 효율적이면서 간단합니다.  
그리고 Protocol Buffer 또한 직렬화 과정을 매우 빠르게 해주기 때문에 성능상의 이점이 있습니다.  
또한 proto 파일을 통해 메세지의 규약을 정의하고 이를 서버와 클라이언트가 공유하기 때문에  
클라이언트를 위한 별도의 응용 프로그램 같은 것이 필요하지 않습니다.

<br>

단점으로는, 브라우저가 HTTP/2를 사용하도록 요구할 수 없으므로, 브라우저 상에서 직접 호출할 수는 없습니다.  
그리고 이진 형식의 Protobuf는 사람이 직접 읽거나 생성할 수가 없습니다.

<br>

## RabbitMQ와 Kafka의 차이점이 뭔가요?

우선 기본 개념적인 차이로, RabbitMQ는 전통적인 메시지 브로커이지만 Kafka는 최신 이벤트 스트리밍 플랫폼입니다.  
그래서 RabbitMQ의 경우, Event Producer가 메시지를 발행하면 메시지 브로커인 RabbitMQ는  
이 메시지를 어떤 큐에 보낼지 결정해서 exchange를 하고,  
이렇게 큐에 들어간 메시지는 Event Consumer가 가져가게 됩니다.  
여기서 한 가지 중요한 점은 컨슈머가 메시지를 가져가게 되면 큐에는 더이상 메시지가 남지 않고  
사라지게 되어서 이벤트를 다시 재생하기가 어렵습니다.  
따라서 RabbitMQ는 소비자와 메시지 브로커의 결합력이 높아지게 되어  
추후 트래픽이 증가해도 확장에 용이하지 못하다는 단점이 있습니다.

<br>

반면에 Kafka는 이벤트 스트리밍 플랫폼으로서, 메시지 브로커와 다르게 topic이라는 것이  
event streamer에 저장됩니다.  
Event Producer가 이벤트를 생성하면 토픽이라고 불리는 이벤트 로그를 streamer에 순서대로 기록하게 됩니다.  
그 이후에 해당 토픽을 subscribe한 컨슈머에게 전달하게 됩니다.  
또한 이 토픽을 컨슈머가 가져간 이후에도 이벤트 스트림에서 계속해서 토픽을 가지고 있기 때문에  
이벤트를 다시 재생할 수도 있습니다.  
따라서 Kafka는 RabbitMQ에 비해 더 유연하고 느슨한 결합을 가지고 있으므로,  
격리와 확장이 비교적 더 쉽습니다.

※ Reference : [RabbitMQ와 Kafka의 차이? 메시지 브로커와 이벤트 스트리밍 플랫폼](https://programming-workspace.tistory.com/69)
