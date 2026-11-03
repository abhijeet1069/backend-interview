# Spring JPA

## Entity

In JPA(Java Persistence API), an entity is a Java class that represents a table in a
database.

```java
@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private double salary;

    public Employee() {
    }

    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }

    //getters and toString
}
```

## Entity Lifecycle

JPA entity lifecyle consists of four stages

```text
                  new Employee()
                         |
                         v
                    TRANSIENT
                         |
                         | persist()
                         v
                     MANAGED
                    /       \
                   /         \
            detach()         remove()
               |                 |
               v                 v
            DETACHED           REMOVED
               |
               | merge()
               v
       A NEW MANAGED INSTANCE
```

- Transient : A Java object that JPA isn't managing
- Managed (Persistent) : An object managed by the JPA persistence context
- Detached : An object that was managed but is no longer managed
- Removed : An entity marked for deletion from the database


## Hibernate

Dirty checking means Hibernate detects changes to a managed entity and automatically generates the 
necessary SQL to synchronize those changes with the database.