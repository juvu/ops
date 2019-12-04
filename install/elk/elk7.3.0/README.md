elasticsearch7.3 安装指南

注意事项：
1. 使用docker-compose安装时, 相应的配置文件移动到对应目录下
2. 这里es是集群， 10.10.10.37的es配置仅仅做了如下修改
`node.data: true`
3. filebeat的配置也放在conf上了，其核心的就是
```
#----------------------------- nsso --------------------------------
- type: log
  enabled: true
  paths:
    - /data/public-nsso/logs/*.log
  fields:
    host: "dev-public-nsso"
# 这里的 fields.host 就是适配 logstash中的 %{[fields][host]}, 以便区分索引名称

output.logstash:
  hosts: ["10.10.10.36:5044"]
```