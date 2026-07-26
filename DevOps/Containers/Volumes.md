Docker allows us to create images and spawn containers that can be started, stopped and deleted by request.
When you create a container, lets say, a MySQL container that stored rows of tabular data, one this container is stopped, all the stores rows will be deleted and when the container will start up, it will always start at it was when it was created at the first time.

This is an intentional behavior!

To persist data between stopping or destroying and recreating a container, we use volumes.

Volumes share some similarities to [[Bind Mounts]] albeit used for different use cases 

For our MySQL example, we will create a volume and map it to the data directory where the database stores it tabular data.

To create a volume

```sh
docker volume create db_data
```

`db_data` is the volume name.

To mount the volume

```sh
docker run --mount type=volume,src=<volume-name>,dst=<mount-path>
```

A less explicit alternative would be..

```sh
docker run --volume <volume-name>:<mount-path>
```

More command details can be found at https://docs.docker.com/engine/storage/volumes/ 