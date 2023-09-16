# Title: Choose API Gateway as Backend for Frontend

## Status

APPROVED

## Context

We want to provide a consistent and optimal user experience for our web application across different devices and platforms. We also want to reduce the complexity and maintenance cost of our frontend development.


## Decision

* We decided to use spring cloud gateway as our backend for frontend (BFF) solution. 
* bSpring cloud gateway is a library for building an API gateway on top of spring webflux, which is a reactive web framework based on project reactor. 
* Spring cloud gateway allows us to define routes that match requests based on various criteria, such as path, host, header, parameter, etc., and apply filters that can modify requests and responses before or after sending them to downstream services. 
* Spring cloud gateway also supports integration with spring cloud discovery client, circuit breaker, and request rate limiter.

We chose spring cloud gateway as our BFF solution for the following reasons:

* It is built on spring framework 6, spring boot 3, and project reactor, which are modern and popular technologies in the Java ecosystem. We can leverage the existing skills and knowledge of our development team and the rich set of features and libraries provided by these technologies.
* It is able to match routes on any request attribute, which gives us flexibility and granularity in routing requests to the appropriate backend services. We can also use predicates and filters to implement cross-cutting concerns, such as security, logging, caching, transformation, etc., in a declarative and reusable way.
* It supports circuit breaker integration, which helps us to handle failures and fallbacks gracefully when calling downstream services. We can use hystrix or resilience4j as our circuit breaker implementation and configure them according to our needs.
* It supports request rate limiter integration, which helps us to prevent overloading our backend services and protect them from denial-of-service attacks. We can use redis or in-memory as our rate limiter implementation and configure them according to our needs.
* It is easy to write custom predicates and filters using Java 8 lambda expressions or functional interfaces. We can also use existing predicates and filters provided by spring cloud gateway or third-party libraries.
* It is easy to test and debug using tools such as postman, curl, or webflux test framework. We can also use actuator endpoints to monitor and manage our gateway instance.

Alternatives considered:

* Zuul: Zuul is another API gateway solution from Netflix that is integrated with spring cloud. Zuul is based on servlet technology and uses blocking I/O. Zuul has less features and flexibility than spring cloud gateway in terms of routing and filtering. Zuul also has performance issues when handling large payloads or high concurrency.
* Custom BFF: We could also build our own BFF solution using spring webflux or other web frameworks. This would give us full control over the design and implementation of our BFF layer. However, this would also require us to reinvent the wheel for many common functionalities that are already provided by existing API gateway solutions. This would increase the complexity and maintenance cost of our frontend development.


## Consequences

By using spring cloud gateway as our BFF solution, we expect the following implications:

* Positive: We can provide a consistent and optimal user experience for our web application across different devices and platforms. We can also reduce the complexity and maintenance cost of our frontend development by delegating some responsibilities to our BFF layer.
* Negative: We need to introduce an additional layer between our frontend application and our backend services, which may increase the latency and overhead of our requests. We also need to manage the configuration and deployment of our BFF layer separately from our frontend application.

[Home Page](../README.md) | [ADR Home Page](../Architecture_Decision_Reports)