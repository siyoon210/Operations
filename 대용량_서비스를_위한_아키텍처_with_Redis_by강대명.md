# Chapter 0. 대규모 서비스의 특성
- SPOF
- On-premis
- IaC (Infrastructure as Code)
  - Terraform

# Chapter 1. 장애포인트를 찾기 위한 모니터링
- Prometheus
- Grafana
- Sentry
- Data Source(모니터링 툴 관점에서)

- Ngrinder

# Chapter 2. 대규모 서비스 설계를 위한 백엔드 에센셜
- 소프트웨어 Load Balancer
  - Nginx, HAProxy
- Failover
- 로드밸런서 서버가 죽으면 (Failover) 어떻게 복구 되는가?
- Hop
- Client Side 로드밸런싱 vs Server Side 로드밸런싱

- 서비스 디스커버리 (Service Discovery)
- Q) Client Side 로드밸런싱을 할때 어떻게 서비스 목록을 알수 있을까?
- Q) Clinet Side 로드밸런싱에서 새로운 서버가 추가되었을때 어떻게 알 수 있을까?
- Q) Clinet Side 로드밸런싱에서 기존 서버가 제거 되었을때 어떻게 알 수 있을까?
- DNS TTL 이슈
- 서비스 디스커버리 툴 (Coordinator 라고도 함)
  - Zookeeper, Etcd, Consul, Eureka
