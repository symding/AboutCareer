> [Elasitc](https://www.elastic.co/guide/en/elasticsearch/reference/7.10/snapshots-restore-snapshot.html?spm=5176.smartservice_service_chat.0.0.75453f1bK7evDL)
#### `datastream` restore
直接恢复 `datastream` 的后备索引并不会直接恢复 `datastream`,需要建立好相关的索引模版后直接恢复 `datastream` 名
```json
POST _snapshot/aliyun_snapshot/snapshot_name/_restore
{
"indices": "datastream_name"
}

```
