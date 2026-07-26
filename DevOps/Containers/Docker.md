Docker is a popular, all in one container platform with a long-running daemon.

#### Some common commands

Get current version

```sh
docker version
```

Pull an image, in this example it's an Nginx image

```sh
docker pull nginx
```

Build an image from a [[Dockerfile]]

```sh
docker buld -t myapp .
```

* `-t` tags the image
* `.` tells the Dockerfile to look at the current directory

Create and start a container

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

Run a command inside a running container

```sh
docker exec -it my-container sh
```

Stop a container

```sh
docker stop my-container
```

Remove a container

```sh
docker rm my-container
```