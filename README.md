# dotnetcorejenkins

docker build -t dotnetjenkins:1.0 .

docker run -p 8080:8080 -p 50000:50000  dotnetjenkins:1.0

docker run -p 8080:8080 -p 50000:50000 -v <dadadir>:/var/lib/jenkins dotnetjenkins:1.0

dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=cobertura /p:Exclude="[xunit.*]*"
reportgenerator.exe "-reports:coverage.cobertura.xml" "-targetdir:coverage"
