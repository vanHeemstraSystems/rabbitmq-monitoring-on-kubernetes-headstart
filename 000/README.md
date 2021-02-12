# 000 Step 0 - Code your Application

Based on "RabbitMQ Monitoring on Kubernetes" at https://piotrminkowski.com/2020/09/29/rabbitmq-monitoring-on-kubernetes/

See also "Building an Application with Spring Boot" at https://spring.io/guides/gs/spring-boot/

## 100 Requirements

- JDK 1.8 or later
- Gradle 4+ or Maven 3.2+ (this example uses Maven)

- POM file

Create the following POM file in the root diretory of the repository.

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.vanheemstrasystems</groupId>
	<artifactId>rabbitmq-monitoring-on-kubernetes-headstart</artifactId>
	<packaging>pom</packaging>
	<version>1.0</version>
	<modules>
		<module>publisher</module>
		<module>consumer</module>
	</modules>

</project>
```
pom.xml

- .gitignore file

Create the following .gitignore file in the root directory of the repository:

```
# Project exclude paths
/publisher/target/
/consumer/target/
```
.gitignore


## 200 Create Publisher

See [README.md](./200/README.md)

... MORE

## 300 Create Consumer

See [README.md](./300/README.md)

... MORE
