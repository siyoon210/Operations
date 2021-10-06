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
- Q) 몇대의 Secondary가 좋을까? (A)최소 2대)
- 새로운 Secondary를 붙여야 할때는 Primary에 부하가 생기는 것을 생각해야겠군..
- 읽기 분배 (읽기분배의 대표적인 방식 -> query off)
  - Q) 읽기 분배를 하는 이유는?
- Replication Lag
- Eventual Consistency
- Replication Lag을 고려하여서 읽기분배를 사용해야할지 말지 결정해야 한다.

## Sharding
- 읽기 분배외에 부하를 줄일수 있는 방식은 무엇이 있을까? (= 읽기 분배만으로 성능 향상의 한계가 있을때 고려 해봐야 하는것)
- Data Partitioning 
- Vertical partitioning
- Horizontal partitioning (Sharding)
- Q) 어떻게 데이터를 나눠야 할까?
  - 특정키를 찾는 방법 (장단점을 생각해보자)
  - Range
  - Modular
  - Indexed (단점 hint SPOF)
  - Complexed

## Consistent Hashing
- Q) Consistent Hashing은 Modular 샤딩방식의 어떤점을 보안하는가? (hint 리밸런싱)
- Q) Consistent Hashing은 장애에 안정적인가?
- Q) Consistent Hashing은 부하에 안정적인가?
- Virtual Node
- Q) Consistent Hashing에서 어떤값을 서버의 key값으로 해야할까? (IP? DNS? 유니크한 닉네임?)
- Consistent Hashing 해시코드
  - ketema hash, murmurhash3, jump hash

## GUID (Globally Unique Identifiers)
- Q)유니크한 key에 대한 요구사항이 생긴다면 어떤 방식을 써야할까?
- UUID의 한계(혹은 단점)
- Timestamp의 한계(혹은 단점)

## 비동기 큐
- Q) 비동기 큐를 이용한 작업이 필요한 경는 언제인가? (hint: latency)
- Q) 비동기 큐를 이용하여서 쓰기 작업을 할 경우, 바로 읽어 드릴때 딜레이때문에 생기는 문제를 해결하는 방식은 어떻게 할 것인가!? (hint: cache)
- sidekiq

## 배포
- Rolling Update
  - 한계는? (hint: 롤백시)
- Blue/Green
  - 한계는? (hint: On-premis 환경이라면?)
  - On-Premis에서 Blue-Green을 할려면?
- Canary Deployment
  - 카나리 배포시에 고려해야 할 점

# Chapter 3. 대규모 트래픽 처리를 위한 Redis
## Redis 기본 자료구조
- Redis, Memcached
- Key Value Store
- Cluster 모드
- Strings(K,V)
  - set/get, mset/mget (multi set, multi get)
- List(=queue, ex 잡큐)
  - lpop, rpop, lpush, rpush, blpop
- Set(ex security token)
  - sadd, sismember, srem, smembers
- Sorted Set(ex 랭크보드) (=skiplist)
  - zadd, zrange, zrevrange, zrangebyscore
- Hash (일반적인 key value 데이터를 특정군의 데이터로 묶고 싶을떄 유용)
  - hset, hget, hmset, hmget, hgetall

- 레디스는 싱글쓰레드 형태다.
  - multi, exec
- Redis Pipeline
  - 작업이 많아질때 Non-pipeline일때보다 10배정도 빠르다.
  - 실제 Redis에서 제공하는 것이 아니라 라이브러리에서 제공하는 방식
