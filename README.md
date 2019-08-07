# kafka-stack-docker-compose
kafka &amp; zookeeper &amp; kafka-manager &amp; zookeeper ZK-Web


## zookeeper
3 z-nodes

change port:
```
zoo1:
  ports:
    - "13821:13821"
  environment:
    ZOO_PORT: 13821
  
kafka:
  environment:
    KAFKA_ZOOKEEPER_CONNECT: "zoo1:13821,zoo2:53822,zoo3:53823"
```

## kafka
3 brokers

change port:    
```
ports:
  - "13832:13832"
environment:
  KAFKA_ADVERTISED_LISTENERS: LISTENER_DOCKER_INTERNAL://kafka2:19093,LISTENER_DOCKER_EXTERNAL://kafka2:13832
```

Notes: you should modify `LISTENER_DOCKER_EXTERNAL` to `//${HOST_IP}:13832`, which ${HOST_IP} is your server's outer ip, if you want to connect kafka from remote.
