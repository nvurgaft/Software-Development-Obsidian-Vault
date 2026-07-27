Docker is a popular, all in one container platform with a long-running daemon.

### Common commands

Get current version

```sh
docker version
```

Pull an image, in this example it's an Nginx image

```sh
docker pull nginx
```

### Starting the container

Build an image from a [[Dockerfile]]

```sh
docker buld -t myapp .
```

* `-t` tags the image
* `.` tells the `Dockerfile` to look at the current directory

Spin up a container

```sh
docker run -d -p 8080:80 nginx/latest
```

- `-d` - run the container in detached mode (in the background)
- `-p 8080:80` - map port 8080 of the host to port 80 in the container
- `nginx/latest` - the image to use and the version (`latest` uses the latest version)

This command can be shortened 

```sh
docker run -dp 8080:80 nginx/latest
```

List running containers

```sh
docker ps
```

List container logs

```sh
docker logs my-container
```

### Running commands

Run a command inside a running container, for example

```sh
docker exec -it my-container uname -a
```

Will execute `uname -a` that will print the OS information

To open an interactive shell, run

```sh
docker exec -it my-container sh
```

or `bash` (whatever shell is installed on the container OS).

### Stopping the container

Stop a container using it's id or name

```sh
docker stop my-container
```

Remove a container using it's id or name

```sh
docker rm my-container
```