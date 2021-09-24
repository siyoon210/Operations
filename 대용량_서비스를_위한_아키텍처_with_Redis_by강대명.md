# Chapter 0. 대규모 서비스의 특성
- SPOF
- On-premis
- IaC (Infrastructure as Code)
  - Terraform

# Chapter 1. 장애포인트를 찾기 위한 모니터링
## 징에 모니터링
- Prometheus
- Grafana
- Sentry
- Data Source(모니터링 툴 관점에서)
## 성능테스트
- Ngrinder

# Chapter 2. 대규모 서비스 설계를 위한 백엔드 에센셜
## 로드밸런서
- 소프트웨어 Load Balancer
  - Nginx, HAProxy
- Failover
- 로드밸런서 서버가 죽으면 (Failover) 어떻게 복구 되는가?
- Hop
- Client Side 로드밸런싱 vs Server Side 로드밸런싱

## 서비스 디스커버리
- 서비스 디스커버리 (Service Discovery)
- Q) Client Side 로드밸런싱을 할때 어떻게 서비스 목록을 알수 있을까?
- Q) Clinet Side 로드밸런싱에서 새로운 서버가 추가되었을때 어떻게 알 수 있을까?
- Q) Clinet Side 로드밸런싱에서 기존 서버가 제거 되었을때 어떻게 알 수 있을까?
- DNS TTL 이슈
- 서비스 디스커버리 툴 (Coordinator 라고도 함)
  - Zookeeper, Etcd, Consul, Eureka
- Feature Flag (Feature Toggle) (= 프론트서버에서 Consul을 활용하여 구현된 사항)

## 서킷브레이커 (Circuit Breaker)
- Fast Fail Back
- 서킷브레이커 상태
  - closed
  - open
  - half open
- Q) 왜 서킷브레이커가 꼭 필요한가? 서킷브레이커기 있거나 없거나 실패 API를 내려주는건 똑같을텐데?
- Side Car 패턴
- 서킷브레이커 구현체 (java)
  - Hystrix (Netflix, 더 이상 업데이트 안됨)
  - Resilience4j
