# ElasKibanaDocker
Elasticsearch e Kibana no Docker

<h1>Pull das imagens do Elasticsearch e Kibana. Neste exemplo utilizaremos a versão 7.7.0. https://www.docker.elastic.com</h1>
<br>
1- docker pull docker.elastic.co/elasticsearch/elasticsearch:7.7.0
<br>
2- docker pull docker.elastic.co/kibana/kibana:7.7.0
<br>
<br>
<h1>Iniciar Containers</h1>
<br>
1- docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.7.0
<br>
2- docker run - link {Container ID do Elasticsearch}:elasticsearch -p 5601:5601 docker.elastic.co/kibana/kibana:7.7.0
<br>
<br>
- <h2></h2>http://localhost:9200</h2>
-<h2>http://localhost:5601</h2>
<br>
<br>
<h1>Docker Compose</h1>
<br>
version: '3.7'
services:

  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.7.0
    ports:
      - "9200:9200"
      - "9300:9300"
    environment:
      discovery.type: "single-node"
      ES_JAVA_OPTS: "-Xms2g -Xmx2g"
      xpack.monitoring.enabled: "true"
    volumes:
      - ./esdata:/usr/share/elasticsearch/data
      
  kibana:
    image: docker.elastic.co/kibana/kibana:7.7.0
    ports:
      - "5601:5601"
    environment:
      ELASTICSEARCH_URL: http://elasticsearch:9200
    depends_on:
      - elasticsearch
      
volumes:
  esdata:
    driver: local

<br> 
docker -compose up
