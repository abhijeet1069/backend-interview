# Core Java

## Variables

A variable is a named storage location that holds a value.

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

## Data types

In Java, data types specify the different sizes and types of values that can be stored in variables. 
Java is a statically-typed language, meaning every variable must be declared with its data type before 
it can be used.

### Primitive types

Store simple values directly.

* byte - 8 bits ( byte x = 10;)
* short - 16 bits ( short x = 100;)
* int - 32 bits ( int x = 1000;)
* long - 64 bits ( long x = 100000L;)
* float - 32 bits ( float x = 10.5f;)
* double - 64 bits ( double x = 10.5; )
* char - 16 bits ( char x = 'A'; )
* boolean - JVM dependent representation ( boolean x = true; )

```java
int a = 10;
// here a,b are independent variables
int b = a; // In primitive types, value of a is copied

b = 20;

System.out.println(a); // 10
System.out.println(b); // 20
```

### Reference types

Hold references to objects.

* String
* Arrays
* Classes
* Interfaces
* Enums

```java
class Employee {
    String name;
}

Employee e1 = new Employee();
e1.name = "Alice";

// both variables hold references to the same object.
Employee e2 = e1;

e2.name = "Bob";

System.out.println(e1.name); // Bob
System.out.println(e2.name); // Bob
```

> Java passes reference by value, not the object by reference.

```java
/**
 * com.example.app.Employee@4aa298b7
com.example.app.Employee@7d4991ad
Alice com.example.app.Employee@4aa298b7
*/

public class App {

    static void change(Employee e) {
        System.out.println(e);
        e = new Employee();
        System.out.println(e);
        e.name = "Bob";
    }

    public static void main(String[] args) {
        Employee emp = new Employee();
        emp.name = "Alice";
        change(emp);
        System.out.println(emp.name + " " + emp);
    }
}

class Employee {
    String name;
}

```

## Class

A class defines the state and behavior that its objects will have.

* State : represented by fields
* Behavior : represented by methods

## Objects

An object is a runtime instance of a class.

A constructor initializes an object when it is created.

```java
/**
 * 
- The object is allocated on the heap.
- The local reference variable car1 lives in the method's stack frame.
- The reference stored in car1 points to the object.
 * 
*/
Car car1 = new Car("Toyota", 50);

```