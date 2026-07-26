Container networking refers to the ability for containers to connect to and communicate with each other, and with non-Docker network services.

Containers have networking enabled by default, and they can make outgoing connections. A container has no information about what kind of network it's attached to, or whether its network peers are also Docker containers. A container only sees a network interface with an IP address, a gateway, a routing table, DNS services, and other networking details.

To create a network

```sh
docker network create -d bridge my-net
```

And then run it

```sh
docker run --network=my-net -it busybox
```

### Drivers

Docker Engine has a number of network drivers, as well as the default "bridge". On Linux, the following built-in network drivers are available:

| Driver  | Description                                                         |
| ------- | ------------------------------------------------------------------- |
| bridge  | The default network driver.                                         |
| host    | Remove network isolation between the container and the Docker host. |
| none    | Completely isolate a container from the host and other containers.  |
| overlay | Swarm Overlay networks connect multiple Docker daemons together.    |
| ipvlan  | Connect containers to external VLANs.                               |
| macvlan | Containers appear as devices on the host's network.                 |

### Connecting to multiple networks

Connecting a container to a network can be compared to connecting an Ethernet cable to a physical host. Just as a host can be connected to multiple Ethernet networks, a container can be connected to multiple Docker networks.

For example, a frontend container may be connected to a bridge network with external access, and a [`--internal`](https://docs.docker.com/reference/cli/docker/network/create/#internal) network to communicate with containers running backend services that do not need external network access.

A container may also be connected to different types of network. For example, an `ipvlan` network to provide internet access, and a `bridge` network for access to local services.


Source: https://docs.docker.com/engine/network/