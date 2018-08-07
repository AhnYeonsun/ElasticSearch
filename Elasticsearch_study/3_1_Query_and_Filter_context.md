# Query_and_Filter_context
: 쿼리문의 동작은 query context에서 사용되는지 filter context에서 사용되는지에 따라 달라진다.

### ==Query context==
##### : "How well does this document match this query clause?"

* Query context에서 쿼리문은 이 문서가 쿼리문과 얼마나 잘 일치하는지에 대한 여부와
* 다른 문서에 비해 match된 문서가 얼마나 잘 일치하는지를 나타내는 점수도 계산한다.

### ==Filter context==
##### : "Does this document match this query clause?"

* Filter context에서 쿼리문은 쿼리문과 문서가 일치하는가? YES/NO 로만 답하여 따로 점수 계산을 하지 않는다.
* 주로 구조화된 데이터를 filtering하는 데 사용된다.
* 자주 사용하는 filter는 성능 속도를 높이기 위해 Elasticsearch에 의해 자동으로 캐싱된다.
* Filter context는 쿼리문이 filter 매개 변수로 전달될 때마다 유효하다. 예를들어,
	- bool query의 'filter'나 'must_not' 매개 변수,
	- constant_score query의 'filter' 매개 변수,
	- filter aggregation 시에.

- - -

아래는 search API의 query 및 filter context에 사용되는 쿼리문의 예이다.
```
GET /_search
{
  "query": { 
    "bool": { 
      "must": [
        { "match": { "title":   "Search"        }}, 
        { "match": { "content": "Elasticsearch" }}  
      ],
      "filter": [ 
        { "term":  { "status": "published" }}, 
        { "range": { "publish_date": { "gte": "2015-01-01" }}} 
      ]
    }
  }
}
```
* bool 에서는 match 를, filter 에서는 term, range 와 같은 절을 사용한다.
* 일치하는 문서의 점수에 영향을 주는 조건은 query context에, 다른 모든 조건들은 filter context에 질의 절을 사용한다.