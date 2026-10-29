# Mockito

Mockito is an open source mocking framework for Java. It is used in unit testing to create
fake("mock") objects that simulate the behavior of real dependecies - like databases,
web services, or external APIs - so you can test your code in complete isolation.

Mockito centers around three key concepts

## Mocking (creating a fake object)

Instead of instantiating real classes (which might require database connections or complex setups), 
you ask Mockito to generate a mock object:

## Stubbing (defining behavior)

You tell the mock how to respond when specific methods

```java
//mocking
PaymentProcessor mockProcessor = mock(PaymentProcessor.class);

// Fake the response: return true when processing $100 - stubbing
when(mockProcessor.processPayment(100.00)).thenReturn(true);

// Fake a failure: throw an exception for invalid cards - stubbing
when(mockProcessor.processPayment(-1.00)).thenThrow(new IllegalArgumentException("Invalid amount"));
```

## Verification (checking interactions)