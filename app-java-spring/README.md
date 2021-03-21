### start test com client mavin ###
mvn test
### start app com client mavin ###
mvn spring-boot:run

### start test ###
./mvnw test

### start app ###
./mvnw spring-boot:run -p 8081


### mvn clean ###
mvn clean install


### Docker ###
https://spring.io/guides/gs/spring-boot-docker/

### Build Javaapp ####
./mvnw package && java -jar target/validador-cpf-docker-0.1.0.jar

# porta externa: 8081 
# porta interna da app : 8081

docker build -t didox/app-cpf-spring -f Dockerfile .
docker run -d -p 8081:8081 --name app-cpf-spring didox/app-cpf-spring
docker ps
docker start app-cpf-spring

docker rm app-cpf-spring
docker start app-cpf-spring
docker stop app-cpf-spring


#### Caso querira rodar docker em modo debugger ####
docker run -it --rm -p 8081:8081 --name app-cpf-spring didox/app-cpf-spring


#### publicar imagem docker em meu HUB ####
docker login
docker tag didox/app-cpf-spring hub.docker.com/r/didox/app-cpf-spring
docker push didox/app-cpf-spring
