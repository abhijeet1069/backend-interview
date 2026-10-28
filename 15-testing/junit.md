# Unit testing

Unit testing is a type of software testing where the smallest isolated testable
parts of an application - typically functions or classes are tested independently
to verify they work exactly as expected.

## Junit 5 dependecies

```xml
<dependencies>
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-api</artifactId>
      <version>5.6.0</version>
      <scope>test</scope>
    </dependency>

    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-engine</artifactId>
      <version>5.6.0</version>
      <scope>test</scope>
    </dependency>

    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-params</artifactId>
      <version>5.6.0</version>
      <scope>test</scope>
    </dependency>
</dependencies>
```

## Assertions

```java
    Exception exception =  assertThrows(IllegalArgumentException.class,
                ()->{
                    throw new IllegalArgumentException("Age cannot be negative");
                });
    assertEquals("Age cannot be negative",exception.getMessage());
    
    assertDoesNotThrow(()->{
            int result = 10/2;
        });
```

## Parameterized test

### CSV source

```java

    @ParameterizedTest
    @CsvSource({
            "hello world, 11",
            "JUnit 5, 7"
    })
    void calculateStringLength(String str, int expectedLength){
        assertEquals(expectedLength,str.length());
    }
```

### Method source

```java

    @ParameterizedTest
    @MethodSource("stringListData")
    void should_return_list_of_strings_length(List<String> input, List<Integer> expected) {
        assertEquals(expected, getLength(input));
    }

    static Stream<Arguments> stringListData(){
        return Stream.of(
                Arguments.of(
                        List.of("Fe","Fi","Fo","Fum"),
                        List.of(2,2,2,3)
                ),
                Arguments.of(
                        List.of("I","will","find","him","I","will","beat","him"),
                        List.of(1,4,4,3,1,4,4,3)
                )
        );
    }
```

### Value source

```java
    @ParameterizedTest
    @ValueSource(strings = {"apple","banana","orange"})
    void testIsNotBlank(String str){
        assertFalse(str.isEmpty());
    }
```

### CSV file source

```java
 /**
     * src/test/resources/test-data.csv and skips the header line
     * 
     * InputA,Expected
     * 2,4
     * 3,9
     * 4,16
     * */
    @ParameterizedTest
    @CsvFileSource(resources = "/test-data.csv", numLinesToSkip = 1)
    void testSquareFromFile(int a, int expectedSum) {
        assertEquals(expectedSum, a * a);
    }
```