FROM java:8-jdk-alpine
copy target/spring-petclinic-config-server-2.3.2.jar /tmp
WORKDIR /tmp
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "spring-petclinic-config-server-2.3.2.jar"]
