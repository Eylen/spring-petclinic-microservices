FROM java:8-jdk-alpine
copy target/spring-petclinic-visits-service-2.3.2.jar /tmp
WORKDIR /tmp
EXPOSE 8083
ENTRYPOINT ["java", "-jar", "spring-petclinic-visits-service-2.3.2.jar"]
