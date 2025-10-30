FROM maven:4.0.0-rc-4-sapmachine-25 AS BUILD_IMAGE
RUN git clone https://github.com/spring-projects/spring-petclinic.git
RUN cd spring-petclinic && mvn install

FROM tomcat:eclipse-temurin:25-jdk-noble AS RUNTIME
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /spring-petclinic/target/*jar /usr/local/tomcat/webapps/ROOT.jar
EXPOSE 8080
CMD ["catalina.sh", "run"]
