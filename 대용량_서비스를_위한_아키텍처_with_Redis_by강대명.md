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
- DNS vs 서비스 디스커버리
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

## Failover
- VIP (Virtual IP)
  - Q) 클라이언트 입장에서는 Failover를 알지 못하게하는 방법은 무엇이 있을까? (VIP를 이용하는 방법)
- DNS
  - Q) 클라이언트 입장에서는 Failover를 알지 못하게하는 방법은 무엇이 있을까? (DNS를 이용하는 방법)
  - DNS TTL 이슈 (Failover 방식을 DNS로 하고자 한다면 내부 DNS를 사용하여 TTL을 짧게 설정한다.)
  - 혹은 영구캐싱 하는 경우라면 에러로 발생된다.
- AWS에서 제공하는 Failover 방식은 DNS 방식으로 제공된다.
  - 그럼 만약 AWS 서버 DNS 결과값을 영구캐싱 하는 애플리케이션의 경우 문제가 생기겠군

## Replication
- primary (= master)
- secondary (= slave, replica)
- (MySQL MHA, MMA failover)
