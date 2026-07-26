Docker allows us to deploy applications using multiple containers, entire architectures can be set up using containers and connected by networks.

A classic setup is an application container paired with a database container for persistence.
A more complex case would be a microservice architecture that would also need multiple networks, message queues and cache containers.

> [!http://localhost/tutorial/using-docker-compose/]
> [Docker Compose](https://docs.docker.com/compose/) is a tool that was developed to help define and share multi-container applications. With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.

Docker compose files are structured YML files that can be executes and the compose executable will run an deploy your containers.

A compose file can equal in functionality to running multiple `docker` commands, it allows for orchestration of spawning and tearing down containers.

### Example

Lets setup a simple application and database containers and connect them via a network.

Instead of using verbose command lines to start your containers like so

```sh
docker run -dp 3000:3000 \ 
	-w /app -v "$(pwd):/app" \ 
	--network todo-app \ 
	-e MYSQL_HOST=mysql \ 
	-e MYSQL_USER=root \ 
	-e MYSQL_PASSWORD=secret \ 
	-e MYSQL_DB=todos \ 
	node:18-alpine \ 
	sh -c "yarn install && yarn run dev"
```

An equivalent compose YAML file will look like so `docker-compose.yml`

```yaml
services: 
	app: 
		image: node:18-alpine 
		command: sh -c "yarn install && yarn run dev" 
		ports: - 3000:3000 
		working_dir: /app 
		volumes: 
			- ./:/ app 
		environment: 
			MYSQL_HOST: mysql 
			MYSQL_USER: root 
			MYSQL_PASSWORD: secret 
			MYSQL_DB: todos
```

The compose file can define multiple services, that map to multiple `docker run` commands. So instead of also executing

```sh
docker run -d \ 
	--network todo-app 
	--network-alias mysql \ 
	-v todo-mysql-data:/var/lib/mysql \ 
	-e MYSQL_ROOT_PASSWORD=secret \ 
	-e MYSQL_DATABASE=todos \ mysql:8.0
```

We can add this segment to the `services:` segment above

```yaml
services: 
	...
	
	mysql: 
		image: mysql:8.0 
		volumes: 
			- todo-mysql-data:/var/lib/mysql 
		environment: 
			MYSQL_ROOT_PASSWORD: secret 
			MYSQL_DATABASE: todos
```

We will also have to define a voluem

```
services:
	...
volumes: 
	todo-mysql-data:
```

The final compose file will look like so.

```yaml
services:
	app:
		image: node:18-alpine 
		command: sh -c "yarn install && yarn run dev" 
		ports: - 3000:3000 
		working_dir: /app 
		volumes: 
			- ./:/ app 
		environment: 
			MYSQL_HOST: mysql 
			MYSQL_USER: root 
			MYSQL_PASSWORD: secret 
			MYSQL_DB: todos
	mysql:
		image: mysql:8.0 
		volumes: 
			- todo-mysql-data:/var/lib/mysql 
		environment: 
			MYSQL_ROOT_PASSWORD: secret 
			MYSQL_DATABASE: todos
volumes: 
	todo-mysql-data:
```

To run the file use the `compose` sub command (in the same directory your `docker-compose.yml` file is).

```
docker compose up -d
```

