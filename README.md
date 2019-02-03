# dotnetcorejenkins

docker build -t dotnetjenkins:1.0 .

docker run -p 8080:8080 -p dotnetjenkins:1.0

docker run -p 8080:8080 -v ./jenkins-home:/var/lib/jenkins dotnetjenkins:1.0

---- Compose

docker-compose build

docker-compose up -d