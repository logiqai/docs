---
description: Monitoring spring boot applications using prometheus
---

# Spring Boot

### Spring Boot Actuator and Micrometer

[Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#production-ready) is a sub-project of Spring Boot. It adds several production-grade services to your application with little effort on your part. It exposes various operational information about the running application - health, metrics, audit entries, scheduled tasks, env settings, etc. You can query the data via several HTTP endpoints. In this guide, we discuss how to enable API and other metrics using Actuator and micrometer. 

[Micrometer](https://micrometer.io) provides a simple facade over the instrumentation clients for the most popular monitoring systems, allowing you to instrument your JVM-based application code without vendor lock-in. Think SLF4J, but for metrics.

```
// Enable Actuator dependency
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>

// Enable micrometer prometheus dependency
<dependency>
  <groupId>io.micrometer</groupId>
  <artifactId>micrometer-registry-prometheus</artifactId>
  <scope>runtime</scope>
</dependency>
```

```
// Enable Actuator Endpoints in application.properties
management.endpoints.web.exposure.include=health,info,prometheus

```

Restart the server and navigate to http://localhost:\<port>/actuator/ to verifiy if the Actuator endpoints are enabled. 

![Actuator Endpoints](<../../.gitbook/assets/image (16).png>)

Navigate to `http://localhost:<port>/actuator/prometheus` and verify prometheus metrics are displayed.

![](<../../.gitbook/assets/image (12).png>)

### Enable API Timings

Micrometer comes with a [timed annotation](https://micrometer.io/docs/concepts#\_the_timed_annotation). Annotate Spring Controller methods with `@Timed `annotation. 

![](<../../.gitbook/assets/image (13).png>)

Restart the server and invoke your API's few times and navigate to `http://localhost:<port>/actuator/prometheus`, you will see the API stats displayed along with other metrics

![](<../../.gitbook/assets/image (14).png>)
