A `Dockerfile` is simply a text-based script of instructions used to create a container images.
A docker file contains build stages that run sequentially, some of these stages are cached to save startup time.
A docker file only describes the image to be created, a `docker build` and a `docker run` commands will have to be executed to create and run the container. 
Use [[Docker Compose]] as an alternative to running these shell commands.

**Example:**

```Dockerfile
FROM node:18-alpine 
WORKDIR /app 
COPY . . 
RUN yarn install --production CMD ["node", "src/index.js"]
```

* `FROM` describes the image from which the container will be created, in the above example the `node:18-alpine` image will be downloaded, a new container will be created and the following steps will be made to it.
* `WORKDIR` set the working directory inside the container
* `COPY` copies files from the host to the container
* `RUN` execute build commands when the container is starting up

Other useful commands

* `EXPOSE` describe which ports your application is listening on.
* `CMD` sets a default command to run when the container starts
* `ENV` set environment variables

Information on more commands can be found at https://docs.docker.com/reference/dockerfile/

Then you can build your image 

```sh
docker build -t my-app .
```

And spin up a container

```sh
docker run -d \ 
	--name application-name \ 
	-p 8443:8443 \ 
	my-app
```