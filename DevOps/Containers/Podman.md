Podman is a daemon-less, rootless first container engine designed to be more secure and Kubernetes friendly
#### Some common commands

```sh
podman ps
```

List all the containers running in the system

```sh
podman images
```

List all the images registered in the system

```sh
podman exec <container> <command>
```

Run a command inside a container, e.g.

```sh
podman exec hpi-ustlo ls /
```

Will return: 

```sh
afs         
bin      
dev      
etc    
home    
lib      
lib64    
lost+found    
....
```

Case 1: Open a log file using vim

```sh
podman exec container-prod-01 cat /var/log/optimize/service/service-console.log | grep -i 'error: ' | vim -
```

Case 2: Open an interactive shell from inside the container

```sh
podman exec -it <container-name> /bin/sh
- or -
poman exec -it <container-name> /bin/bash
```

`-it` opens an interactive shell