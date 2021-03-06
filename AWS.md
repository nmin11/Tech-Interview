## LoadBalancer에 대해 설명해주세요

하나의 인터넷 서비스에서 발생하는 트래픽이 많을 때 여러 대의 서버를 통해 분산 처리하여  
서버의 로드율 증가, 부하량, 속도 저하 등을 고려하여 적절히 분산처리하여 해결해주는 서비스입니다.  
로드밸런서와 관련된 주요 기능으로는 NAT, Tunneling, DSR이 있는데,  
NAT는 사설 IP를 공인 IP 주소로 변경해주는 통신망의 주소 변조기이며,  
Tunneling은 통신하는 통로를 만들고 데이터를 캡슐화해서 통로를 통한 경로로만 패킷을 구별해서 캡슐을 해제할 수 있도록 합니다.  
그리고 DSR은 로드 밸런서 사용 시 서버에서 클라이언트로 되돌아가는 경우 목적지 주소를  
스위치의 IP 주소가 아닌 클라이언트의 IP 주소로 전달해서 네트워크 스위치를 거치지 않고 바로 클라이언트를 찾아가는 개념입니다.

<br>

## 프로젝트에서 HTTPS를 적용하셨던 과정을 설명해주세요

우선 freenom이라는 도메인 호스팅 사이트에서 저희만의 도메인을 등록했고,  
AWS의 Certificate Manager를 활용해서 인증된 민간 기업인 CA로부터  
프라이빗 인증서를 발급받았습니다.  
그리고 등록했던 저희 도메인을 AWS의 Route53을 이용해서  
정상적으로 라우팅될 수 있도록 연결했습니다.

<br>

## LoadBalancer를 활용해서 여러 대의 EC2를 가동할 때 어떻게 실행 스크립트를 실행할 수 있나요?

저라면 Github Action을 사용해서 CI/CD 환경을 구축해볼 것입니다.  
똑같은 Repository를 여러 EC2에 설치하게 될것이니,  
Github 상에서 배포 스크립트를 작성해두면 편리하게 배포할 수 있을 것이리라 생각합니다.
