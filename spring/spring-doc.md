#### Spring Doc

-----------------------------

[TOC]

#### Configure multiple application.properties

- problem statement:

Configure multple application properties in spring project

- Description:

Suppose we have default application.properties and we want to create another config-one-application.properties, config-two-application.properties and both the properties file in our spring project.

```java

@SpringBootApplication
@Slf4j
public class DemoApplication {

    public static void main(String[] args) {

        ConfigurableApplicationContext applicationContext = new SpringApplicationBuilder(DemoApplication.class)
                .properties("spring.config.name:application,confi1-application,confi2-application",
                        "spring.config.location:classpath:/")
                .build().run(args);
		
		// we can confirm the properties are loaded or not by accessing their props
        ConfigurableEnvironment environment = applicationContext.getEnvironment();

        log.info(environment.getProperty("application.loading.messages"));
        log.info(environment.getProperty("config1.loading.messages"));
        log.info(environment.getProperty("config2.loading.messages"));

    }

}
```

-------------------
#### application properties syntax

+ reference in application properties
  + syntax of reference `${<prop-name>}`

```properties
key1="sample1","sample11"
key2="sample2","sample22","sample222"

# refering above key1 and key2 for key.all properties
key.all=${key1},${key2}
```

- Accessing application properties in class

```properties
application.name=demoApplication

city.name=city1 ,city2 ,city3
```

```java
@Value("${application.name}")
private String applicationName;

// converting city.name values into list 
@Value("#{'${city.name}'.trim().replaceAll(' ','').toLowerCase().split(',')}")
private List<String> cities;
```



----------------------

