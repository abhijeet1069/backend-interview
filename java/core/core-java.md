# Core Java

## Variables

A variable is a named storage location that holds a value.
Java is statically typed, meaning the type of variable is known at compile time.

### Scope of variables

* Local variable - Declared inside a method or block, lifetime during the execution 
                    of the block.
* Instance variable - Declared inside a class outside methods, lifetime associated
                    with an object
* Static variable - Declared inside a class with static, lifetime associated with
                    the class

```java
class Employee {

    static String company = "Servion"; // Static variable

    String name;                       // Instance variable

    void display() {
        int age = 25;                  // Local variable
    }
}
```