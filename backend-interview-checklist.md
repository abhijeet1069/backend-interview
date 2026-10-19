# Java / Spring Backend Interview Preparation Checklist

A comprehensive interview-preparation map for experienced Java/Spring backend roles.

> **How to use this:** Treat this as a reference/checklist, not a syllabus that must be completed cover-to-cover. 
Prioritize Tier 1, use books/documentation to fill gaps exposed by practice, and progressively work through the 
lower-priority areas.

---

## Priority Overview

### Tier 1 — Absolutely Master ⭐⭐⭐⭐⭐

- DSA / Problem Solving
- Java
- Java Concurrency
- Spring Boot
- REST / HTTP
- JPA / Hibernate
- SQL
- Database Transactions
- System Design
- Microservices
- Security
- Resume / Project Deep Dive
- Behavioral Interviews

### Tier 2 — Strong Working Knowledge ⭐⭐⭐⭐

- JVM
- Database Internals
- Networking
- Testing
- Docker
- Git
- Kafka / Messaging
- Redis / Caching
- Observability

### Tier 3 — Interview-Level Familiarity ⭐⭐⭐

- Operating Systems
- Kubernetes
- Cloud
- Linux
- Maven / Gradle

### Tier 4 — Lower Priority for Immediate Interview Preparation ⭐⭐

- Compiler Design
- Computer Graphics
- Assembly
- Advanced Mathematics
- Deep Kernel Internals
- Advanced Distributed Consensus
- Advanced Algorithms Beyond Typical Interview Requirements

---

# 1. DSA / Problem Solving ⭐⭐⭐⭐⭐

## Foundations

- [ ] Big-O
- [ ] Big-Theta
- [ ] Big-Omega
- [ ] Time complexity
- [ ] Space complexity
- [ ] Recursion
- [ ] Iteration vs recursion
- [ ] Call stack
- [ ] Mathematical reasoning
- [ ] Bit manipulation

## Arrays & Strings

- [ ] Array traversal
- [ ] Prefix sums
- [ ] Difference arrays
- [ ] Kadane's algorithm
- [ ] Two pointers
- [ ] Sliding window
- [ ] Sorting
- [ ] String manipulation
- [ ] Frequency counting
- [ ] Hashing

## Hashing

- [ ] HashMap
- [ ] HashSet
- [ ] Frequency maps
- [ ] Hash collisions
- [ ] Custom hashing
- [ ] `equals()` + `hashCode()`

## Linked Lists

- [ ] Singly linked list
- [ ] Doubly linked list
- [ ] Fast/slow pointers
- [ ] Reversal
- [ ] Cycle detection
- [ ] Merging
- [ ] Intersection

## Stack / Queue

- [ ] Stack
- [ ] Queue
- [ ] Deque
- [ ] Monotonic stack
- [ ] Monotonic queue
- [ ] Expression problems

## Binary Search

- [ ] Standard binary search
- [ ] First/last occurrence
- [ ] Search on answer
- [ ] Rotated arrays
- [ ] Binary search over ranges

## Trees

- [ ] Binary trees
- [ ] BST
- [ ] DFS
- [ ] BFS
- [ ] Preorder
- [ ] Inorder
- [ ] Postorder
- [ ] Level-order
- [ ] Tree height/depth
- [ ] Path problems
- [ ] Lowest common ancestor
- [ ] Balanced trees
- [ ] Serialization/deserialization

## Heap / Priority Queue

- [ ] Min heap
- [ ] Max heap
- [ ] PriorityQueue
- [ ] Top-K
- [ ] K-way merge
- [ ] Median problems

## Backtracking

- [ ] Subsets
- [ ] Permutations
- [ ] Combinations
- [ ] N-Queens
- [ ] Constraint problems
- [ ] Decision trees
- [ ] Pruning

## Graphs

- [ ] Graph representation
- [ ] BFS
- [ ] DFS
- [ ] Connected components
- [ ] Cycle detection
- [ ] Topological sorting
- [ ] DAG
- [ ] Shortest path
- [ ] Dijkstra
- [ ] Bellman-Ford
- [ ] Union-Find / DSU
- [ ] Minimum spanning tree
- [ ] Kruskal
- [ ] Prim
- [ ] Bipartite graphs

## Greedy

- [ ] Interval scheduling
- [ ] Activity selection
- [ ] Sorting + greedy
- [ ] Exchange arguments
- [ ] Heap-based greedy

## Dynamic Programming

- [ ] 1D DP
- [ ] 2D DP
- [ ] Knapsack
- [ ] Subsequence problems
- [ ] Grid DP
- [ ] Partition problems
- [ ] State definition
- [ ] Transition
- [ ] Memoization
- [ ] Tabulation
- [ ] Space optimization

## Advanced / Lower Priority

- [ ] Trie
- [ ] Segment tree
- [ ] Fenwick tree
- [ ] Bitmask DP
- [ ] Advanced graph algorithms

> **DSA strategy:** Don't try to memorize algorithms. Build pattern recognition by solving groups of related problems.

---

# 2. Java ⭐⭐⭐⭐⭐

## Core Java

- [ ] Variables and data types
- [ ] Primitive vs reference types
- [ ] Classes and objects
- [ ] Constructors
- [ ] `this`
- [ ] `static`
- [ ] `final`
- [ ] Access modifiers
- [ ] Encapsulation
- [ ] Inheritance
- [ ] Polymorphism
- [ ] Abstraction
- [ ] Interfaces
- [ ] Abstract classes
- [ ] Composition vs inheritance
- [ ] Method overloading
- [ ] Method overriding
- [ ] `Object` class

## Strings

- [ ] String immutability
- [ ] String pool
- [ ] StringBuilder
- [ ] StringBuffer
- [ ] `==` vs `.equals()`

## Collections

- [ ] List
- [ ] ArrayList
- [ ] LinkedList
- [ ] Set
- [ ] HashSet
- [ ] LinkedHashSet
- [ ] TreeSet
- [ ] Map
- [ ] HashMap
- [ ] LinkedHashMap
- [ ] TreeMap
- [ ] Queue
- [ ] Deque
- [ ] PriorityQueue
- [ ] Internal structure
- [ ] Complexity
- [ ] Ordering
- [ ] Null behavior
- [ ] Thread safety
- [ ] Appropriate use cases

## `equals()` / `hashCode()`

- [ ] Contract
- [ ] HashMap behavior
- [ ] Mutable keys
- [ ] Custom objects as keys

## Generics

- [ ] Generic classes
- [ ] Generic methods
- [ ] Bounded types
- [ ] Wildcards
- [ ] `? extends`
- [ ] `? super`
- [ ] Type erasure

## Exceptions

- [ ] Checked exceptions
- [ ] Unchecked exceptions
- [ ] Error vs Exception
- [ ] `try/catch/finally`
- [ ] Try-with-resources
- [ ] Custom exceptions

## Functional Java

- [x] Lambda expressions
- [ ] Functional interfaces
- [ ] Predicate
- [ ] Function
- [ ] Consumer
- [ ] Supplier
- [ ] Method references
- [ ] Streams
- [ ] Intermediate operations
- [ ] Terminal operations
- [ ] Collectors
- [ ] Parallel streams
- [ ] Optional

---

# 3. Java Concurrency ⭐⭐⭐⭐⭐

- [ ] Process vs thread
- [ ] Thread lifecycle
- [ ] Thread creation
- [ ] Race conditions
- [ ] Critical sections
- [ ] Thread safety
- [ ] `synchronized`
- [ ] Intrinsic locks
- [ ] `volatile`
- [ ] Atomic classes
- [ ] CAS
- [ ] `Lock`
- [ ] `ReentrantLock`
- [ ] ReadWriteLock
- [ ] StampedLock
- [ ] Deadlocks
- [ ] Starvation
- [ ] Livelock
- [ ] Thread pools
- [ ] ExecutorService
- [ ] Callable / Future
- [ ] CompletableFuture
- [ ] ConcurrentHashMap
- [ ] BlockingQueue
- [ ] Producer/consumer
- [ ] ForkJoinPool
- [ ] Java Memory Model
- [ ] Happens-before
- [ ] Visibility
- [ ] Atomicity
- [ ] Immutability

---

# 4. JVM ⭐⭐⭐⭐

- [ ] JVM architecture
- [ ] Class loading
- [ ] ClassLoader
- [ ] Bytecode
- [ ] Stack
- [ ] Heap
- [ ] Metaspace
- [ ] Garbage collection
- [ ] GC roots
- [ ] Minor/major/full GC
- [ ] Generational GC
- [ ] G1 basics
- [ ] JIT
- [ ] Interpreter
- [ ] JIT compilation
- [ ] Escape analysis
- [ ] Memory leaks
- [ ] OutOfMemoryError
- [ ] StackOverflowError

### Execution Pipeline

```text
Java source
    ↓
javac
    ↓
Bytecode
    ↓
JVM
    ↓
Interpreter / JIT
    ↓
Machine code
```

---

# 5. Spring Framework ⭐⭐⭐⭐⭐

## Spring Core

- [ ] IoC
- [ ] Dependency Injection
- [ ] ApplicationContext
- [ ] BeanFactory
- [ ] Beans
- [ ] Bean lifecycle
- [ ] Component scanning
- [ ] `@Component`
- [ ] `@Service`
- [ ] `@Repository`
- [ ] `@Controller`
- [ ] `@Configuration`
- [ ] `@Bean`

## Dependency Injection

- [ ] Constructor injection
- [ ] Setter injection
- [ ] Field injection
- [ ] `@Autowired`
- [ ] `@Qualifier`
- [ ] `@Primary`
- [ ] Why constructor injection is preferred

## Spring Lifecycle

- [ ] Bean creation
- [ ] Dependency injection
- [ ] Initialization
- [ ] `@PostConstruct`
- [ ] Destruction
- [ ] Singleton scope
- [ ] Prototype scope
- [ ] Request scope

## AOP

- [ ] Aspect
- [ ] Join point
- [ ] Pointcut
- [ ] Advice
- [ ] Proxy
- [ ] JDK dynamic proxy
- [ ] CGLIB
- [ ] Cross-cutting concerns

---

# 6. Spring Boot ⭐⭐⭐⭐⭐

## Boot Fundamentals

- [ ] Auto-configuration
- [ ] Starters
- [ ] Spring Boot configuration
- [ ] `application.properties`
- [ ] `application.yml`
- [ ] Profiles
- [ ] Configuration properties
- [ ] Actuator
- [ ] Logging
- [ ] Embedded Tomcat
- [ ] DevTools
- [ ] Environment variables

## REST / HTTP

- [ ] REST principles
- [ ] HTTP methods
- [ ] GET
- [ ] POST
- [ ] PUT
- [ ] PATCH
- [ ] DELETE
- [ ] HTTP status codes
- [ ] Headers
- [ ] Cookies
- [ ] JSON
- [ ] Content negotiation
- [ ] Idempotency
- [ ] Pagination
- [ ] Sorting
- [ ] Filtering

## Spring MVC

- [ ] DispatcherServlet
- [ ] Controllers
- [ ] Request mapping
- [ ] Request parameters
- [ ] Path variables
- [ ] Request body
- [ ] Response body
- [ ] Validation
- [ ] Exception handling
- [ ] `@ControllerAdvice`
- [ ] `@ExceptionHandler`

---

# 7. Spring Data / Hibernate / JPA ⭐⭐⭐⭐⭐

## JPA

- [x] Entity
- [ ] Entity lifecycle
- [ ] Persistence context
- [ ] EntityManager
- [ ] Repository
- [ ] JPQL
- [ ] Native queries
- [ ] Lazy loading
- [ ] Eager loading
- [ ] Dirty checking
- [ ] Cascading
- [ ] Entity relationships

## Relationships

- [ ] One-to-one
- [ ] One-to-many
- [ ] Many-to-one
- [ ] Many-to-many

## Hibernate

- [ ] First-level cache
- [ ] Second-level cache
- [ ] N+1 problem
- [ ] Fetch joins
- [ ] Proxy
- [ ] LazyInitializationException
- [ ] Persistence context
- [ ] Flush
- [ ] Batch operations

## Transactions

- [ ] `@Transactional`
- [ ] Transaction boundaries
- [ ] Propagation
- [ ] Isolation
- [ ] Rollback
- [ ] Read-only transactions
- [ ] Proxy limitations

---

# 8. SQL ⭐⭐⭐⭐⭐

## SQL Fundamentals

- [ ] SELECT
- [ ] INSERT
- [ ] UPDATE
- [ ] DELETE
- [ ] WHERE
- [ ] GROUP BY
- [ ] HAVING
- [ ] ORDER BY
- [ ] DISTINCT
- [ ] LIMIT / OFFSET

## Joins

- [ ] INNER JOIN
- [ ] LEFT JOIN
- [ ] RIGHT JOIN
- [ ] FULL JOIN
- [ ] Self join
- [ ] Cross join

## Advanced SQL

- [ ] Subqueries
- [ ] Correlated subqueries
- [ ] CTE
- [ ] Recursive CTE
- [ ] Window functions
- [ ] `ROW_NUMBER`
- [ ] `RANK`
- [ ] `DENSE_RANK`
- [ ] `LEAD`
- [ ] `LAG`

## Database Concepts

- [ ] Primary key
- [ ] Foreign key
- [ ] Constraints
- [ ] Normalization
- [ ] Denormalization
- [ ] Indexes
- [ ] Composite indexes
- [ ] B-tree
- [ ] Query plans
- [ ] `EXPLAIN`

---

# 9. DBMS ⭐⭐⭐⭐

## Transactions

- [ ] ACID
- [ ] Atomicity
- [ ] Consistency
- [ ] Isolation
- [ ] Durability

## Isolation Levels

- [ ] Read uncommitted
- [ ] Read committed
- [ ] Repeatable read
- [ ] Serializable
- [ ] Dirty reads
- [ ] Non-repeatable reads
- [ ] Phantom reads

## Concurrency

- [ ] Locks
- [ ] Shared locks
- [ ] Exclusive locks
- [ ] Row locks
- [ ] Table locks
- [ ] Deadlocks
- [ ] MVCC

## Storage

- [ ] Pages
- [ ] Records
- [ ] Buffer pool
- [ ] Indexes
- [ ] B-trees
- [ ] Clustered / non-clustered indexes

## Database Scaling

- [ ] Replication
- [ ] Read replicas
- [ ] Sharding
- [ ] Partitioning

---

# 10. System Design ⭐⭐⭐⭐⭐

## Fundamentals

- [ ] Scalability
- [ ] Availability
- [ ] Reliability
- [ ] Performance
- [ ] Latency
- [ ] Throughput
- [ ] Fault tolerance
- [ ] Consistency
- [ ] CAP theorem
- [ ] ACID vs BASE

## Architecture

- [ ] Monolith
- [ ] Modular monolith
- [ ] Microservices
- [ ] Service boundaries
- [ ] API gateway
- [ ] Load balancer
- [ ] Reverse proxy
- [ ] Service discovery

## Distributed Systems

- [ ] Synchronization
- [ ] Distributed locks
- [ ] Leader election
- [ ] Replication
- [ ] Partitioning
- [ ] Consensus basics
- [ ] Eventual consistency
- [ ] Idempotency
- [ ] Retries
- [ ] Timeouts
- [ ] Circuit breakers
- [ ] Backpressure

## Caching

- [ ] Redis
- [ ] Cache-aside
- [ ] Write-through
- [ ] Write-behind
- [ ] TTL
- [ ] Eviction
- [ ] Cache invalidation
- [ ] Cache stampede

## Messaging

- [ ] Kafka
- [ ] RabbitMQ
- [ ] Queues
- [ ] Pub/sub
- [ ] Consumer groups
- [ ] Partitions
- [ ] Ordering
- [ ] At-least-once delivery
- [ ] At-most-once delivery
- [ ] Exactly-once concepts
- [ ] Dead-letter queues

## Common Designs to Practice

- [ ] URL shortener
- [ ] Rate limiter
- [ ] Notification system
- [ ] File storage
- [ ] Chat system
- [ ] Payment system
- [ ] Order system
- [ ] Ticket booking
- [ ] News feed
- [ ] Ride sharing
- [ ] Logging system

---

# 11. Microservices ⭐⭐⭐⭐⭐

- [ ] Microservice principles
- [ ] Service boundaries
- [ ] Database per service
- [ ] API gateway
- [ ] Service discovery
- [ ] Configuration management
- [ ] Inter-service communication
- [ ] REST
- [ ] gRPC basics
- [ ] Synchronous communication
- [ ] Asynchronous communication
- [ ] Distributed transactions
- [ ] Saga pattern
- [ ] Outbox pattern
- [ ] CQRS basics
- [ ] Event-driven architecture
- [ ] Retry
- [ ] Timeout
- [ ] Circuit breaker
- [ ] Bulkhead
- [ ] Idempotency
- [ ] Distributed tracing

---

# 12. Security ⭐⭐⭐⭐⭐

## Web Security

- [ ] Authentication
- [ ] Authorization
- [ ] Sessions
- [ ] Cookies
- [ ] JWT
- [ ] OAuth 2.0
- [ ] OpenID Connect
- [ ] Access tokens
- [ ] Refresh tokens
- [ ] Password hashing
- [ ] BCrypt / Argon2
- [ ] HTTPS / TLS
- [ ] CORS
- [ ] CSRF
- [ ] XSS
- [ ] SQL injection
- [ ] SSRF
- [ ] Rate limiting

## Spring Security

- [ ] SecurityFilterChain
- [ ] Authentication
- [ ] Authorization
- [ ] UserDetails
- [ ] PasswordEncoder
- [ ] JWT authentication
- [ ] Method security
- [ ] Roles
- [ ] Authorities

---

# 13. Networking ⭐⭐⭐⭐

Understand what happens when:

```text
Browser
   ↓
DNS
   ↓
TCP
   ↓
TLS
   ↓
HTTP
   ↓
Load Balancer
   ↓
Spring Boot
```

## Topics

- [ ] OSI model
- [ ] TCP/IP
- [ ] DNS
- [ ] TCP
- [ ] UDP
- [ ] TCP handshake
- [ ] TCP connection termination
- [ ] HTTP/1.1
- [ ] HTTP/2
- [ ] HTTP/3 basics
- [ ] HTTPS
- [ ] TLS
- [ ] IP
- [ ] Ports
- [ ] NAT
- [ ] Proxy
- [ ] Reverse proxy
- [ ] Load balancer
- [ ] WebSocket

---

# 14. Operating Systems ⭐⭐⭐

- [ ] Process
- [ ] Thread
- [ ] Context switching
- [ ] Scheduling
- [ ] Virtual memory
- [ ] Paging
- [ ] Page fault
- [ ] Stack
- [ ] Heap
- [ ] Memory protection
- [ ] System calls
- [ ] File systems
- [ ] Locks
- [ ] Deadlocks
- [ ] IPC
- [ ] Kernel mode
- [ ] User mode

---

# 15. Testing ⭐⭐⭐⭐

## Unit Testing

- [ ] JUnit 5
- [ ] Assertions
- [ ] Parameterized tests
- [ ] Mockito
- [ ] Mock
- [ ] Spy
- [ ] Stub
- [ ] Test isolation

## Integration Testing

- [ ] Spring Boot Test
- [ ] Testcontainers
- [ ] Database integration tests
- [ ] REST integration tests

## API Testing

- [ ] Postman
- [ ] REST Assured

## Testing Concepts

- [ ] Unit vs integration vs E2E
- [ ] Test pyramid
- [ ] Mocking
- [ ] Test fixtures
- [ ] Test data
- [ ] Contract testing

---

# 16. Docker / Containers ⭐⭐⭐⭐

- [ ] Images
- [ ] Containers
- [ ] Dockerfile
- [ ] Layers
- [ ] Volumes
- [ ] Networks
- [ ] Ports
- [ ] Environment variables
- [ ] Multi-stage builds
- [ ] Docker Compose
- [ ] Container lifecycle
- [ ] Image registries

Understand:

```text
Dockerfile
    ↓
Image
    ↓
Container
```

---

# 17. Kubernetes ⭐⭐⭐

- [ ] Pod
- [ ] Deployment
- [ ] Service
- [ ] ConfigMap
- [ ] Secret
- [ ] Namespace
- [ ] Ingress
- [ ] ReplicaSet
- [ ] StatefulSet
- [ ] Health checks
- [ ] Liveness probes
- [ ] Readiness probes
- [ ] Scaling
- [ ] Rolling deployment

---

# 18. Cloud ⭐⭐⭐

Pick one cloud platform and understand the fundamentals.

- [ ] Compute
- [ ] Storage
- [ ] Database
- [ ] Networking
- [ ] IAM
- [ ] Load balancing
- [ ] Autoscaling
- [ ] Containers
- [ ] Serverless
- [ ] Monitoring
- [ ] Secrets / configuration

---

# 19. Git ⭐⭐⭐⭐

- [ ] clone
- [ ] add
- [ ] commit
- [ ] push
- [ ] pull
- [ ] fetch
- [ ] branch
- [ ] merge
- [ ] rebase
- [ ] cherry-pick
- [ ] revert
- [ ] reset
- [ ] stash
- [ ] reflog
- [ ] `git switch`
- [ ] `git restore`
- [ ] Conflict resolution
- [ ] Recovering from mistakes

---

# 20. Build Tools ⭐⭐⭐

## Maven

- [ ] `pom.xml`
- [ ] Dependencies
- [ ] Dependency scopes
- [ ] Lifecycle
- [ ] Plugins
- [ ] Profiles
- [ ] Dependency management
- [ ] Transitive dependencies

## Gradle

- [ ] `build.gradle`
- [ ] Dependencies
- [ ] Tasks
- [ ] Repositories

---

# 21. Linux ⭐⭐⭐

- [ ] Filesystem
- [ ] Permissions
- [ ] Processes
- [ ] Signals
- [ ] Environment variables
- [ ] Pipes
- [ ] Redirection
- [ ] grep
- [ ] sed
- [ ] awk basics
- [ ] curl
- [ ] ssh
- [ ] ps
- [ ] top
- [ ] netstat / ss
- [ ] Logs
- [ ] systemd basics
- [ ] Shell scripting basics

---

# 22. Observability ⭐⭐⭐⭐

- [ ] Logging
- [ ] Metrics
- [ ] Tracing
- [ ] SLF4J
- [ ] Logback
- [ ] Micrometer
- [ ] Prometheus
- [ ] Grafana
- [ ] OpenTelemetry
- [ ] Distributed tracing
- [ ] Correlation IDs
- [ ] Health checks

Be able to answer:

> "Your API suddenly becomes slow in production. How do you investigate?"

---

# 23. Behavioral / HR ⭐⭐⭐⭐⭐

Prepare stories for:

- [ ] Tell me about yourself
- [ ] Difficult technical problem
- [ ] Production incident
- [ ] Conflict with teammate
- [ ] Failure
- [ ] Mistake
- [ ] Leadership
- [ ] Ownership
- [ ] Tight deadline
- [ ] Ambiguous requirement
- [ ] Improving a system
- [ ] Debugging something difficult
- [ ] Why are you leaving?
- [ ] Why this company?
- [ ] Why backend?
- [ ] Why should we hire you?

## STAR Method

```text
Situation
    ↓
Task
    ↓
Action
    ↓
Result
```

Use real experiences wherever possible.

---

# 24. Resume / Project Deep Dive ⭐⭐⭐⭐⭐

Anything on your resume can become an interview question.

For every project or technology, be able to answer:

- [ ] What did you build?
- [ ] Why did you build it?
- [ ] Why this technology?
- [ ] What alternatives did you consider?
- [ ] What problems occurred?
- [ ] How did you debug them?
- [ ] How did you test it?
- [ ] How would you scale it?
- [ ] What would you change?
- [ ] What was the hardest bug?
- [ ] What did you personally implement?

> **Rule:** Never put technology on your resume that you cannot discuss.

---

# 25. Interview-Specific Skills ⭐⭐⭐⭐⭐

## DSA Interview

Practice:

- [ ] Clarifying requirements
- [ ] Thinking aloud
- [ ] Brute-force solution
- [ ] Optimization
- [ ] Complexity analysis
- [ ] Coding without IDE assistance
- [ ] Testing edge cases
- [ ] Explaining trade-offs

## System Design Interview

Use this general flow:

```text
Requirements
    ↓
Scale estimation
    ↓
API
    ↓
Data model
    ↓
High-level architecture
    ↓
Deep dive
    ↓
Bottlenecks
    ↓
Failure handling
```

## Backend Interview

Be able to explain:

```text
HTTP request
    ↓
Load balancer
    ↓
Spring
    ↓
Controller
    ↓
Service
    ↓
Transaction
    ↓
Hibernate
    ↓
Database
```

Know what happens at every layer.

---

# Recommended Preparation Strategy

Do **not** turn this checklist into another giant syllabus.

Use it as a gap-finding system.

```text
                 INTERVIEW
                     │
        ┌────────────┼────────────┐
        ↓            ↓            ↓
       DSA       Backend       System Design
        │            │            │
    Problems       Project      Design
        │            │            │
        ↓            ↓            ↓
    Patterns      Questions    Trade-offs
        │            │            │
        └────────────┼────────────┘
                     ↓
                Mock Interview
                     ↓
               Identify Gaps
                     ↓
             Read That Topic
                     ↓
                  Repeat
```

## The Core Principle

> **Books are references. Problems and projects are the training. Interviews expose gaps; books and documentation fill those gaps.**

If an interviewer asks about MVCC and you don't understand it → study MVCC.

If you fail a backtracking problem → study backtracking and solve more problems.

If you can't explain Spring transactions → study `@Transactional` deeply.

If you can't design a notification system → study queues, Kafka, retries and idempotency.

The goal is not to eliminate every possible knowledge gap before interviewing.

The goal is to become progressively better at:

- [ ] Solving problems
- [ ] Writing correct code
- [ ] Explaining your reasoning
- [ ] Building backend systems
- [ ] Designing systems
- [ ] Debugging production problems
- [ ] Communicating technical decisions
- [ ] Defending your experience

---

# Suggested High-Level Order

## Phase 1 — Interview Core

1. [ ] Java
2. [ ] DSA
3. [ ] SQL
4. [ ] Spring Boot
5. [ ] REST / HTTP
6. [ ] JPA / Hibernate

## Phase 2 — Backend Depth

7. [ ] Java Concurrency
8. [ ] DBMS
9. [ ] Testing
10. [ ] Security
11. [ ] Redis / Caching
12. [ ] Kafka / Messaging
13. [ ] Docker

## Phase 3 — Architecture

14. [ ] System Design
15. [ ] Microservices
16. [ ] Networking
17. [ ] Observability
18. [ ] Cloud
19. [ ] Kubernetes

## Phase 4 — Interview Execution

20. [ ] Resume deep dive
21. [ ] Behavioral questions
22. [ ] DSA mock interviews
23. [ ] Backend mock interviews
24. [ ] System design mock interviews
25. [ ] Company-specific preparation

---

# Final Rule

Do not wait until this entire checklist is complete before applying.

A much better loop is:

```text
Prepare
   ↓
Apply
   ↓
Interview
   ↓
Find weaknesses
   ↓
Study weaknesses
   ↓
Practice
   ↓
Interview again
   ↓
Improve
```

**The interview itself is part of the preparation.**
