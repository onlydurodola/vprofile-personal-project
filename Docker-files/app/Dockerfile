FROM maven:3.9.9-eclipse-temurin-21-jammy AS build
RUN git clone -b containers https://github.com/onlydurodola/vprofile-personal-project.git
RUN cd vprofile-personal-project && mvn install

FROM tomcat:10-jdk21

LABEL "Author"="Durodola"
LABEL "project"="vprofile"

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build vprofile-personal-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
