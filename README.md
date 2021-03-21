### docker hub - repositório oficial de imagens ###
https://hub.docker.com/


### alguns comandos ###
docker run ubuntu # cria ou faz o download do container no caso do exemplo "ubuntu"
docker run -it ubuntu # roda o container em modo debugger
docker start ubuntu # roda o container
docker ps # lista containers ativos
docker ps -a # lista containers ativos/nao ativos
docker container prune # remove todos os containers ativos
docker port dotnet-image # Mostra qual a porta interna e externa do docker  -> 80/tcp -> 0.0.0.0:5001





















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

