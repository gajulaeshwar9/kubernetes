FROM maven:3.9.11-eclipse-temurin-25-alpine  AS BUILD_IMAGE
ADD . /app
WORKDIR /app
RUN mvn package

#FROM tomcat:11.0.13-jdk25-temurin-noble AS RUNTIME
FROM eclipse-temurin:25_36-jdk AS runtime   
ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
ENV MAVEN_HOME=/opt/apache.3.9.11
COPY --from=BUILD_IMAGE /app/target/*.jar /target/eshwar.jar
WORKDIR target
EXPOSE 8080
CMD ["java", "-jar", "eshwar.jar"]

