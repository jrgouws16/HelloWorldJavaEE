# HelloWorldJavaEE
- Basic knowledge gained from upskilling in Java EE from Oracle tutorial and Udemy course
- Oracle tutorial [link](https://javaee.github.io/tutorial/toc.html)
- Udemy course [link](https://www.udemy.com/course/java-enterprise-edition-8)

# Getting started
## Download Maven for building project
- Download [maven](http://maven.apache.org/download.cgi)
- Download executable and unzip.
- Add to Path in ~/.baschrc
```shell script
- Add paths to maven
export PATH="$PATH:/media/fastcomm/HDD/apache-maven-3.8.1/bin"
```
- Check to see if successful
```shell script
mvn --version
```

## Install Java JDK
```shell script
sudo apt install -y openjdk-8-jdk openjdk-8-source
```

## Install Netbeans
- Install from snap store on Linux

## Install Payara server as Java EE server
- Install Payara micro server from [website](https://www.payara.fish/)
- Add path to payara server in ~/.baschrc
```shell script
export PATH="$PATH:/media/fastcomm/HDD/Payara_Server/glassfish/bin"
```

## Add Payara server to netbeans
- In services, right click on servers and add Payara server. Provide path to installation.

# Deploying the application
## Method 1
### Step 1 - Build with Maven
```shell script
mvn package
```
-  Creates a .war file in target directory

### Step 2 - Start Payara server
- On netbeans, under services -> servers, right click Payara server and start
- Make sure Payara server is running (http://localhost:8080/)


### Step 3 - Deploy with Payara server
```shell script
asadmin deploy target/hello-javaee8.war
```
- View avaialble endpoints (http://localhost:4848/) under Applications -> hello-javaee8 -> View endpoints
- You can now make requests to the endpoints or navigate to them on http://localhost:8080/
- 
## Method 2 - Building and running a jar executable
### Step 1 - Create the jar
```shell script
java -jar /media/fastcomm/HDD/pm.jar --deploy target/hello-javaee8.war --port 8080 --outputUberJar helloTodo.jar
```
### Step 2 - Run the jar
```shell script
java -jar helloTodo.jar
```

## Method 3
- Configure a profile pom.xml that will automatically build and run the jar file. Investigation needed

# Java API Topics
## CDI API features
### Interceptors 
- Intercept requests and log for example
### Events 
- Send data between different components
- Trigger and listen events
- Payload with event possible
- Sync or Async
- Define order of events
### Service Provider Interface
- Write CDI extensions for portable extensions consumed in projects

## Persist API
### Persistance unit config
- how to manage and persist a collection of entities
- See config in Other Sources/src/main/resources/META-INF/persistence.xml


# Other topics
## Containers
- Black box that takes all your Java classes that transforms them into something else that you can use elsewhere in the application
- Like a factory that classes and add features and functionality
- Manages your classes and makes your life as a developer easy
- Scans application at boot time and shows out errors and discovers candidates for deploy time
- Also manages the life-cycle of beans

## Bean discovery
- Beans are simply classes in Java containers. Contextual beans are instances of beans created by CDI container and managed by it.
- Mechanism which DI run-time analyses and discovers beans to manage
- With DI you externalize dependencies to the CDI container
- See config in src/mean/webapp/WEB-INF/beans.xml
    - annotated: Only beans eligible to be managed at run-time is beans that uses CDI annotations e.g. @RequestScoped
    - all: Every single bean will be managed by CDI at run-time
    - none: Disable all. You won't really want this

## Bean lifecycle
- Init hook
    - Bean has been created and all injections has been done 
- Predestroy
    - Just before bean is destroyed by garbage collection



