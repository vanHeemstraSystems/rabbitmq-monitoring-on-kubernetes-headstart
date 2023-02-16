rabbitmq-monitoring-on-kubernetes-headstart
# RabbitMQ Monitoring on Kubernetes - Headstart

Based on "RabbitMQ Monitoring on Kubernetes" at https://piotrminkowski.com/2020/09/29/rabbitmq-monitoring-on-kubernetes/

RabbitMQ monitoring can be a key point of your system management. Therefore we should use the right tools for that. To enable them on RabbitMQ we need to install some plugins. In this article, I will show you how to use Prometheus and Grafana to monitor the key metrics of RabbitMQ. Of course, we will build the applications that send and receive messages. We will use Kubernetes as a target platform for our system. In the last step, we are going to enable the tracing plugin. It helps us in collecting the list of incoming messages.

## 000 Step 0 - Code your Application

See [README.md](./000/README.md)

## 100 Step 1 – Building a RabbitMQ image

See [README.md](./100/README.md)

## 200 Step 2 – Deploying RabbitMQ on Kubernetes

See [README.md](./200/README.md)
