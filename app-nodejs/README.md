### start test  ###
npm run test
npm run test-comportamento

### start app ###
npm start

### build ###
npm install


# porta externa: 3000 
# porta interna da app : 3000

docker build -t didox/nodejs-image -f Dockerfile .
docker run -d -p 3000:3000 --name nodejs-image didox/nodejs-image
docker ps

docker start nodejs-image

docker rm nodejs-image
docker start nodejs-image
docker stop nodejs-image


#### publicar imagem docker em meu HUB ####
docker login
docker tag didox/nodejs-image hub.docker.com/r/didox/nodejs-image
docker push didox/nodejs-image



#### Caso querira rodar docker em modo debugger ####
docker run -it --rm -p 3000:3000 --name nodejs-image nodejs-image











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

