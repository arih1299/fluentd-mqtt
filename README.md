# fluentd-mqtt
Fluentd container with MQTT plugin and customised fluent.conf to forward logs to Solace PubSub+

```
docker build -t fluentd-mqtt:latest ./
docker run -d  --network solace-net  --name fluentd-mqtt  -p 24224:24224 -p 5140:5140 fluentd-mqtt:latest
docker run --log-driver=fluentd --log-opt tag="a/b/c/{{.ID}}" --log-opt fluentd-address=localhost:24224 python:alpine echo HelloSolace
```
