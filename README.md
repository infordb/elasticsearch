# elasticsearch

## Window 환경 Test

### Download 경로   
![image](https://user-images.githubusercontent.com/10610884/131291698-79e46ff5-aef6-4034-bde0-5f8065e3722b.png)



### Elasticsearch
https://www.elastic.co/kr/downloads/past-releases/elasticsearch-oss-7-9-3
```
관리자 권한으로
bin\elasticsearch.bat
```

high disk watermark [90%] exceeded 오류 발생 시 config 추가
```
cluster.routing.allocation.disk.threshold_enabled: false
```


### kibana
https://www.elastic.co/kr/downloads/past-releases/kibana-oss-7-9-3
```
관리자 권한
bin\kibana.bat
```
local kibana 접속   
```
localhost:5601
```




### metricbeat
https://www.elastic.co/kr/downloads/past-releases/metricbeat-oss-7-9-3

### Nori
https://artifacts.elastic.co/downloads/elasticsearch-plugins/analysis-nori/analysis-nori-7.9.3.zip
```
C:\elastic\elasticsearch-oss-7.9.3-windows-x86_64\elasticsearch-7.9.3\bin\elasticsearch-plugin install file:///C:\elastic\analysis-nori-7.9.3.zip
```


## Docker for Window

download   
https://docs.docker.com/desktop/windows/install/


### 참고 URL
opensearch : https://aws.amazon.com/ko/opensearch-service/the-elk-stack/what-is-opensearch/
