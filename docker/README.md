This section contains information to package a tomcat web application as a docker image.

 DemoApp - source code to build the sample web application. To generate the source files, use *mvn archetype:generate -DgroupId=lk.cloud.meetup.k8s.demo -DartifactId=DemoApp -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false*

 DemoApp.war - sample war file which is accessible on tomcat as http://localhost:8080/DemoApp/

 Dockerfile - sample docker file to build a docker image.

Sample docker images are pushed to Docker Hub in repository 'manjula/lk.cloud.meetup.k8s.tomcat-app:1.0.0'

To build the docker image
```bash
	docker build -t repo-demo-web-app:1.0.0 -f Dockerfile .
```
To build the docker image with application changes.
```bash
	cd DemoApp
	mvn clean install
	cp target/DemoApp.war ../
	docker build -t repo-demo-web-app:2.0.0 -f Dockerfile .
```
To push the docker images to Docker Hub
```bash
	docker login
	docker push repo-demo-web-app
``` 
To run the docker image
```bash
	docker run --rm -p 80:8080 repo-demo-web-app:1.0.0 
```
To access the application
```bash
	curl http://localhost:80/DemoApp/
```
