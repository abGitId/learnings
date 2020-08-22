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

