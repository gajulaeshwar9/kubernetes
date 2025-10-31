FROM maven:4.0.0-rc-4-sapmachine-25 AS BUILD_IMAGE
ADD . /app
WORKDIR /app
RUN mvn package

#FROM tomcat:11.0.13-jdk25-temurin-noble AS RUNTIME
FROM eclipse-temurin:25_36-jdk AS runtime   
COPY --from=BUILD_IMAGE /app/target/*.jar /target/eshwar.jar
WORKDIR target
EXPOSE 8080
CMD ["java", "-jar", "eshwar.jar"]

