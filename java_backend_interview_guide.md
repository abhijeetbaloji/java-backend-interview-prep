# Java Backend Interview Question Bank — 300 Questions (Concept-wise)

Serially numbered 1–300, organized by concept rather than priority tier, so you can study one subject end-to-end. Each question still carries a **Priority** (P1 = must-know, asked almost everywhere → P4 = advanced, senior/product-company loops), **Difficulty**, **Frequency** (★★★★★ = near-universal), and the companies most likely to ask it. No answers included by design.

---

### 1. Java Core
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 1 | `==` vs `.equals()`, and why `hashCode()`/`equals()` must be overridden together | P1 | Easy | ★★★★★ | Amazon, Microsoft, Google, Adobe |
| 2 | String immutability and the String pool — why is String immutable? | P1 | Easy | ★★★★★ | Amazon, Flipkart, Infosys, TCS |
| 3 | Abstract class vs interface — when to use which | P1 | Easy | ★★★★★ | Microsoft, Cisco, Visa, Capgemini |
| 4 | Method overloading vs overriding, with edge cases (covariant return types, static methods) | P1 | Medium | ★★★★☆ | Amazon, Google, Oracle |
| 5 | Checked vs unchecked exceptions; when to create a custom exception | P1 | Easy | ★★★★★ | Amazon, JPMorgan, Wipro |
| 6 | Java's pass-by-value semantics, especially for objects | P1 | Medium | ★★★★☆ | Microsoft, Atlassian, Goldman Sachs |
| 7 | Functional interfaces: `Runnable`, `Callable`, `Supplier`, `Function` | P1 | Medium | ★★★★☆ | Amazon, Adobe, ServiceNow |
| 8 | `final` vs `finally` vs `finalize()` | P1 | Easy | ★★★☆☆ | TCS, Infosys, Cognizant |
| 9 | Primitives vs wrapper classes, and autoboxing pitfalls | P2 | Easy | ★★★★☆ | Amazon, Microsoft, Infosys |
| 10 | Composition vs inheritance — when do you prefer composition? | P2 | Medium | ★★★★☆ | Amazon, Google, Adobe |
| 11 | Static vs instance methods/variables, and static initialization order | P1 | Easy | ★★★★☆ | Amazon, TCS, Capgemini |
| 12 | The diamond problem — how does Java resolve it with default methods? | P2 | Medium | ★★★☆☆ | Oracle, Cisco |
| 13 | Designing an immutable class in Java | P2 | Medium | ★★★★☆ | Amazon, Microsoft, JPMorgan |
| 14 | Shallow copy vs deep copy, and implementing `clone()` correctly | P2 | Medium | ★★★☆☆ | Amazon, Adobe |
| 15 | Enums beyond constants — can they implement interfaces or have methods? | P3 | Easy | ★★★☆☆ | Microsoft, Oracle |

### 2. Java Collections
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 16 | Internal working of `HashMap` (hashing, buckets, treeification in Java 8+) | P1 | Hard | ★★★★★ | Amazon, Google, Microsoft, Flipkart |
| 17 | `HashMap` vs `LinkedHashMap` vs `TreeMap`, with use cases | P1 | Medium | ★★★★★ | Amazon, Adobe, Visa |
| 18 | `ArrayList` vs `LinkedList` — when to use which | P1 | Easy | ★★★★★ | Microsoft, Infosys, Capgemini |
| 19 | How `ConcurrentHashMap` achieves thread safety without locking the whole map | P1 | Hard | ★★★★☆ | Amazon, Uber, LinkedIn |
| 20 | `Comparable` vs `Comparator` with a real use case | P1 | Medium | ★★★★☆ | Microsoft, JPMorgan, Cisco |
| 21 | Why `HashMap` isn't thread-safe (pre-Java 8 infinite loop on resize) | P1 | Medium | ★★★★☆ | Amazon, Google |
| 22 | `Iterator` vs `ListIterator`; fail-fast vs fail-safe iterators | P1 | Medium | ★★★★☆ | Adobe, Oracle, Wipro |
| 23 | `Set`/`List`/`Map` implementations and their time complexities | P1 | Medium | ★★★★☆ | Flipkart, Swiggy, Zomato |
| 24 | Array vs `ArrayList`, and when arrays are still preferable | P2 | Easy | ★★★☆☆ | Amazon, Infosys |
| 25 | `PriorityQueue` internals and a real-world use case | P2 | Medium | ★★★★☆ | Amazon, Microsoft, Flipkart |
| 26 | `Vector` vs `Stack` vs `ArrayDeque` | P3 | Easy | ★★★☆☆ | TCS, Wipro |
| 27 | How `equals()`/`hashCode()` contracts affect collection correctness (mutable keys in a `HashMap`) | P2 | Medium | ★★★★☆ | Amazon, JPMorgan |
| 28 | Immutable collections in Java (`List.of()`, `Collections.unmodifiableList`) | P2 | Easy | ★★★☆☆ | Amazon, Adobe |

### 3. Java Concurrency
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 29 | The Java Memory Model and the concept of happens-before | P1 | Hard | ★★★★★ | Amazon, Google, Microsoft, Goldman Sachs |
| 30 | `synchronized` vs `ReentrantLock` vs `volatile` | P1 | Medium | ★★★★★ | Amazon, JPMorgan, Visa |
| 31 | What is a deadlock? How do you detect and prevent it in production? | P1 | Medium | ★★★★★ | Microsoft, Atlassian, Oracle |
| 32 | Executor framework and the difference between thread pool types | P1 | Medium | ★★★★★ | Amazon, Uber, LinkedIn |
| 33 | Virtual Threads (Project Loom, Java 21) vs platform threads | P1 | Medium | ★★★★☆ | Amazon, Google, Netflix |
| 34 | `CompletableFuture` vs `Future` | P1 | Medium | ★★★★☆ | Amazon, Adobe, ServiceNow |
| 35 | `CountDownLatch` vs `CyclicBarrier` vs `Semaphore` | P1 | Medium | ★★★☆☆ | Microsoft, Cisco |
| 36 | Debugging a production thread-dump showing high CPU usage | P1 | Hard | ★★★★☆ | Amazon, Goldman Sachs, Morgan Stanley |
| 37 | `ThreadLocal`, a real use case, and its memory leak risks | P2 | Medium | ★★★★☆ | Amazon, JPMorgan, Visa |
| 38 | Implementing a custom thread-safe cache without a library | P2 | Hard | ★★★☆☆ | Amazon, Google, Uber |
| 39 | Producer-consumer pattern using `BlockingQueue` | P2 | Medium | ★★★★☆ | Amazon, Microsoft, Flipkart |
| 40 | False sharing and its impact on multithreaded performance | P2 | Hard | ★★☆☆☆ | Google, Netflix |
| 41 | Race conditions — a real code example and how you'd fix it | P2 | Medium | ★★★★☆ | Amazon, Microsoft |
| 42 | Fork/Join framework vs `ExecutorService` for parallel tasks | P3 | Hard | ★★★☆☆ | Amazon, Google |
| 43 | Implementing a custom thread pool with a bounded queue and rejection policy | P3 | Hard | ★★★☆☆ | Amazon, Uber |

### 4. Java Memory Management
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 44 | JVM memory areas: heap, stack, metaspace, PC register | P1 | Medium | ★★★★★ | Amazon, Microsoft, Oracle |
| 45 | Garbage Collection fundamentals (generational, minor vs major GC) | P1 | Medium | ★★★★★ | Amazon, Google, Adobe |
| 46 | Diagnosing `OutOfMemoryError` / memory leaks in production | P1 | Hard | ★★★★★ | Amazon, JPMorgan, Visa |
| 47 | Strong, Weak, Soft, and Phantom references | P1 | Hard | ★★★☆☆ | Amazon, Google |
| 48 | G1GC vs ZGC vs Parallel GC, and when to choose each | P2 | Hard | ★★★☆☆ | Netflix, Uber, LinkedIn |
| 49 | Tuning GC parameters for a low-latency Java service | P4 | Hard | ★★★☆☆ | Netflix, Uber, Goldman Sachs |
| 50 | Analyzing a heap dump to find a memory leak (Eclipse MAT) | P4 | Hard | ★★★★☆ | Amazon, JPMorgan, Visa |

### 5. Java JVM
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 51 | Class loading and the classloader hierarchy | P1 | Medium | ★★★☆☆ | Oracle, Cisco, Intel |
| 52 | JIT compilation and how it affects application warm-up/performance | P2 | Medium | ★★★☆☆ | Amazon, Google, Oracle |
| 53 | JIT de-optimization, and how it can cause performance regressions | P4 | Hard | ★★☆☆☆ | Google, Netflix |
| 54 | Off-heap memory usage in Java — when would you use it? | P4 | Hard | ★★☆☆☆ | Amazon, Netflix |
| 55 | Bytecode and how the JVM executes a `.class` file | P3 | Medium | ★★★☆☆ | Oracle, Microsoft |
| 56 | Escape analysis — how it enables stack allocation of objects | P3 | Hard | ★★☆☆☆ | Google, Amazon |
| 57 | Reducing GC pause times for a service handling millions of requests/day | P4 | Hard | ★★★☆☆ | Netflix, Uber, LinkedIn |

### 6. Java 8+ / Functional Programming
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 58 | Streams API: `map`, `filter`, `reduce`, `collect` with real-world examples | P1 | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 59 | Intermediate vs terminal operations, and lazy evaluation in streams | P1 | Medium | ★★★★☆ | Amazon, Adobe |
| 60 | `Optional` and best practices for avoiding null checks | P1 | Easy | ★★★★☆ | Microsoft, Visa, Infosys |
| 61 | Default and static methods in interfaces — why were they introduced? | P1 | Easy | ★★★☆☆ | Oracle, Cisco |
| 62 | Records, sealed classes, and pattern matching in recent Java versions | P1 | Medium | ★★★☆☆ | Amazon, Google, Netflix |
| 63 | How parallel streams work internally, and when to avoid them | P1 | Hard | ★★★☆☆ | Amazon, Uber |
| 64 | Method references and how they relate to lambdas under the hood | P2 | Easy | ★★★☆☆ | Amazon, Microsoft |
| 65 | `Collectors.toMap()` pitfalls vs `groupingBy()` with downstream collectors | P2 | Medium | ★★★★☆ | Amazon, Flipkart |

### 7. Spring Core
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 66 | Dependency Injection and Inversion of Control with real examples | P1 | Easy | ★★★★★ | Amazon, Microsoft, TCS |
| 67 | `@Component` vs `@Service` vs `@Repository` vs `@Controller` | P1 | Easy | ★★★★★ | Infosys, Capgemini, Wipro |
| 68 | Spring Bean lifecycle and scopes (singleton, prototype, request, session) | P1 | Medium | ★★★★★ | Amazon, Adobe, Visa |
| 69 | Circular dependency in Spring — how do you resolve it? | P1 | Medium | ★★★★☆ | Microsoft, JPMorgan |
| 70 | How `@Autowired` works internally — constructor vs field injection | P1 | Medium | ★★★★☆ | Amazon, Oracle |
| 71 | `ApplicationContext` vs `BeanFactory` | P2 | Easy | ★★★☆☆ | Amazon, Microsoft |
| 72 | How Spring AOP works internally (JDK dynamic proxy vs CGLIB) | P2 | Hard | ★★★★☆ | Amazon, Adobe, Oracle |

### 8. Spring Boot
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 73 | Spring Boot auto-configuration and how `@SpringBootApplication` works internally | P1 | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 74 | Global exception handling (`@ControllerAdvice`, `@ExceptionHandler`) | P1 | Medium | ★★★★★ | Amazon, Visa, Razorpay |
| 75 | Starter dependencies and the embedded server (Tomcat/Netty) | P1 | Medium | ★★★★☆ | Adobe, ServiceNow |
| 76 | Externalizing config across environments (profiles, `application.yml`) | P1 | Easy | ★★★★★ | Amazon, JPMorgan, PhonePe |
| 77 | Spring Boot Actuator for production health checks | P1 | Medium | ★★★★☆ | Netflix, Uber, Swiggy |
| 78 | Bean validation (`@Valid`, custom validators) | P1 | Easy | ★★★★☆ | Amazon, Microsoft |
| 79 | WebMVC (servlet-based) vs WebFlux (reactive) | P1 | Hard | ★★★★☆ | Amazon, Netflix, Uber |
| 80 | Securing sensitive configuration (DB passwords, API keys) | P1 | Medium | ★★★★☆ | Visa, Mastercard, JPMorgan |
| 81 | How `@ConditionalOn...` annotations drive auto-configuration decisions | P2 | Medium | ★★★☆☆ | Amazon, Adobe |
| 82 | Building a custom Spring Boot starter for internal reuse | P3 | Hard | ★★★☆☆ | Amazon, Microsoft |
| 83 | Spring Boot DevTools and how hot-reload works in development | P3 | Easy | ★★☆☆☆ | Infosys, TCS |
| 84 | Graceful shutdown in Spring Boot, and why it matters for Kubernetes deployments | P2 | Medium | ★★★★☆ | Amazon, Netflix, Uber |
| 85 | Scheduled tasks (`@Scheduled`) and their pitfalls in a clustered deployment | P2 | Medium | ★★★★☆ | Amazon, Swiggy |

### 9. Spring MVC
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 86 | `DispatcherServlet` request lifecycle in Spring MVC | P2 | Medium | ★★★★☆ | Amazon, Microsoft, Oracle |
| 87 | `@RequestParam` vs `@PathVariable` vs `@RequestBody` | P1 | Easy | ★★★★★ | Amazon, Infosys, TCS |
| 88 | How Spring MVC handles content negotiation (JSON vs XML responses) | P3 | Medium | ★★★☆☆ | Amazon, Adobe |
| 89 | `HandlerInterceptor` vs `Filter` — when to use each | P2 | Medium | ★★★★☆ | Amazon, Microsoft |
| 90 | Implementing custom request/response logging across all endpoints | P3 | Medium | ★★★☆☆ | Amazon, JPMorgan |

### 10. REST APIs
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 91 | What makes an API RESTful? REST constraints and statelessness | P1 | Easy | ★★★★★ | Amazon, Microsoft, Flipkart |
| 92 | Idempotency in REST APIs — which HTTP methods are idempotent | P1 | Medium | ★★★★★ | Amazon, Razorpay, PhonePe |
| 93 | API versioning strategies and their trade-offs | P1 | Medium | ★★★★☆ | Microsoft, Adobe, Atlassian |
| 94 | Proper HTTP status code usage (200/201/204/400/422/500) | P1 | Easy | ★★★★★ | Amazon, Infosys, TCS |
| 95 | Designing pagination, filtering, and sorting in a REST API | P1 | Medium | ★★★★☆ | Amazon, Flipkart, Swiggy |
| 96 | API rate limiting and throttling at the application layer | P1 | Medium | ★★★★☆ | Amazon, Uber, Razorpay |
| 97 | HATEOAS — what is it, and is it worth implementing in practice? | P3 | Medium | ★★☆☆☆ | Amazon, Oracle |
| 98 | Designing consistent error response contracts across an API | P2 | Medium | ★★★★☆ | Amazon, JPMorgan, Visa |
| 99 | Synchronous request/response vs webhook-based API design | P2 | Medium | ★★★★☆ | Amazon, Razorpay, PhonePe |
| 100 | Designing backward-compatible API changes without breaking clients | P2 | Medium | ★★★★☆ | Amazon, Microsoft |
| 101 | gRPC vs REST — trade-offs for internal service-to-service communication | P3 | Medium | ★★★☆☆ | Amazon, Netflix, Uber |

### 11. Hibernate
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 102 | `save()` vs `persist()` vs `merge()` vs `saveOrUpdate()` | P1 | Medium | ★★★★★ | Amazon, Infosys, Capgemini |
| 103 | The N+1 select problem and how to solve it | P1 | Hard | ★★★★★ | Amazon, Microsoft, Flipkart |
| 104 | First-level vs second-level cache | P1 | Medium | ★★★★☆ | Amazon, Adobe, Oracle |
| 105 | `FetchType.LAZY` vs `EAGER`, and `LazyInitializationException` | P1 | Medium | ★★★★★ | Amazon, JPMorgan, Visa |
| 106 | Entity state transitions: transient, persistent, detached, removed | P1 | Medium | ★★★☆☆ | Microsoft, Oracle |
| 107 | Hibernate's dirty checking mechanism and how it triggers updates | P2 | Medium | ★★★★☆ | Amazon, Microsoft |
| 108 | Primary key generation strategies (IDENTITY vs SEQUENCE vs TABLE) | P2 | Medium | ★★★☆☆ | Amazon, JPMorgan |
| 109 | Cascading types (`CascadeType.ALL`, `PERSIST`, `MERGE`) and their risks | P2 | Medium | ★★★★☆ | Amazon, Adobe |
| 110 | Batch inserting/updating thousands of records efficiently with Hibernate | P2 | Hard | ★★★★☆ | Amazon, Flipkart, JPMorgan |
| 111 | HQL vs JPQL vs native SQL queries in Hibernate | P3 | Easy | ★★★☆☆ | Infosys, TCS |

### 12. JPA
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 112 | `@Transactional` propagation and isolation in Spring | P1 | Hard | ★★★★☆ | Amazon, Goldman Sachs |
| 113 | `@OneToMany`, `@ManyToOne`, `@ManyToMany` mappings with `mappedBy` | P1 | Medium | ★★★★★ | Amazon, Microsoft, Infosys |
| 114 | `JpaRepository` vs `CrudRepository` | P2 | Easy | ★★★★☆ | Amazon, TCS |
| 115 | Custom queries via `@Query` and derived query methods | P2 | Easy | ★★★★☆ | Amazon, Infosys |
| 116 | Why overriding `equals`/`hashCode` on JPA entities is tricky | P3 | Hard | ★★★☆☆ | Amazon, JPMorgan |
| 117 | Optimistic locking with `@Version` in JPA | P2 | Medium | ★★★★☆ | Amazon, Flipkart, Razorpay |
| 118 | Spring Data JPA's pagination and sorting support (`Pageable`) | P2 | Easy | ★★★★☆ | Amazon, Microsoft |
| 119 | Handling a many-to-many relationship with extra attributes (join entity) | P3 | Medium | ★★★☆☆ | Amazon, Adobe |
| 120 | JPA entity lifecycle callbacks (`@PrePersist`, `@PostLoad`) | P3 | Easy | ★★★☆☆ | Amazon, Oracle |

### 13. SQL
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 121 | INNER JOIN vs LEFT JOIN vs RIGHT JOIN vs FULL JOIN, with examples | P1 | Easy | ★★★★★ | Amazon, Microsoft, JPMorgan |
| 122 | Clustered vs non-clustered indexes | P1 | Medium | ★★★★★ | Amazon, Goldman Sachs, Visa |
| 123 | ACID properties and how a database enforces them | P1 | Medium | ★★★★★ | Amazon, Microsoft, Oracle |
| 124 | Write a query to find the Nth highest salary/record | P1 | Medium | ★★★★★ | Amazon, Flipkart, Infosys |
| 125 | Database normalization (1NF/2NF/3NF) and when to denormalize | P1 | Medium | ★★★★☆ | Microsoft, JPMorgan, TCS |
| 126 | `WHERE` vs `HAVING` | P1 | Easy | ★★★★☆ | Amazon, Cognizant, Wipro |
| 127 | Identifying and fixing a slow SQL query in production (EXPLAIN plan) | P1 | Hard | ★★★★★ | Amazon, Goldman Sachs, Morgan Stanley |
| 128 | Transaction isolation levels and the anomalies they prevent | P1 | Hard | ★★★★☆ | Amazon, JPMorgan, Visa |
| 129 | Window functions (`RANK`/`ROW_NUMBER`/`DENSE_RANK`) for a real scenario | P2 | Medium | ★★★★☆ | Amazon, JPMorgan, Flipkart |
| 130 | `GROUP BY` with aggregates and common pitfalls (non-aggregated columns) | P2 | Easy | ★★★★☆ | Amazon, Infosys |
| 131 | `UNION` vs `UNION ALL`, and performance implications | P2 | Easy | ★★★☆☆ | Amazon, TCS |
| 132 | Correlated vs non-correlated subqueries | P2 | Medium | ★★★★☆ | Amazon, Microsoft |
| 133 | Detecting and safely deleting duplicate records | P2 | Medium | ★★★★☆ | Amazon, Flipkart, JPMorgan |
| 134 | Composite indexes and why column order matters | P3 | Medium | ★★★☆☆ | Amazon, Goldman Sachs |
| 135 | Database-level deadlocks and how you'd debug one in production | P3 | Hard | ★★★★☆ | Amazon, JPMorgan, Visa |

### 14. Database Design
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 136 | Designing a database schema for an e-commerce order system | P2 | Medium | ★★★★★ | Amazon, Flipkart, Swiggy |
| 137 | Sharding vs partitioning, and when you'd use each | P2 | Hard | ★★★★☆ | Amazon, Uber, Netflix |
| 138 | Schema design for soft deletes and audit trails | P2 | Medium | ★★★☆☆ | Microsoft, JPMorgan |
| 139 | Optimistic vs pessimistic locking with a real scenario (inventory update) | P2 | Medium | ★★★★☆ | Amazon, Flipkart, Razorpay |
| 140 | Database replication and handling replication lag | P2 | Medium | ★★★★☆ | Amazon, Uber, PhonePe |
| 141 | Schema design for a multi-tenant SaaS application | P2 | Hard | ★★★☆☆ | Salesforce, ServiceNow, Freshworks |
| 142 | SQL vs NoSQL — when would you pick a document/key-value store? | P2 | Medium | ★★★★★ | Amazon, Flipkart, PhonePe |
| 143 | Schema design for time-series data (metrics, events) | P3 | Medium | ★★★☆☆ | Amazon, Netflix |
| 144 | Connection pooling and why unbounded connections cause outages | P2 | Medium | ★★★★☆ | Amazon, JPMorgan, Visa |
| 145 | Schema design for versioned/auditable records (e.g., pricing history) | P3 | Medium | ★★★☆☆ | Amazon, Visa |
| 146 | Eventual consistency — designing a process to reconcile it | P3 | Hard | ★★★★☆ | Amazon, Uber, Flipkart |

### 15. Microservices
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 147 | Microservices vs monolith — when would you NOT choose microservices? | P2 | Medium | ★★★★★ | Amazon, Netflix, Uber |
| 148 | Sync vs async microservice communication, and the trade-offs | P2 | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 149 | Saga pattern for distributed transactions — choreography vs orchestration | P2 | Hard | ★★★★★ | Amazon, Uber, Razorpay |
| 150 | Service discovery in a microservices architecture | P2 | Medium | ★★★★☆ | Amazon, Netflix, Swiggy |
| 151 | Circuit Breaker pattern (Resilience4j/Hystrix) | P2 | Medium | ★★★★★ | Amazon, Netflix, PhonePe |
| 152 | Data consistency across microservices owning separate databases | P2 | Hard | ★★★★★ | Amazon, Uber, Flipkart |
| 153 | What is an API Gateway, and what responsibilities does it handle? | P2 | Medium | ★★★★☆ | Amazon, Netflix, Zomato |
| 154 | Distributed logging and tracing across microservices | P2 | Hard | ★★★★☆ | Amazon, Uber, LinkedIn |
| 155 | Strangler Fig pattern for migrating a monolith to microservices | P3 | Medium | ★★★☆☆ | Amazon, Microsoft |
| 156 | Versioning internal service contracts (API/event schemas) | P3 | Medium | ★★★★☆ | Amazon, Uber |
| 157 | Database-per-service pattern and handling cross-service joins | P2 | Medium | ★★★★☆ | Amazon, Flipkart |
| 158 | Rolling back a distributed transaction when one service call fails midway | P3 | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 159 | Bulkhead pattern — isolating failures between services | P3 | Medium | ★★★☆☆ | Amazon, Netflix |
| 160 | Contract testing between producer and consumer microservices (Pact) | P3 | Medium | ★★★☆☆ | Amazon, Atlassian |
| 161 | Common microservices anti-patterns (e.g., distributed monolith) | P3 | Hard | ★★★★☆ | Amazon, Netflix, Uber |

### 16. Kafka
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 162 | Kafka architecture: topics, partitions, brokers, consumer groups | P2 | Medium | ★★★★★ | Amazon, Uber, LinkedIn |
| 163 | How Kafka guarantees message ordering, and trade-offs of multiple partitions | P2 | Hard | ★★★★☆ | Amazon, Uber, Swiggy |
| 164 | At-most-once, at-least-once, exactly-once delivery semantics | P2 | Hard | ★★★★★ | Amazon, Flipkart, PhonePe |
| 165 | Handling a Kafka consumer lag issue in production | P2 | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 166 | Role of ZooKeeper/KRaft in Kafka, and how leader election works | P2 | Medium | ★★★☆☆ | Amazon, LinkedIn |
| 167 | Designing a retry and dead-letter-queue mechanism for failed messages | P2 | Medium | ★★★★☆ | Amazon, Swiggy, Zomato |
| 168 | Designing a Kafka topic partitioning strategy for a multi-tenant system | P4 | Hard | ★★★☆☆ | Amazon, Uber, LinkedIn |
| 169 | Kafka Streams vs a traditional consumer-based processing approach | P4 | Hard | ★★★☆☆ | Amazon, LinkedIn |
| 170 | Handling schema evolution in Kafka messages (Avro/Schema Registry) | P4 | Hard | ★★★☆☆ | Amazon, Uber |
| 171 | Kafka vs RabbitMQ vs SQS for different messaging use cases | P4 | Medium | ★★★★☆ | Amazon, Swiggy, Razorpay |
| 172 | Consumer rebalancing and how it can cause duplicate processing | P3 | Hard | ★★★★☆ | Amazon, Uber, LinkedIn |
| 173 | Ensuring message ordering across multiple consumers for a given key | P3 | Medium | ★★★★☆ | Amazon, Razorpay |

### 17. Redis
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 174 | Common Redis use cases (caching, sessions, rate limiting) | P2 | Easy | ★★★★★ | Amazon, Flipkart, Razorpay |
| 175 | Redis eviction policies and how you'd choose one for a caching layer | P2 | Medium | ★★★★☆ | Amazon, Swiggy, PhonePe |
| 176 | Implementing a distributed lock using Redis (Redlock) | P2 | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 177 | Cache invalidation strategies and the "cache stampede" problem | P2 | Hard | ★★★★☆ | Amazon, Netflix, Flipkart |
| 178 | Redis persistence options — RDB vs AOF | P2 | Medium | ★★★☆☆ | Amazon, Microsoft |
| 179 | Redis data structures (sorted sets, hashes) and when each fits | P3 | Medium | ★★★★☆ | Amazon, Flipkart, Swiggy |
| 180 | Redis Pub/Sub vs Streams for event-driven use cases | P3 | Medium | ★★★☆☆ | Amazon, Razorpay |

### 18. Docker
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 181 | Docker image vs container | P2 | Easy | ★★★★★ | Amazon, Microsoft, Infosys |
| 182 | Writing a multi-stage Dockerfile for a Spring Boot application | P2 | Medium | ★★★★★ | Amazon, Adobe, ServiceNow |
| 183 | Docker networking modes and how containers communicate | P2 | Medium | ★★★☆☆ | Microsoft, Cisco |
| 184 | Optimizing Docker image size for a Java application | P2 | Medium | ★★★★☆ | Amazon, Netflix, Flipkart |
| 185 | Docker volumes vs bind mounts | P2 | Easy | ★★★☆☆ | Microsoft, Visa |
| 186 | Debugging a container that keeps restarting | P3 | Medium | ★★★★☆ | Amazon, Uber |

### 19. Kubernetes
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 187 | Pod vs Deployment vs Service in Kubernetes | P3 | Easy | ★★★★★ | Amazon, Netflix, Flipkart |
| 188 | How Kubernetes handles auto-scaling (HPA) for a Spring Boot service | P3 | Medium | ★★★★☆ | Amazon, Uber, Swiggy |
| 189 | Readiness vs liveness probes — why both matter | P3 | Medium | ★★★★★ | Amazon, Netflix, PhonePe |
| 190 | Managing configuration and secrets (ConfigMap, Secret) | P3 | Medium | ★★★★☆ | Amazon, Microsoft, Visa |
| 191 | Rolling update vs blue-green vs canary deployment | P3 | Medium | ★★★★☆ | Amazon, Netflix, Atlassian |
| 192 | Debugging a `CrashLoopBackOff` for a deployed pod | P3 | Hard | ★★★★☆ | Amazon, Uber, Swiggy |
| 193 | Resource requests/limits, and what happens when a pod exceeds them | P3 | Medium | ★★★★☆ | Amazon, Netflix |

### 20. AWS
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 194 | EC2 vs ECS vs EKS vs Lambda for a Java backend | P3 | Medium | ★★★★★ | Amazon, Netflix, Flipkart |
| 195 | Designing a highly available architecture (ALB, ASG, multi-AZ) | P3 | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 196 | RDS vs DynamoDB — when to choose each | P3 | Medium | ★★★★★ | Amazon, JPMorgan, PhonePe |
| 197 | Securing AWS resources accessed by a backend app (IAM, least privilege) | P3 | Medium | ★★★★☆ | Amazon, Visa, Mastercard |
| 198 | S3 storage classes and using S3 for a file upload service | P3 | Easy | ★★★☆☆ | Amazon, Adobe, Zoho |
| 199 | SQS vs SNS — when would you use each? | P3 | Medium | ★★★★☆ | Amazon, Swiggy, Zomato |
| 200 | Designing cost-efficient auto-scaling for bursty traffic on AWS | P3 | Medium | ★★★☆☆ | Amazon, Flipkart |

### 21. Spring Security
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 201 | Spring Security filter chain — how a request gets authenticated | P2 | Hard | ★★★★★ | Amazon, JPMorgan, Visa |
| 202 | Role-based and method-level security in Spring Boot | P2 | Medium | ★★★★★ | Amazon, Microsoft, Adobe |
| 203 | CSRF and CORS — how Spring Security handles each | P2 | Medium | ★★★★☆ | Amazon, Atlassian, ServiceNow |
| 204 | Implementing custom authentication (e.g., API-key based) | P2 | Medium | ★★★☆☆ | Amazon, Visa |
| 205 | Authentication vs authorization, with implementation examples | P2 | Easy | ★★★★☆ | Microsoft, Infosys, Wipro |
| 206 | Rate limiting per authenticated user vs per IP | P3 | Medium | ★★★★☆ | Amazon, Razorpay |

### 22. OAuth & JWT
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 207 | How JWT works, and its security risks (token theft, "none" algorithm) | P2 | Medium | ★★★★★ | Amazon, JPMorgan, Razorpay |
| 208 | OAuth2 Authorization Code flow and where it's used | P2 | Medium | ★★★★★ | Amazon, Microsoft, PhonePe |
| 209 | Handling JWT token refresh and revocation securely | P2 | Hard | ★★★★☆ | Amazon, Visa, Mastercard |
| 210 | OAuth2 vs OpenID Connect | P2 | Medium | ★★★☆☆ | Microsoft, Salesforce |
| 211 | Where should you store JWT tokens client-side, and why? | P2 | Medium | ★★★★☆ | Amazon, Atlassian |
| 212 | Client Credentials grant — when it's used for service-to-service auth | P3 | Medium | ★★★☆☆ | Amazon, JPMorgan |

### 23. System Design
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 213 | Design a URL shortening service — scale, schema, hashing strategy | P3 | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 214 | Design a rate limiter for a public API (token bucket vs sliding window) | P3 | Medium | ★★★★★ | Amazon, Uber, Razorpay |
| 215 | Design a notification system (email, SMS, push) at scale | P3 | Medium | ★★★★☆ | Amazon, Swiggy, PhonePe |
| 216 | Design a distributed unique ID generator (Snowflake-like) | P3 | Hard | ★★★★☆ | Amazon, Uber, LinkedIn |
| 217 | Design a scalable inventory system handling concurrent stock updates | P3 | Hard | ★★★★★ | Amazon, Flipkart, Meesho |
| 218 | Design a chat/messaging backend for millions of concurrent users | P3 | Hard | ★★★★☆ | Amazon, LinkedIn |
| 219 | Design a payment processing system ensuring idempotency and consistency | P3 | Hard | ★★★★★ | Razorpay, PhonePe, Visa, JPMorgan |
| 220 | Design a news feed system (fan-out on write vs read) | P3 | Hard | ★★★☆☆ | LinkedIn, Netflix |
| 221 | Design a ride-hailing driver-rider matching system at scale | P4 | Hard | ★★★★☆ | Uber, Amazon |
| 222 | Design a food delivery ETA/order-tracking system | P4 | Hard | ★★★☆☆ | Swiggy, Zomato |
| 223 | CAP theorem with a real backend scenario where you'd choose AP over CP | P4 | Hard | ★★★★★ | Amazon, Uber, Netflix |
| 224 | Designing a distributed cache invalidation system across regions | P4 | Hard | ★★★★☆ | Amazon, Netflix, Uber |
| 225 | Consistent hashing — why it's used in caching/load balancing | P4 | Hard | ★★★★☆ | Amazon, Uber, LinkedIn |
| 226 | Designing "exactly-once" processing in a distributed pipeline | P4 | Hard | ★★★★☆ | Amazon, Uber, Swiggy |
| 227 | Designing a multi-region active-active architecture for low latency | P4 | Hard | ★★★☆☆ | Amazon, Netflix, Uber |

### 24. LLD
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 228 | Design a Parking Lot system using OOP principles | P3 | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 229 | Design a Library Management System with proper class design | P3 | Medium | ★★★★☆ | Amazon, Infosys, Capgemini |
| 230 | Design an Elevator System handling concurrent requests | P3 | Hard | ★★★★☆ | Amazon, Microsoft, Google |
| 231 | Design a Logging Framework from scratch | P3 | Medium | ★★★☆☆ | Amazon, Oracle |
| 232 | Design a Vending Machine using the State pattern | P3 | Medium | ★★★☆☆ | Amazon, Microsoft |
| 233 | Design a Splitwise-style expense-sharing system | P3 | Hard | ★★★★☆ | Amazon, Flipkart, Swiggy |
| 234 | Design a board-game engine (e.g., Tic-Tac-Toe) with extensible rules | P4 | Medium | ★★★☆☆ | Amazon, Microsoft |
| 235 | Design a cab booking system's core domain model (driver, rider, trip, pricing) | P4 | Hard | ★★★★☆ | Uber, Amazon |

### 25. Design Patterns
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 236 | Singleton pattern — thread-safe implementation in Java | P2 | Easy | ★★★★★ | Amazon, Microsoft, TCS |
| 237 | Factory and Abstract Factory patterns with a real-world example | P2 | Medium | ★★★★☆ | Amazon, Adobe, Infosys |
| 238 | Builder pattern for objects with many optional fields | P2 | Easy | ★★★★☆ | Amazon, Microsoft |
| 239 | Strategy pattern and how Spring uses it internally | P2 | Medium | ★★★★☆ | Amazon, Oracle, Cisco |
| 240 | Observer pattern and where it's used in Java/Spring (events) | P2 | Medium | ★★★☆☆ | Amazon, Adobe |
| 241 | Decorator pattern vs Proxy pattern | P2 | Medium | ★★★☆☆ | Microsoft, Google |
| 242 | Adapter pattern with a real integration example | P3 | Easy | ★★★☆☆ | Amazon, Infosys |
| 243 | Template Method pattern, and where Spring's `JdbcTemplate` uses it | P3 | Medium | ★★★☆☆ | Amazon, Oracle |
| 244 | Chain of Responsibility pattern, and how Filters/Interceptors use it | P3 | Medium | ★★★☆☆ | Amazon, Microsoft |
| 245 | Facade pattern vs a Service layer in layered architecture | P3 | Easy | ★★★☆☆ | Amazon, TCS |
| 246 | When to prefer composition-based patterns (Strategy) over inheritance | P3 | Medium | ★★★★☆ | Amazon, Google |

### 26. CI/CD
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 247 | A typical CI/CD pipeline for a Spring Boot microservice | P3 | Medium | ★★★★★ | Amazon, Atlassian, ServiceNow |
| 248 | Implementing automated rollback in CI/CD on deployment failure | P3 | Medium | ★★★★☆ | Amazon, Netflix, Uber |
| 249 | Jenkins pipelines vs GitHub Actions/GitLab CI for Java builds | P3 | Easy | ★★★☆☆ | Amazon, Atlassian |
| 250 | Managing environment-specific configuration across CI/CD stages securely | P3 | Medium | ★★★☆☆ | Amazon, Visa |
| 251 | Feature flags and how they decouple deployment from release | P3 | Medium | ★★★☆☆ | Amazon, Netflix, Atlassian |

### 27. Monitoring
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 252 | Setting up Prometheus and Grafana to monitor a Spring Boot application | P3 | Medium | ★★★★★ | Amazon, Uber, Swiggy |
| 253 | Key metrics (RED/USE) to monitor for a backend service in production | P3 | Medium | ★★★★☆ | Amazon, Netflix, JPMorgan |
| 254 | Distributed tracing (Zipkin/Jaeger) across microservices | P3 | Medium | ★★★★☆ | Amazon, Uber, LinkedIn |
| 255 | Designing alerting thresholds to avoid alert fatigue | P3 | Medium | ★★★☆☆ | Amazon, Netflix |
| 256 | Correlating logs, metrics, and traces during an incident (observability) | P3 | Medium | ★★★★☆ | Amazon, Netflix, Uber |

### 28. Caching
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 257 | Multi-level caching (local + distributed) and consistency trade-offs | P3 | Medium | ★★★★☆ | Amazon, Netflix, Flipkart |
| 258 | Write-through vs write-behind vs write-around caching | P3 | Medium | ★★★★☆ | Amazon, Uber, Swiggy |
| 259 | Caching at the API Gateway / CDN layer | P3 | Medium | ★★★☆☆ | Amazon, Zomato |
| 260 | Cache coherence across multiple service instances | P3 | Hard | ★★★☆☆ | Amazon, Netflix |
| 261 | Deciding TTL values for different types of cached data | P3 | Medium | ★★★☆☆ | Amazon, Flipkart |

### 29. Performance
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 262 | Profiling and optimizing a slow Java application in production | P3 | Hard | ★★★★★ | Amazon, Goldman Sachs, Netflix |
| 263 | Connection pooling (HikariCP) and tuning pool size | P3 | Medium | ★★★★☆ | Amazon, JPMorgan, Visa |
| 264 | Reducing p99 latency for a high-throughput REST API | P3 | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 265 | Load-testing a backend service before a major traffic event | P3 | Medium | ★★★★☆ | Amazon, Flipkart, Swiggy |
| 266 | Throughput vs latency, and how you optimize for each | P2 | Easy | ★★★★☆ | Amazon, Microsoft |
| 267 | Bottleneck analysis — is it the DB, app, or network? | P3 | Hard | ★★★★☆ | Amazon, JPMorgan |
| 268 | Designing a backend that degrades gracefully under extreme load | P3 | Hard | ★★★★☆ | Amazon, Netflix, Uber |
| 269 | Batching/bulk operations as a performance technique, with trade-offs | P3 | Medium | ★★★☆☆ | Amazon, Flipkart |

### 30. Testing
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 270 | Unit tests vs integration tests, and mocking with Mockito | P2 | Easy | ★★★★★ | Amazon, Microsoft, Flipkart |
| 271 | Integration tests for a Spring Boot REST API (MockMvc/TestRestTemplate) | P2 | Medium | ★★★★☆ | Amazon, Adobe, ServiceNow |
| 272 | Why Testcontainers are preferred over mocking the DB | P2 | Medium | ★★★★☆ | Amazon, Uber, Netflix |
| 273 | Mutation testing — why it matters for critical code paths | P2 | Medium | ★★☆☆☆ | Google, Netflix |
| 274 | Testing asynchronous code (Kafka consumers, `CompletableFuture`) | P2 | Hard | ★★★☆☆ | Amazon, Uber |
| 275 | Contract testing (Pact) and how it prevents breaking changes | P3 | Medium | ★★★☆☆ | Amazon, Atlassian |

### 31. Maven & Gradle
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 276 | Maven's build lifecycle (compile, test, package, install, deploy) | P3 | Easy | ★★★★☆ | Amazon, Infosys, TCS |
| 277 | Resolving dependency version conflicts in Maven ("dependency hell") | P3 | Medium | ★★★★☆ | Amazon, Microsoft |
| 278 | Maven vs Gradle, and why teams migrate | P3 | Easy | ★★★☆☆ | Amazon, Adobe |
| 279 | Creating a custom Maven/Gradle plugin or task for a build step | P4 | Medium | ★★☆☆☆ | Amazon, Oracle |

### 32. Git
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 280 | `git merge` vs `git rebase` — when to use each | P3 | Easy | ★★★★☆ | Amazon, Microsoft, all companies |
| 281 | Resolving a complex merge conflict involving multiple contributors | P3 | Medium | ★★★★☆ | Amazon, Atlassian, Infosys |
| 282 | Git branching strategies — GitFlow vs trunk-based development | P3 | Easy | ★★★☆☆ | Amazon, Microsoft, Cisco |
| 283 | Recovering a commit after an accidental force-push or reset | P3 | Medium | ★★★☆☆ | Amazon, Microsoft |

### 33. Linux
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 284 | Finding the process consuming the most CPU/memory on a production server | P3 | Medium | ★★★★☆ | Amazon, JPMorgan, Goldman Sachs |
| 285 | Hard link vs symbolic link; common debugging commands (`top`, `netstat`, `lsof`) | P3 | Easy | ★★★☆☆ | Amazon, Cisco, Infosys |
| 286 | Diagnosing a "too many open files" error | P4 | Medium | ★★★☆☆ | Amazon, JPMorgan |
| 287 | File permissions (`chmod`/`chown`) for a deployed Java app's log/config files | P3 | Easy | ★★★☆☆ | Amazon, TCS |

### 34. Networking
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 288 | TCP vs UDP, and why REST APIs use TCP | P3 | Easy | ★★★★☆ | Amazon, Cisco, Microsoft |
| 289 | What happens between typing a URL and the browser receiving the response | P3 | Medium | ★★★★☆ | Amazon, Google, Microsoft |
| 290 | Load balancing algorithms — round robin, least connections, consistent hashing | P3 | Medium | ★★★★☆ | Amazon, Uber, Netflix |
| 291 | Layer 4 vs Layer 7 load balancing | P4 | Medium | ★★★☆☆ | Amazon, Netflix |
| 292 | How DNS resolution affects latency for a globally distributed backend | P4 | Medium | ★★★☆☆ | Amazon, Netflix, Uber |

### 35. Behavioral
| # | Question | Priority | Difficulty | Frequency | Companies |
|---|---|---|---|---|---|
| 293 | Tell me about a time you disagreed with a technical decision and how you handled it | P1 | Medium | ★★★★★ | Amazon, Google, Microsoft |
| 294 | Describe a production incident you handled — your role and the outcome | P1 | Medium | ★★★★★ | Amazon, Netflix, Uber, JPMorgan |
| 295 | Tell me about a time you had to learn a new technology quickly | P1 | Easy | ★★★★☆ | Microsoft, Adobe, Infosys |
| 296 | Describe pushing back on an unrealistic deadline | P1 | Medium | ★★★★☆ | Amazon, Atlassian, ServiceNow |
| 297 | Tell me about a conflict with a teammate and how you resolved it | P1 | Medium | ★★★★★ | Amazon, Google |
| 298 | Why do you want to leave your current company / why this company? | P1 | Easy | ★★★★★ | all companies |
| 299 | Tell me about a time you made a mistake in production — what did you learn? | P1 | Medium | ★★★★★ | Amazon, Microsoft, Netflix |
| 300 | Describe a time you mentored a junior engineer or reviewed someone else's design | P2 | Easy | ★★★☆☆ | Amazon, Google, Microsoft |

---

## TOP 50 ABSOLUTE MUST-KNOW QUESTIONS

Master these and you should comfortably clear most Java Backend interviews.

| # | Question | Difficulty | Frequency | Companies |
|---|---|---|---|---|
| 1 | `==` vs `.equals()`, and the `hashCode()`/`equals()` contract | Easy | ★★★★★ | Amazon, Microsoft, Google |
| 2 | String immutability and the String pool | Easy | ★★★★★ | Amazon, Flipkart, TCS |
| 3 | Abstract class vs interface — when to use which | Easy | ★★★★★ | Microsoft, Cisco, Visa |
| 4 | Checked vs unchecked exceptions; custom exceptions | Easy | ★★★★★ | Amazon, JPMorgan |
| 5 | Internal working of `HashMap` (hashing, treeification) | Hard | ★★★★★ | Amazon, Google, Flipkart |
| 6 | `HashMap` vs `LinkedHashMap` vs `TreeMap` | Medium | ★★★★★ | Amazon, Adobe |
| 7 | `ArrayList` vs `LinkedList` | Easy | ★★★★★ | Microsoft, Infosys |
| 8 | Java Memory Model and happens-before | Hard | ★★★★★ | Amazon, Google, Goldman Sachs |
| 9 | `synchronized` vs `ReentrantLock` vs `volatile` | Medium | ★★★★★ | Amazon, JPMorgan |
| 10 | Deadlock detection and prevention | Medium | ★★★★★ | Microsoft, Atlassian |
| 11 | Executor framework and thread pool types | Medium | ★★★★★ | Amazon, Uber, LinkedIn |
| 12 | JVM memory areas (heap, stack, metaspace) | Medium | ★★★★★ | Amazon, Microsoft |
| 13 | Garbage Collection fundamentals | Medium | ★★★★★ | Amazon, Google |
| 14 | Diagnosing `OutOfMemoryError` / memory leaks in production | Hard | ★★★★★ | Amazon, JPMorgan |
| 15 | Streams API: `map`/`filter`/`reduce`/`collect` | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 16 | Dependency Injection and Inversion of Control | Easy | ★★★★★ | Amazon, Microsoft |
| 17 | `@Component` vs `@Service` vs `@Repository` vs `@Controller` | Easy | ★★★★★ | Infosys, Capgemini |
| 18 | Spring Bean lifecycle and scopes | Medium | ★★★★★ | Amazon, Adobe |
| 19 | Spring Boot auto-configuration internals | Medium | ★★★★★ | Amazon, Microsoft |
| 20 | Global exception handling (`@ControllerAdvice`) | Medium | ★★★★★ | Amazon, Visa, Razorpay |
| 21 | Externalizing config across environments (profiles) | Easy | ★★★★★ | Amazon, JPMorgan |
| 22 | REST constraints and statelessness | Easy | ★★★★★ | Amazon, Microsoft |
| 23 | Idempotency in REST APIs | Medium | ★★★★★ | Amazon, Razorpay |
| 24 | HTTP status code usage (200/201/204/400/422/500) | Easy | ★★★★★ | Amazon, Infosys |
| 25 | SQL joins (INNER/LEFT/RIGHT/FULL) | Easy | ★★★★★ | Amazon, Microsoft, JPMorgan |
| 26 | Clustered vs non-clustered indexes | Medium | ★★★★★ | Amazon, Goldman Sachs |
| 27 | ACID properties | Medium | ★★★★★ | Amazon, Microsoft, Oracle |
| 28 | Nth-highest-record SQL query | Medium | ★★★★★ | Amazon, Flipkart |
| 29 | Diagnosing slow SQL queries with EXPLAIN | Hard | ★★★★★ | Amazon, Goldman Sachs |
| 30 | `save()` vs `persist()` vs `merge()` in Hibernate | Medium | ★★★★★ | Amazon, Infosys |
| 31 | N+1 select problem and how to fix it | Hard | ★★★★★ | Amazon, Microsoft, Flipkart |
| 32 | `FetchType.LAZY` vs `EAGER`, and `LazyInitializationException` | Medium | ★★★★★ | Amazon, JPMorgan |
| 33 | Tell me about a production incident you handled | Medium | ★★★★★ | Amazon, Netflix, JPMorgan |
| 34 | Tell me about a technical disagreement and how you handled it | Medium | ★★★★★ | Amazon, Google |
| 35 | Conflict with a teammate and how you resolved it | Medium | ★★★★★ | Amazon, Google |
| 36 | Why this company / why leave your current role | Easy | ★★★★★ | All companies |
| 37 | Microservices vs monolith — when NOT to use microservices | Medium | ★★★★★ | Amazon, Netflix, Uber |
| 38 | Synchronous vs asynchronous microservice communication | Medium | ★★★★★ | Amazon, Microsoft |
| 39 | Saga pattern — choreography vs orchestration | Hard | ★★★★★ | Amazon, Uber, Razorpay |
| 40 | Circuit Breaker pattern (Resilience4j/Hystrix) | Medium | ★★★★★ | Amazon, Netflix, PhonePe |
| 41 | Data consistency across microservices with separate databases | Hard | ★★★★★ | Amazon, Uber, Flipkart |
| 42 | Kafka architecture: topics, partitions, consumer groups | Medium | ★★★★★ | Amazon, Uber, LinkedIn |
| 43 | Kafka delivery semantics (at-most-once/at-least-once/exactly-once) | Hard | ★★★★★ | Amazon, Flipkart |
| 44 | Common Redis use cases (caching, sessions, rate limiting) | Easy | ★★★★★ | Amazon, Flipkart, Razorpay |
| 45 | Spring Security filter chain | Hard | ★★★★★ | Amazon, JPMorgan, Visa |
| 46 | How JWT works, and its security risks | Medium | ★★★★★ | Amazon, JPMorgan |
| 47 | OAuth2 Authorization Code flow | Medium | ★★★★★ | Amazon, Microsoft |
| 48 | Singleton pattern — thread-safe implementation | Easy | ★★★★★ | Amazon, Microsoft |
| 49 | Design a URL shortening service | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 50 | Design a payment processing system ensuring idempotency | Hard | ★★★★★ | Razorpay, PhonePe, Visa, JPMorgan |

---

## TOP 25 RESUME-BASED QUESTIONS

Assumed profile: 1+ year Java, Spring Boot, REST APIs, SQL, Docker, Kubernetes, Kafka, Redis, AWS basics, microservices, CI/CD, Prometheus, Grafana.

| # | Question | Difficulty | Frequency | Companies |
|---|---|---|---|---|
| 1 | Walk me through the architecture of your most complex Spring Boot project | Hard | ★★★★★ | All companies |
| 2 | Why did you choose Kafka over plain REST calls or a simple queue? | Medium | ★★★★★ | Amazon, Uber, Razorpay |
| 3 | Tell me about a production incident you faced — root cause and fix | Hard | ★★★★★ | Amazon, JPMorgan, Netflix |
| 4 | How did you implement authentication/authorization in your project? | Medium | ★★★★★ | Amazon, Visa |
| 5 | Why did you use Redis, and what would break if it went down? | Medium | ★★★★★ | Amazon, Flipkart, Razorpay |
| 6 | How did you containerize your application, and what Docker challenges did you face? | Medium | ★★★★☆ | Amazon, Microsoft |
| 7 | Walk me through your CI/CD pipeline — triggers and rollback strategy | Medium | ★★★★★ | Amazon, Atlassian |
| 8 | How did you monitor your services with Prometheus and Grafana, and what alerts did you set? | Medium | ★★★★☆ | Amazon, Uber, Swiggy |
| 9 | How did you design your database schema, and why SQL vs NoSQL? | Medium | ★★★★★ | Amazon, Flipkart |
| 10 | Describe a specific scaling challenge you faced and how you solved it | Hard | ★★★★★ | Amazon, Netflix, Uber |
| 11 | How do your microservices communicate, and why that choice? | Medium | ★★★★☆ | Amazon, Microsoft |
| 12 | What happens to your system if a downstream microservice goes down? | Hard | ★★★★★ | Amazon, Netflix |
| 13 | How did you deploy to Kubernetes, and how did you configure resource requests/limits? | Medium | ★★★★☆ | Amazon, Uber |
| 14 | A production bug your tests didn't catch — how did you improve your testing process? | Hard | ★★★★☆ | Amazon, Microsoft |
| 15 | How did you secure AWS resources/credentials in your project? | Medium | ★★★★☆ | Amazon, Visa |
| 16 | What was your approach to API versioning as the project evolved? | Medium | ★★★☆☆ | Amazon, Adobe |
| 17 | How did you ensure consistency between your DB writes and Kafka events? | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 18 | How did you implement rate limiting/throttling in your API? | Medium | ★★★★☆ | Amazon, Razorpay |
| 19 | What metrics told you your service was healthy, and how did you set thresholds? | Medium | ★★★★☆ | Amazon, Netflix |
| 20 | If you redesigned your project's architecture today, what would you change and why? | Hard | ★★★★★ | Amazon, Microsoft, Google |
| 21 | How did you handle zero-downtime schema migrations on your SQL database? | Medium | ★★★★☆ | Amazon, JPMorgan |
| 22 | Sync REST vs async Kafka — what trade-offs did you weigh in your project? | Hard | ★★★★☆ | Amazon, Uber |
| 23 | How did you test microservices in CI before deployment (unit/integration/contract tests)? | Medium | ★★★★☆ | Amazon, Atlassian |
| 24 | What was the most challenging Kubernetes issue you debugged? | Hard | ★★★☆☆ | Amazon, Uber |
| 25 | How did you estimate or handle expected traffic/load for your project's APIs? | Medium | ★★★★☆ | Amazon, Flipkart, Swiggy |

---

## TOP 25 MACHINE CODING / LIVE CODING BACKEND QUESTIONS

Backend-only (no DSA, no frontend). Expect 45–90 minutes to design classes, write working code, and discuss extensibility/concurrency.

| # | Question | Difficulty | Frequency | Companies |
|---|---|---|---|---|
| 1 | Build a URL Shortener API (encode/decode, custom aliases) | Medium | ★★★★★ | Amazon, Microsoft, Flipkart |
| 2 | Implement a Rate Limiter (token bucket or sliding window) as a reusable component | Medium | ★★★★★ | Amazon, Uber, Razorpay |
| 3 | Build a Parking Lot API (allocate/release spots, pricing) | Medium | ★★★★★ | Amazon, Microsoft |
| 4 | Build an Inventory Management API supporting concurrent stock updates | Hard | ★★★★☆ | Amazon, Flipkart, Meesho |
| 5 | Implement a Payment API ensuring idempotency for duplicate requests | Hard | ★★★★★ | Razorpay, PhonePe, Visa |
| 6 | Build a Notification Service supporting multiple channels via the Strategy pattern | Medium | ★★★★☆ | Amazon, Swiggy |
| 7 | Build an Order Management Service (create, update status, cancel) | Medium | ★★★★★ | Amazon, Flipkart, Swiggy |
| 8 | Build an Authentication Service with JWT login/signup/token refresh | Medium | ★★★★★ | Amazon, JPMorgan, Visa |
| 9 | Build a File Upload Service with chunking and storage abstraction | Medium | ★★★☆☆ | Amazon, Adobe, Zoho |
| 10 | Build an in-memory Cache Layer with TTL and LRU eviction | Medium | ★★★★★ | Amazon, Microsoft, Netflix |
| 11 | Build a Splitwise-style Expense Sharing API (split, settle balances) | Hard | ★★★★☆ | Amazon, Flipkart |
| 12 | Build a Library Management API (issue/return books, fines) | Easy | ★★★☆☆ | Amazon, Infosys |
| 13 | Implement a Distributed ID Generator service (Snowflake-like) | Hard | ★★★☆☆ | Amazon, Uber |
| 14 | Build a Movie Ticket Booking API handling concurrent seat selection | Hard | ★★★★☆ | Amazon |
| 15 | Implement a Vending Machine backend using state-based design | Medium | ★★★☆☆ | Amazon, Microsoft |
| 16 | Build a Logging/Audit Service capturing user actions with searchable storage | Medium | ★★★☆☆ | Amazon, Oracle |
| 17 | Implement an API Gateway-lite handling routing, auth, and rate limiting | Hard | ★★★★☆ | Amazon, Netflix |
| 18 | Build a Job Scheduler API supporting one-time and recurring jobs | Hard | ★★★★☆ | Amazon, LinkedIn |
| 19 | Implement a Wallet Service supporting credit/debit with transaction history | Hard | ★★★★★ | Razorpay, PhonePe |
| 20 | Build a Food Ordering API (menu, cart, order, status tracking) | Medium | ★★★★☆ | Swiggy, Zomato |
| 21 | Implement a Polling/Voting System API with real-time vote counts | Medium | ★★★☆☆ | Amazon, Microsoft |
| 22 | Build a Distributed Lock Service using Redis or DB-based locking | Hard | ★★★★☆ | Amazon, Uber, Razorpay |
| 23 | Implement a Chat Backend supporting message persistence and delivery status | Hard | ★★★★☆ | Amazon, LinkedIn |
| 24 | Build a Coupon/Discount Engine API applying rules to a cart | Medium | ★★★★☆ | Amazon, Flipkart, Meesho |
| 25 | Build an audit-safe Bank Account Transfer API (atomic debit/credit) | Hard | ★★★★★ | JPMorgan, Goldman Sachs, Visa |
