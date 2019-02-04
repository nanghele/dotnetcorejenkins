# Using Jenkins to build a dotNet Core project 

## Abstract
This is an example for using Jenkins inside a docker container to let CI take place in a dotNet Core environment. Microsoft is moving fast in the direction of docker and the linux systems and [Docker Hub](https://hub.docker.com/u/microsoft) is full of usefull images for any use. What I did is quite simple I have used microsoft/dotnet sdk in a debian stretch enviroment to run Jenkins and configure it for a basic CI block.

## Getting started
First checkout this project and then create the jenkins-home directory to persist jenkins configuration locally. Otherwise you could create a docker volume and mount it from the container, that's up to you , in this example I mount a local directory
```
mkdir jenkins-home
```
Now it's time to start your container
```
# using docker cli
docker run -p 8080:8080 -v ./jenkins-home:/var/lib/jenkins dotnetjenkins:1.0
# or if you prefer docker-compose
docker-compose up -d
```
