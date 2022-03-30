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
