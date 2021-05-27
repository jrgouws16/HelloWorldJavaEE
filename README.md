# HelloWorldJavaEE
Basic knowledge gained from upskilling in Java EE

# Getting started (Based on [Oracle Tutorial](https://javaee.github.io/tutorial/toc.html))
## Download Maven for building project
- Download [link](http://maven.apache.org/download.cgi)
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


# Build
```shell script
mvn package
```
???? mvn clean package && docker build -t academy.learnprogramming/hello-javaee8 .

# Deploy
```shell script
asadmin deploy target/hello-javaee8.war
```

# View
- Make sure Payara server is running (http://localhost:8080/)
- View avaialble endpoints (http://localhost:4848/) under Applications -> hello-javaee8 -> View endpoints

# Building and running a jar executable
- Create the jar
```shell script
java -jar /media/fastcomm/HDD/pm.jar --deploy target/hello-javaee8.war --port 8080 --outputUberJar helloTodo.jar
```
- Run the jar
```shell script
java -jar helloTodo.jar
```


# RUN
docker rm -f hello-javaee8 || true && docker run -d -p 8080:8080 -p 4848:4848 --name hello-javaee8 academy.learnprogramming/hello-javaee8 