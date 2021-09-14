# Getting Started
Simple project to run spring-boot on a docker image

# Commands
The following commands are supposed to be executed from project's root directory

### build the project fat jar:
To build the solution generating the fat jar into /target/ directory

	$ mvn package (-DskipTests)

### creates the docker image:
Creates an image called olly/springboot-on-docker in local

	$ docker build -t olly/springboot-on-docker .

### run the docker container:
Run the docker image named olly/springboot-on-docker from a local repo

	$ docker run -p 8080:8080 -t olly/springboot-on-docker

### monitor running instalces:
	$ docker ps
	$ docker stats

### docker push
In order to push the instance to be viewable from an external account, it has to be pushed somewhere.  
An option is to push to the [Docker HUB](https://hub.docker.com/). It allows you to create only one private repository/registry and many public repositories/registries. Of course, images in private repositories are visible only by subset of users.  
  
To create a repository, go to DockerHUB console, register yourself (e.g. "ollyit", this will be the organization name) and create a repository (e.g. i've tried with a private one named: "private-repo").  
  
Build your image to create a local copy of the image

	$ docker build -t ollyit/private-repo:springboot-on-docker_0.0.1 .

Register docker with a user/password that can access the registry

	$ docker login

Push the image

	$ docker push ollyit/private-repo:springboot-on-docker_0.0.1

NOTE:
1. build command will create an image tagged as: "ollyit/private-repo:springboot-on-docker_0.0.1"
1. push command looks for an image tagged with "ollyit/private-repo:springboot-on-docker_0.0.1" and pushed the image to "ollyit/private-repo:springboot-on-docker_0.0.1"
  
If you want to use your own registry, you must tag the image with the registry path before pushing it.
For ex. let's assume we've built an image named "aaa:latest". To push this image in a registry server we should do:

	$ docker image tag aaa:latest registry-host:5000/mypath/aaa:latest
	$ docker image push registry-host:5000/mypath/aaa:latest

### docker pull & run
To run an image previously pulled, you just have to do:

	$ docker pull ollyit/private-repo:springboot-on-docker_0.0.1
	$ docker run -p 8080:8080 -t ollyit/private-repo:springboot-on-docker_0.0.1

