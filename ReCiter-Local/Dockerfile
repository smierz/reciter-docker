### container only for building package
FROM maven:3.6.3-jdk-11-slim AS build-env
#install git
RUN apt-get update
RUN apt-get install -y git

#clone repo and build package
RUN git clone https://github.com/smierz/ReCiter.git -b dynamodb_local app
WORKDIR /app
RUN mvn clean install -Dmaven.test.skip=true && cp target/*.jar app.jar



#### execution container
FROM openjdk:11-jre-slim AS execute-env
RUN mkdir -p /reciter
COPY --from=build-env /app/app.jar /reciter/app.jar
COPY ./application.properties /reciter/application.properties
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/reciter/app.jar"]