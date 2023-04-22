### Elasticsearch

#### CreateClient
```golang
cfg := elasticsearch.Config{
		Addresses: []string{"$Host"},
		Username:  "username",
		Password:  "password",
es, _ := elasticsearch.NewClient(cfg)
```

#### Index
```golang
res, err := es.Index(
		"test",                                  // Index name
		strings.NewReader(`{"title" : "Test"}`), // Document body
		es.Index.WithDocumentID("1"),            // Document ID
		es.Index.WithRefresh("true"),            // Refresh
	)
	)
```

#### Search
```golang
res, _ := es.Search(
    es.Search.WithIndex("amazon_product_us"), // Document ID
    es.Search.WithBody(strings.NewReader(`{
        "query": {
            "match_all": {
            }},"_source":"parentAsin"}`)),
	)
```