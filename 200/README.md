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
```
k8s/rabbitmq-deployment.yaml (only partly shown here)

