# Etap 1: pobranie kodu zrodlowego java z github
FROM alpine/git as downloadSourceCode
WORKDIR /app
RUN git clone https://github.com/adalbertii/dhl-alpine-tomcat-java-mysql.git

# etap 2: zbudowanie projektu wykorzystujac maven framewwrk 
FROM maven:3.5-jdk-8-alpine as packageSourceCode
WORKDIR /app
COPY --from=downloadSourceCode /app/docker-with-java-and-mysql/java /app
RUN mvn package

# Etap 3: zainicjowanie kontenera Tomcat-owego i wggranieWAR- z usługą REST-ową
FROM tomcat:9.0-alpine
WORKDIR /app
COPY --from=packageSourceCode /app/target/RESTfulExample.war /usr/local/tomcat/webapps
# ustawienie portu n aktrym kontenere Tomcata nasłuchi=uje zewnetrzne wywowałnia 
EXPOSE 8080
# uruchomienie serwera Tomaca z aplikacja
CMD ["catalina.sh", "run"]
