### container only for building jar
FROM maven:3.6.3-jdk-11-slim AS build-env
#install git
RUN apt-get update
RUN apt-get install -y git

#clone repo and build jar
RUN git clone https://github.com/wcmc-its/ReCiter-PubMed-Retrieval-Tool.git app
WORKDIR /app
RUN mvn clean install -Dmaven.test.skip=true && cp target/*.jar app.jar



#### execution container
FROM openjdk:11-jre-slim AS execute-env
RUN mkdir -p /reciter-pubmed
COPY --from=build-env /app/app.jar /reciter-pubmed/app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/reciter-pubmed/app.jar"]
