# Workshop with Asynchonous communication
* NodeJS 20
* RabbitMQ
  * Publisher/Subscriber
* Observability
  * Distributed tracing
  * Application metric

## Start RabbitMQ
```
$docker compose up -d rabbitmq
$docker compose ps
```

Access to admin page
* http://localhost:15672/
  * user=guest
  * pass=guest

## Start Jaeger
```
$docker compose up -d jaeger
$docker compose ps
```
Access to jaeger = http://localhost:16686/

## Start Prometheus
```
$docker compose build prometheus
$docker compose up -d prometheus
$docker compose ps
```
Access to jaeger = http://localhost:9090/

## Start Otel-collector
```
$docker compose up -d otel-collector
$docker compose ps
```

## Start publisher
```
$SERVICE=demo node --require './tracing.js'  publisher.js
```

## Start consumer
```
$SERVICE=consumer1 node --require './tracing.js' consumer.js
$SERVICE=consumer2 node --require './tracing.js' consumer.js
```

## Publish message
```
$curl http://localhost:3000
```