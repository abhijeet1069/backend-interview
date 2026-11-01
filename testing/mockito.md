# Mockito

Mockito is an open source mocking framework for Java. It is used in unit testing to create
fake("mock") objects that simulate the behavior of real dependecies - like databases,
web services, or external APIs - so you can test your code in complete isolation.

Mockito centers around three key concepts

## Mocking (creating a fake object)

A mock is a fake object created by Mockito. Its methods don't execute the original implementation.

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

```java
@Test
void mock() {
    //creates a mock object
    List<String> mockedList = Mockito.mock(List.class);

    // calls are recorded but no storage happens
    mockedList.add("Java");
    mockedList.add("Spring");

    System.out.println(mockedList.size()); // 0

    //mockito records interactions
    verify(mockedList).add("Java"); // verify(mockedList).add("Java1"); //fails
    verify(mockedList, never()).clear();
}
```

## Spying

A Mockito spy is a partial mock that wraps around a real, existing Java object. 
By default, it delegates all method calls to the real object unless you explicitly 
stub them to return a custom value. 

```java
@Test
void spy(){
    List<String> list = new ArrayList<>();

    List<String> spylist = Mockito.spy(list);
    spylist.add("Java");
    spylist.add("Spring");

    //The actual ArrayList implementation is executed.
    //However, you can override individual methods
    System.out.println(spylist.size()); // 2
    System.out.println(list.size()); // 0

    doReturn(100).when(spylist).size();
    System.out.println(spylist.size()); // 100
}
```

## Test isolation

Test isolation means ensuring that one test does not depend on or interfere with 
another test. It also means keeping the code being tested independent of unnecessary 
external dependencies.

## Mockito Dependencies

``xml
<dependencies>
    <dependency>
      <groupId>org.mockito</groupId>
      <artifactId>mockito-core</artifactId>
      <version>5.24.0</version>
    </dependency>
</dependencies>

<!-- remove mockito warning-->
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-dependency-plugin</artifactId>
        <executions>
          <execution>
            <goals>
              <goal>properties</goal>
            </goals>
          </execution>
        </executions>
      </plugin>

      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <configuration>
          <argLine>-javaagent:${org.mockito:mockito-core:jar} -Xshare:off</argLine>
        </configuration>
      </plugin>
    </plugins>
  </build>
```