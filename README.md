# HelloWorldJavaEE
Basic knowledge gained from upskilling in Java EE

# Build
mvn clean package && docker build -t academy.learnprogramming/hello-javaee8 .

# RUN
docker rm -f hello-javaee8 || true && docker run -d -p 8080:8080 -p 4848:4848 --name hello-javaee8 academy.learnprogramming/hello-javaee8 
