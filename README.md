# Using Jenkins to build a .Net Core project 

## Abstract
This is an example for using Jenkins inside a docker container to let CI take place in a .Net Core environment. Microsoft is moving fast in the direction of docker and  linux systems, [Docker Hub](https://hub.docker.com/u/microsoft) is full of usefull images for any use in the MS world. What I did is quite simple, I have used microsoft/dotnet sdk in a debian stretch enviroment to run Jenkins and configure it for a basic CI block. You can follow this instruction for any linux, windows, Mac-OsX machine which has a working docker and shell.

## Getting started
First checkout this project and then create the jenkins-home directory to persist jenkins configuration locally. Otherwise you could create a docker volume and mount it from the container, that's up to you , in this example I mount a local directory. 
```
mkdir jenkinsCI
git clone https://github.com/nanghele/dotnetcorejenkins.git jenkinsCI
cd jenkinsCI
mkdir jenkins-home
```
Now it's time to start your container
```
# using docker cli
docker run -p 8080:8080 -v ./jenkins-home:/var/lib/jenkins dotnetjenkins:1.0
# or if you prefer docker-compose
docker-compose up -d
```
In a few seconds you can browse Jenkins on http://localhost:8080
and you will have to start configuration
<img src='/docs/img/jenkins1.PNG' width=50% >

Since I would like to get code coverage report I will install the Cobertura plugin and unselect some uneeded plugins.
<img src='/docs/img/jenkins2.PNG' width=50% > 

Let's go on.

<img src='/docs/img/jenkins3.PNG' width=50% >

After few minutes depending on your machine you will be ready to create your first job. I will skip the congifuration of git account and I will directly go into the compile section of the job 
```
# step 1 execute shell
dotnet build
# step 2 execute shell
dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=cobertura /p:Exclude="[xunit.*]"
# post build step 
cobertura xml report pattern =>  cobertura.coverage.xml
```
<img src='/docs/img/jenkins6.PNG' width=100% >

and at the end you will get your coverage report

<img src='/docs/img/jenkins7.PNG' width=50% >
