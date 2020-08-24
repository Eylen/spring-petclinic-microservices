FROM maven:3.6.3-jdk-8
COPY target/spring-petclinic-api-gateway.jar /tmp/app
WORKDIR /tmp/app
RUN java -jar spring-petclinic-api-gateway-2.3.2.jar
EXPOSE 8080
