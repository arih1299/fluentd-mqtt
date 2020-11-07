# fluentd-mqtt
Fluentd container with MQTT plugin and customised fluent.conf to forward logs to Solace PubSub+

To build and run this docker container:
```
docker build -t fluentd-mqtt:latest ./
docker run -d  --network solace-net  --name fluentd-mqtt  -p 24224:24224 -p 5140:5140 fluentd-mqtt:latest
```

To test, run this simple container that will simply echo "HelloSolace" string which will then get picked up and the tag will be used as the destination topic by the MQTT output plugin.
```
docker run --log-driver=fluentd --log-opt tag="acme/clusterx/appz/{{.ID}}" --log-opt fluentd-address=localhost:24224 python:alpine echo HelloSolace
```

For reference on docker tag please see here https://docs.docker.com/config/containers/logging/log_tags/
