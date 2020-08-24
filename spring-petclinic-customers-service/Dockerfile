FROM java:8-jdk-alpine
copy target/spring-petclinic-customers-service-2.3.2.jar /tmp
WORKDIR /tmp
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "spring-petclinic-customers-service-2.3.2.jar"]
