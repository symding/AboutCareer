##### [`_msearch`](https://www.elastic.co/guide/en/elasticsearch/reference/8.3/search-multi-search.html)
```json
// demo， 在kibana中，一个dsl必须占用一行，不允许分行，否则报错
GET my-index-000001/_msearch
{ }
{"query" : {"match" : { "message": "this is a test"}}}
{"index": "my-index-000002"}
{"query" : {"match_all" : {}}}

//return 
{
  "took" : 334,
  "responses" : [
  ]
}
```

