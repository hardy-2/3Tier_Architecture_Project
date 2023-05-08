# 3Tier_Architecture_Project
![3tier](https://user-images.githubusercontent.com/73948888/236825582-aaed858d-bdfc-4fdf-8914-38729ede3b7b.png)

## 💻 맡은 역할

프로젝트 팀장, VPN, DNS, CDN, Azure Files 설정, 모니터링 및 알람 설정, 웹 서비스 설정, SSL 인증서 발행

## 📖 상세 내용

Azure의 다양한 리소스들을 이용하여 3Tier 아키텍처를 구축하고 웹 서비스를 배포 한다.

****P2S VPN****

- 관리자는 점프박스(Bastion)에 접속할 때 Azure의 P2S VPN으로 접속

******DNS******

A Record

- application gateawy ip를 구매한 도메인 주소로 연결

**CDN**

- 정적 콘텐츠 캐싱
- Blob Storage와 CDN을 연동
- 웹페이지 코드에서 정적인 파일 주소 경로로 변경

**********AGW**********

- Web 서버를 부하 분산
- 백 엔드 풀을 VMSS로 설정 및 연결
- SSL인증서 등록 → https

**LB**

- 내부 로브 밸런서를 이용
- WAS를 부하 분산
- 백 엔드 풀은 VMSS로 설정 및 연결

**VMSS**

- VM에서 미리 Web, WAS 서버의 골든 이미지 생성
- CPU 사용량에 따라 자동으로 Scale Out, Scale In(Auto Scaling)

**DB**

- Private Endpoint를 통해서만 DB를 연결
    - 보안성 향상

**Azure Files**

- 골든 이미지 생성시 미리 아파치, 톰캣의 접속로그 등을 마운트

********************Monitoring********************

- Azure Monitor를 사용
- Jmeter로 트래픽 부하 테스트
    - AGW 트래픽 증가수를 파악
- 스트레스 테스트
    - CPU 사용량 증가
    - AutoScaling 동작확인
- Alert
    - CPU가 일정 사용량이 넘어가면 이메일로 알림

**웹서비스**

- 아파치-Tomcat-Mysql 연결
    - apache reverse proxy
    
## 😀시연 영상

[https://www.youtube.com/watch?v=KQRGf0gE7ho&ab_channel=%EC%9D%B4%EC%B0%BD%ED%9D%AC](https://www.youtube.com/watch?v=KQRGf0gE7ho&ab_channel=%EC%9D%B4%EC%B0%BD%ED%9D%AC)

## 😀시연 사진

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57e6b5e7-1506-4542-b3c9-26cafc9e6b18/Untitled.png)

---

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d083284c-0fe5-4ac7-b4cf-116691297674/Untitled.png)

---

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/afda6af1-5f21-4be6-b495-b887da9e0060/Untitled.png)
