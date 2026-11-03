# Integration test

## Spring Boot test

```java
@SpringBootTest
class OrderServiceTest {

    @Autowired
    private OrderService orderService;

    @Test
    void shouldReturnOrder() {
        Order order = orderService.getOrder(1L);

        assertNotNull(order);
        assertEquals("Macbook",order.product());
        assertEquals(1500000.0,order.price());
    }
}
```

## Test containers

Testcontainers is a Java library that allows you to run real dependencies (databases, message brokers, etc.) inside Docker containers during tests.

It's particularly useful for Spring Boot integration testing.

## Database Integration test