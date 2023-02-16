# 200 Step 2 – Deploying RabbitMQ on Kubernetes

Now, we are going to deploy our custom image of RabbitMQ on Kubernetes. For the purpose of this article, we will run a standalone version of RabbitMQ. 

In that case, the only thing we need to do is to override some configuration properties in the rabbitmq.conf and enabled_plugins files. 

First, I’m enabling logging to the console at the debug level. Then I’m also enabling all the required plugins.

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: rabbitmq
  labels:
    name: rabbitmq
data:
  rabbitmq.conf: |-
    loopback_users.guest = false
    log.console = true
    log.console.level = debug
    log.exchange = true
    log.exchange.level = debug
  enabled_plugins: |-
    [rabbitmq_management,rabbitmq_prometheus,rabbitmq_tracing].
---
```
k8s/rabbitmq-deployment.yaml (only partly shown here)

Both rabbitmq.conf and enabled_plugins files should be placed inside the /etc/rabbitmq directory. Therefore, I’m mounting them inside the volume assigned to the RabbitMQ Deployment. Additionally, we are exposing three ports outside the container. The port 5672 is used in communication with applications through AMQP protocol. The Prometheus plugin exposes metrics on the dedicated port 15692. In order to access Management UI and HTTP endpoints, you should use the 15672 port.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rabbitmq
  labels:
    app: rabbitmq
spec:
  replicas: 1
  selector:
    matchLabels:
      app: rabbitmq
  template:
    metadata:
      labels:
        app: rabbitmq
    spec:
      containers:
        - name: rabbitmq
          image: vanheemstrasystems/rabbitmq-monitoring:latest
          ports:
            - containerPort: 15672
              name: http
            - containerPort: 5672
              name: amqp
            - containerPort: 15692
              name: prometheus
          volumeMounts:
            - name: rabbitmq-config-map
              mountPath: /etc/rabbitmq/
      volumes:
        - name: rabbitmq-config-map
          configMap:
            name: rabbitmq
---
```
k8s/rabbitmq-deployment.yaml (only partly shown here)

... more

*** WE ARE HERE ***
