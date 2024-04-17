# ElasKibanaDocker
Elasticsearch e Kibana no Docker

<h3>Pull das imagens do Elasticsearch e Kibana. Neste exemplo utilizaremos a versão 7.7.0. https://www.docker.elastic.com</h3>
<br>
1- docker pull docker.elastic.co/elasticsearch/elasticsearch:7.7.0
<br>
2- docker pull docker.elastic.co/kibana/kibana:7.7.0
<br>
<br>
<h3>Iniciar Containers</h3>
<br>
1- docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.7.0
<br>
2- docker run - link {Container ID do Elasticsearch}:elasticsearch -p 5601:5601 docker.elastic.co/kibana/kibana:7.7.0
<br>
<br>
-http://localhost:9200
-http://localhost:5601
<br>
<br>
<h3>Docker Compose</h3>
<br>
version: '3.7'
<br>
services:

![image](https://github.com/LeoAquino54/ElasKibanaDocker/assets/99769679/fd1a3012-a332-49fe-84ca-e0e15242229f)


<br> 
docker -compose up
