FROM java:8-jdk-alpine
copy target/spring-petclinic-discovery-server-2.3.2.jar /tmp
WORKDIR /tmp
EXPOSE 8761
ENTRYPOINT ["java", "-jar", "spring-petclinic-discovery-server-2.3.2.jar"]
