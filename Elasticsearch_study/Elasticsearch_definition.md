# Elasticsearch_definition
_ _ _

#### Elastic stack(ELK) = Elasticsearch + Kibana + Logstash
##### 3개의 제품들은 연동 솔루션으로 사용할 목적으로 설계됨


- - -

* Elasticsearch
	- Lucene 기반의 **검색 엔진**
	- Web interface와 schema에서 JSON 형태의 문서와 함께 ==distributed-multitenant== 지원, ==full-text 검색 엔진==을 제공한다.
	- Be available in JAVA, C#, PHP, Python...
_ _ _

* Logstash
	- 데이터 수집 및 로그 파싱 엔진
_ _ _

* Kibana
	- 데이터 분석 및 시각화 플랫폼
_ _ _

* Lucene
	- JAVA로 쓰인 정보 검색 라이브러리 오픈 소스 소프트웨어
_ _ _

* Distributed-
	- Elasticsearch는 분산 방식이므로 index를 여러 shards로 나눌 수 있으며, 각 shard는 0개 이상의 replica를 가질 수 있다.
	- shard : DB, Web 검색 엔진의 데이터의 수평 분할. 개개의 partition을 shard라고 부름. / sharding
	- 각 node는 하나 이상의 shard를 관리하며 검색 작업을 올바른 shard로 할당시켜준다. rebalancing & routing은 자동적으로 수행됨.
_ _ _

* Multitenancy
	- multiple 사용자, 즉 tenants가 하나의 application을 공유하는 architecture를 말함.
	- The application
		- running on the same OS, HW, with the same data-storage mechanism.
		- be designed to provide every tenant a dedicated share of the instance - including its data, configuration, user management, tenant individual functionality and non-functional properties.
_ _ _

* NoSQL
	- Elasticsearch는 실시간 GET 요청을 지원하여 NoSQL data store에 적합함.
	- RDB보다 덜 제한적인 일관성 모델을 이용하는 데이터 저장 및 검색을 위한 메커니즘 제공.
	- 단순 검색 및 추가 작업을 위해 최적화된 key 값 저장 공간으로, latency, throughput과 관련하여 상당한 성능 이익을 내는 것이 목적.
	- 주로 Big Data / real time web app 에서 사용된다.
