#### spring 
--------------------

##### Convert spring boot application to exe executable file / as a windows service

**Step 1**

+ add configuration executebale=true in pom.ml

  ```xml
  <build>
      <finalName>my-application-demo</finalName>
      <plugins>
          <plugin>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-maven-plugin</artifactId>
              <configuration>
                  <executable>true</executable>
              </configuration>
          </plugin>
      </plugins>
  </build>
  ```

+ create spring jar which will be creating with name `my-application-demo.jar`

**Step 2**

+ Download recent `WinSW.NET4.exe` file and `sample-minimal.xml` from winsw releases

+ package structure to create our service

  ```
  before
  + service-package
     |
     |- my-application-demo.jar
     |- WinSW.NET4.exe
     |- sample-minimal.xml
   
  ```

+ update `sample-minimal.xml` as below

  ```xml
  <service>
    <!-- ID of the service. It should be unique across the Windows system-->
    <id>my-application-demo</id>
    <!-- Display name of the service -->
    <name>my-application-demo Service (powered by WinSW)</name>
    <!-- Service description -->
    <description>This service is a service created from a minimal configuration</description>
  
    <!-- Path to the executable, which should be started -->
    <executable>java</executable>
    <arguments>-Xms1028m -Xmx2026m -jar "%BASE%\my-application-demo.jar"</arguments>
  </service>
  ```

+ rename .exe and .xml with same name which is service name we want to run
  ```
  + service-package
    |
    |- my-application-demo.jar
    |- my-application.exe
    |- my-application.xml
    
  ```

+ Now open cmd prompt and  run below command 

  ```
  $ my-application.exe install
  2020-09-06 16:47:40,670 INFO  - Installing the service with id 'my-application-demo'
  
  $ my-application.exe start/stop/reset/uninstall
  ```

------------------------------



- referance url

> - https://www.baeldung.com/spring-boot-app-as-a-service
>
> -  https://repo.jenkins-ci.org/releases/com/sun/winsw/winsw/
> -  https://github.com/winsw/winsw/releases



--------------------------------










