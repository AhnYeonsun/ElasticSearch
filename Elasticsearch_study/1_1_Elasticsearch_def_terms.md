# Elasticsearch_def_terms
: Elasticsearch에서 사용되는 기본 개념과 용어

* **NRT(Near Realtime)** : Elasticsearch는 NRT 검색 플랫폼. 문서를 색인화하는 시점부터 문서 검색 가능해지는 시점까지 약 1초의 대기 시간이 있다.
_ _ _

* **Cluster** : 하나 이상의 node가 모인 것. 이를 통해 전체 데이터를 저장하고 모든 node를 포괄하는 통합 색인화 및 검색 기능을 제공한다.
_ _ _

* **Node** : cluseter에 포함된 단일 서버. 데이터를 저장하고 cluster의 색인화 및 검색 기능에 참여. 하나의 cluster에서 여러 node를 포함할 수 있다.
_ _ _

* **Index** : 비슷한 특성을 가진 문서의 모음. 색인화, 검색, 업데이트, 삭제 작업에서 해당 index를 가리키는 데 쓰인다. 하나의 cluster에서 여러 index를 정의할 수 있다.
_ _ _

* **Type** : 하나의 index에서 하나 이상의 유형을 정의할 수 있다. index를 사용자 임의의 논리적으로 분류/구분한 것.
_ _ _

* **Document** : 색인화 할 수 있는 기본 정보 단위. 예를 들어 어떤 단일 고객, 단일 제품, 단일 주문에 대한 문서가 각각 존재할 수 있다. JSON 형식.
_ _ _

* **Shards** : 하나의 index가 수억개의 문서로 구성될 수 있지만 용량에 따른 검색 요청 처리 속도에 영향을 미칠 수 있다. 이에 따라 index를 shard라는 조각으로 분할하여, 각 shard는 온전히 독립적인 index의 역할을 하며, cluster의 어떤 node에서도 hosting 할 수 있다.
	- contents volumn의 수평 분할 및 확장이 가능해진다.
	- 작업을 여러 shards에 분산 배치하고 병렬화함으로써 성능 및 처리량을 늘릴 수 있다.
_ _ _

* **Replica** : network/cloud 환경에서 언제든 오류가 일어나 shard/node가 오프라인 상태가 되거나 사라지게 될 경우에 대비하여 index의 shard에 대해 하나 이상의 복사본을 생성할 수 있다.
	- shard/node 오류가 발생하여도 고가용성 제공. 따라서 replica는 원본과 동일한 node에 배정되지 않는다.
	- 모든 replica에서 병렬 방식으로 검색 실행 가능. 검색 volumn 및 처리량 확장 가능.

