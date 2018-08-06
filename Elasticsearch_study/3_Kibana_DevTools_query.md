# Kibana_DevTools_query
* Kibana에 input stream으로 넣은 데이터와 상호작용하는데 사용할 수 있는 development tools. JAVA REST api와 상호작용하기 위한 UI를 제공한다.
* Console 창에 데이터를 다룰 query를 입력하고 output을 확인할 수 있다.
* URI Search 방식과 Request Body Search 방식이 있으나, 후자의 방식이 더 상세한 표현이 가능하며 읽기 쉬운 JSON 형식으로 검색을 정의할 수 있다.

예를들어,
```
GET /bank/_search?q=*sort=acount_number:asc&pretty
```
와 같은 **URI Search** 방식을
```
GET /bank/_search
{
	"query": { "match_all": {} },
    "sort": [
    	{ "account_number": "asc" }
    ]
}
```
와 같이 **Request Body Search** 방식으로 작성할 수도 있다.
_ _ _

이 때,
```
{
  "took" : 63,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "failed" : 0
  },
  "hits" : {
    "total" : 1000,
    "max_score" : null,
    "hits" : [ {
      "_index" : "bank",
      "_type" : "account",
      "_id" : "0",
      "sort": [0],
      "_score" : null,
      "_source" : {"account_number":0,"balance":16623,"firstname":"Bradshaw","lastname":"Mckenzie","age":29,"gender":"F","address":"244 Columbus Place","employer":"Euron","email":"bradshawmckenzie@euron.com","city":"Hobucken","state":"CO"}
    }, {
      "_index" : "bank",
      "_type" : "account",
      "_id" : "1",
      "sort": [1],
      "_score" : null,
      "_source" : {"account_number":1,"balance":39225,"firstname":"Amber","lastname":"Duke","age":32,"gender":"M","address":"880 Holmes Lane","employer":"Pyrami","email":"amberduke@pyrami.com","city":"Brogan","state":"IL"}
    }, ...
    ]
  }
}
```
위와 같은 응답이 뜰 수 있는데,

* `took` : Elasticsearch가 검색을 실행하는 데 걸린 시간(ms)
* `timed_out` : 검색의 시간 초과 여부
* `_shards` : 검색한 샤드 수 및 검색에 성공/실패한 shard 수
* `hits` : 검색 결과
* `hits.total` : 검색 조건과 일치하는 문서의 총 개수
* `hits.hits` : 검색 결과의 실제 배경(default 처음 10개 docs)\
* `hits.sort` : 결과의 정렬 key
* ...

등을 가리킨다.