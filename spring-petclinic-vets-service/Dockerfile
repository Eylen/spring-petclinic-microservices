FROM java:8-jdk-alpine
copy target/spring-petclinic-vets-service-2.3.2.jar /tmp
WORKDIR /tmp
ENTRYPOINT ["java", "-jar", "spring-petclinic-vets-service-2.3.2.jar"]
