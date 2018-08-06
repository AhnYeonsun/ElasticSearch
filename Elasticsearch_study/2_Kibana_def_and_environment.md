# Kibana_def_and_environment
#### : Elasticsearch를 위한 오픈 소스 데이터 시각화 플러그인
* Elasticsearch cluster에 indexed된 contents의 시각화 기능을 제공한다. 사용자는 대량의 데이터를 막대 그래프, 선 그림 및 분산 그림, 원형 도표와 지도의 형태로 만들 수 있다.

* Logstash가 데이터 저장 및 검색을 위한 Elastic에 input stream을 제공하고, Kibana는 데이터에 엑세스하여 시각화한다.

- - -

> Kibana에서는 다양한 데이터 visualize 및 explore부터, Elastic Stack을 관리할 툴이 존재하나, 아래 문서에서는 회사 솔루션 테스트용 로컬 DB로 검색 query 작성 및 검색 엔진 효율성 증진에 대한 업무를 스터디한 내용만 작성할 것.

- - -

> 선행되어야 할 환경 : Logstash로 데이터를 Kibana, Elastic에 넣음.
> 실제 검색 시에 필요한 한글 분석기 arirang plugin, 문서 색인 전 데이터 전처리 전용 노드 ingest plugin을 연결.