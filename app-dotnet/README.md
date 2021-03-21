### start test ###
cd ../WebTddBddSharp/TDD
dotnet test
cd ../WebTddBddSharp/BDDValidator
dotnet test
### start app ###
dotnet run

### build ###
dotnet build


# porta externa: 5001 
# porta interna da app : 80

docker build -t didox/dotnet-image -f Dockerfile .
docker run -d -p 5001:80 --name dotnet-image  didox/dotnet-image 
docker ps

docker start dotnet-image 

docker rm dotnet-image 
docker start dotnet-image 
docker stop dotnet-image 



#### publicar imagem docker em meu HUB ####
docker login
docker tag didox/dotnet-image hub.docker.com/r/didox/dotnet-image
docker push didox/dotnet-image



#### Caso querira rodar docker em modo debugger ####
docker run -it --rm -p 5001:80 --name dotnet-image dotnet-image










::::::::: CONSOLE APP :::::::::::

https://docs.microsoft.com/pt-br/dotnet/core/docker/build-container?tabs=windows


dotnet publish -c Release


-- Dockerfile conteúdo --
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]

docker build -t counter-image -f Dockerfile .

docker images

-- para remover imagem -- 
docker rmi counter-image

docker create --name dotnet-console-container counter-image

docker ps -a

docker rm dotnet-console-container

docker start dotnet-console-container

docker attach --sig-proxy=false dotnet-console-container

docker stop dotnet-console-container

docker ps


:::::::::: WEB MVC :::::::::

https://docs.docker.com/engine/examples/dotnetcore/

dotnet new mvc
arquivo Dockerfile
docker build .

docker build -t aspnetapp .
docker run -d -p 8080:80 --name myapp aspnetapp
docker ps

docker start aspnetapp



:::::: Usando docker ::::::

cd dotnet-docker/samples/aspnetapp

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp

