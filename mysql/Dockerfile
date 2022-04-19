# Etap 1: załadowanie kodu zrodlowego z gitHUB -a 
FROM alpine/git as downloadSourceCode
WORKDIR /app
RUN git clone https://github.com/adalbertii/dhl-alpine-tomcat-java-mysql.git

# Etap 2: utworzenie kontenera  mysql (załadowanie obrazu a DockerHub a i jego zainicjowanie) 
FROM mysql
# ustawienie bazy 
ENV MYSQL_DATABASE company
# dodanie skryptow (katalogu sql-scripts) tworzacych zawartosc schammtu bazy "company" do obrazu 
# skrypty  automatycznie uruchamiane podczas startupu kontenera (All scripts in docker-entrypoint-initdb.d/)
COPY --from=downloadSourceCode /app/docker-with-java-and-mysql/mysql/sql-scripts/ /docker-entrypoint-initdb.d/
