# dotnetcorejenkins

# Create the jenkins-home directory if you want to persist jenkins configuration locally.
# Otherwise you could create a docker volume and mount it from the container
mkdir jenkins-home

# if you need to modify the docker file you have to build it.
docker build -t dotnetjenkins:1.0 .

docker run -p 8080:8080 -p dotnetjenkins:1.0

docker run -p 8080:8080 -v ./jenkins-home:/var/lib/jenkins dotnetjenkins:1.0

# Using docker-compose

docker-compose build

docker-compose up -d