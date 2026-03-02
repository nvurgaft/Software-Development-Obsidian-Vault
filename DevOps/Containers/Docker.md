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

Build an image from a Dockerfile

```sh
docker buld -t myapp .
```

Create and start a container

```sh
docker run -d -p 8080:80 nginx
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