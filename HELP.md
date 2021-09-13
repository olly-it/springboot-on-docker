# Getting Started
Simple project to run spring-boot on a docker image

# Commands
The following commands are supposed to be executed from project's root directory

### build the project fat jar:
to build the solution generating the fat jar into /target/ directory

	mvn package (-DskipTests)

### creates the docker image:
creates an image called olly/springboot-on-docker in local

	docker build -t olly/springboot-on-docker .

### run the docker container:
run the docker image named olly/springboot-on-docker from a local repo

	docker run -p 8080:8080 -t olly/springboot-on-docker
