A `Dockerfile` is simply a text-based script of instructions that is used to create a container image.
A docker file contains build stages that run sequentially, some of these stages are cached to save startup time.

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