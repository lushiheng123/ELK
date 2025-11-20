# `es.indices.delete(index='my_index', ignore_unavailable=True)`删除之前的索引

# 像typescript一样，指定数据类型
```python
es.indices.delete(index='my_index', ignore_unavailable=True)
# 新写法 - 使用单独的参数
response = es.indices.create(
    index="my_index",
    settings={
        "number_of_shards": 2,
        "number_of_replicas": 1,
        "refresh_interval": "1s"
    },
    mappings={
        "properties": {
            "title": {"type": "text"},
            "author": {"type": "keyword"},
            "created_at": {"type": "date"},
            "views": {"type": "integer"}
        }
    }
)
print("新写法创建索引：")
pprint(response.body)
```
![alt text](README_Images/2-mapping/image.png)


# ` es.indices.get_settings`查看索引配置，`es.indices.get_mapping`查看数据类型
```sh
# 查看索引设置
print("=== 索引设置 ===")
settings = es.indices.get_settings(index="my_index")
pprint(settings.body)

# 查看映射
print("\n=== 索引映射 ===")
mappings = es.indices.get_mapping(index="my_index")
pprint(mappings.body)
```
![alt text](README_Images/2-mapping/image-1.png)