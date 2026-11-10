# Lambda expression

When you hit a lambda you don't understand, as two questions
- Which interface does the recieving method expect?
- What are its inputs and output?

The lambda just fills in that one method.

When the lambda only calls one existing method, you can shorten it with ::

```java
//Runnable takes nothing, returns nothing 
Runnable r = () -> System.out.println("hello");
r.run();                                   // prints hello

//Supplier<T> takes nothing, returns a value
Supplier<String> greeting = () -> "hi";
System.out.println(greeting.get());         // hi

//Functions<T,R> takes a value, returns true/false
Function<String, Integer> length = s -> s.length();
System.out.println(length.apply("spring")); // 6

//Predicate<T> takes a value, returns true/false
Predicate<String> isLong = s -> s.length() > 5;
System.out.println(isLong.test("spring"));  // true

//Consumer<T> takes 1 value, returns nothing
Consumer<String> printUpperCase = str->System.out.println(str.toUpperCase());
printUpperCase.accept("hello java");

//Compator<T> takes 2 values and returns an int
employees.sort(
    Comparator.comparingInt(Employee::getSalary)
              .thenComparing(Employee::getName)
);

```