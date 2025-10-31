FROM maven:4.0.0-rc-4-sapmachine-25 AS BUILD_IMAGE
ADD . /app
WORKDIR /app
RUN mvn package

FROM tomcat:11.0.13-jdk25-temurin-noble AS RUNTIME
COPY --from=BUILD_IMAGE /target/*jar /usr/local/tomcat/webapps/eshwar.jar
EXPOSE 8080
CMD ["java", "-jar", "eshwar.jar"]

