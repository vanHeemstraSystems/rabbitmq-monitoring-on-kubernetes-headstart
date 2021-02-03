# 100 Step 1 – Building a RabbitMQ image

In the first step, we are overriding the Docker image of RabbitMQ. In that case, we need to extend the base image with a tag 3-management and add two plugins. The plugin rabbitmq_prometheus adds Prometheus exporter of core RabbitMQ metrics. The second of them, rabbitmq_tracing allows us to log the payloads of incoming messages. That’s all that we need to define in our Dockerfile, which is visible below.

| | rabbitmq-monitoring | |
| -- | -- | -- |
| | plugin | |
| | Base Image: rabbitmq:3-management | |

vanheemstrasystems/rabbitmq-monitoring

```
FROM rabbitmq:3-management
RUN rabbitmq-plugins enable --offline rabbitmq_prometheus rabbitmq_tracing
```
dockerfile

Then you just need to build an already defined image. Let’s say its name is vanheemstrasystems/rabbitmq-monitoring. After building I’m pushing it to my remote Docker registry.

```
$ docker build -t vanheemstrasystems/rabbitmq-monitoring .
$ docker push vanheemstrasystems/rabbitmq-monitoring
```
