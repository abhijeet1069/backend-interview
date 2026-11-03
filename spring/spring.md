# Spring framework

Spring is a Java framework that helps you build applications by managing objects,
their dependencies, application configuration, transactions, security etc.

## IOC

IOC or Inversion of Control is where you handover the lifecycle of object to 
the spring container.

The IoC container is the heart of the Spring Framework.

Its responsibilities include:
1. Creating objects.
2. Managing object lifecycles.
3. Resolving dependencies.
4. Injecting dependencies.
5. Managing bean scopes.
These objects managed by Spring are called Beans.

## Dependency Injection

Dependency Injection is a design pattern in which an object's dependencies are supplied 
externally rather than being created by the object itself. Spring implements this through 
its IoC container.

### Constructor Injection

```java
//without dependency injection
class UserRepository {
    public void save() {
        System.out.println("Saving user");
    }
}

class UserService {
    //UserService just created its dependency UserRepository by itself
    // Now UserService has a side-effect, and its difficult to test
    private UserRepository repository = new UserRepository();
    public void registerUser() {
        repository.save();
    }
}
```

```java
//with dependency injection
class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }

    public void registerUser() {
        repository.save();
    }
}

UserRepository repository = new UserRepository();
// now the dependency is injected, now the dependencies can later be replaced with other
// depencies making the structure more flexible 
UserService service = new UserService(repository);
```

Now spring automates all of this.

```java
/**
 * You don't need to manually instantiate these objects.

Spring:
1. Discovers UserRepository.
2. Creates its bean.
3. Discovers UserService.
4. Sees that UserService requires UserRepository.
5. Injects the repository through the constructor.

This is called Constructor Injection.
 * 
*/
@Repository
class UserRepository {

    public void save() {
        System.out.println("Saving user");
    }
}

@Service
class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }

    public void registerUser() {
        repository.save();
    }
}

```

### Field Injection

Field Injection is a type of Dependency Injection where Spring injects a dependency directly into a 
class field.

```java
@Service
public class UserService {

    //Spring sees @Autowired and injects the appropriate UserRepository bean into this field.
    @Autowired
    private UserRepository repository;

    public void registerUser() {
        repository.save();
    }
}
```

## BeanFactory

BeanFactory is the fundamental container interface in Spring.

Its primary responsibilities are:

* Creating beans.
* Managing bean lifecycles.
* Resolving dependencies.
* Providing beans when requested.

```java
BeanFactory factory = new XmlBeanFactory(
    new ClassPathResource("beans.xml")
);

OrderService service = factory.getBean(OrderService.class);
```

## ApplicationContext

ApplicationContext extends BeanFactory.

In other words, it provides everything BeanFactory provides, along with additional enterprise application features.

Some important features include:

* Internationalization (i18n).
* Event publishing and event handling.
* Integration with Spring AOP.
* Automatic detection and registration of BeanPostProcessors.
* Resource loading.

```java
@SpringBootApplication
public class MyApplication {

    public static void main(String[] args) {

        ApplicationContext context =
                SpringApplication.run(MyApplication.class, args);

        OrderService service =
                context.getBean(OrderService.class);
    }
}
```

## Spring Lifecycle

```java
       Spring Container Starts
                 |
                 v
       Instantiate Bean
                 |
                 v
       Populate Dependencies
                 |
                 v
       BeanNameAware
       BeanFactoryAware
       ApplicationContextAware
                 |
                 v
       BeanPostProcessor
       (Before Initialization)
                 |
                 v
       @PostConstruct
                 |
                 v
       InitializingBean.afterPropertiesSet()
                 |
                 v
       Custom init-method
                 |
                 v
       BeanPostProcessor
       (After Initialization)
                 |
                 v
          Bean Ready
                 |
                 v
       Application Running
                 |
                 v
       Container Shutdown
                 |
                 v
       @PreDestroy
                 |
                 v
       DisposableBean.destroy()
                 |
                 v
       Custom destroy-method
```