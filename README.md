# AWS 3-Tier Web Service 아키텍처 구축

개인 실습으로 3-Tier 웹 서비스 인프라 전체(VPC부터 ALB, Nginx-Tomcat 연동, RDS까지)를 먼저 구축했고, 이후 4인 팀 프로젝트에서는 인프라 설계도 작성과 구축 워크플로우 문서화를 담당했습니다.

---

## Architecture

    [ Route53 ]
         │
       [ ALB ]
         │
    ┌────┴────┐
    │ Public   │  Nginx (Reverse Proxy)
    │ Subnet   │
    └────┬────┘
         │
    ┌────┴────┐
    │ Private  │  Tomcat (WAS)
    │ Subnet   │
    └────┬────┘
         │
    ┌────┴────┐
    │ DB       │  RDS (MySQL)
    │ Subnet   │
    └─────────┘

---

## 담당 역할

4인 팀 프로젝트에서는 인프라 설계도 작성과 구축 워크플로우 문서화를 담당해, 팀원들이 따라야 할 아키텍처 청사진과 구축 순서를 제시했습니다.

---

## 구현 내용 (개인 실습)

- VPC 3계층 서브넷(Public / Private / DB) 구조 구성
- ALB를 통한 외부 트래픽 수신 및 Public Subnet의 Nginx로 라우팅
- Nginx 리버스 프록시 → Private Subnet의 Tomcat WAS로 요청 전달
- RDS(MySQL)를 DB 전용 서브넷에 격리 배치

---

## 트러블슈팅

*(기존에 작성해두신 VPC CIDR 검증 관련 트러블슈팅 섹션을 여기에 그대로 옮겨주세요)*

---

## 검증 결과

*(내일 스크린샷 추가 예정)*

- [ ] VPC/서브넷 구성 콘솔 화면
- [ ] 보안그룹 인바운드 규칙
- [ ] ALB 타겟그룹 Healthy 상태
- [ ] Nginx-Tomcat 연동 확인 (실제 접속 화면)
- [ ] RDS 인스턴스 Available 상태

---

## 발표 자료

[프로젝트 발표 자료 보기](https://github.com/gyu2001/aws-3tier-web-architecture/blob/main/aws-3tier-web-architecture.pdf)

> 위 자료는 팀 전체 프로젝트 내용을 담고 있습니다. 본인이 실제로 담당한 범위는 위 "담당 역할" 기준으로 확인하실 수 있습니다.
