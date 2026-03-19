Show and manipulate routing, network devices, interfaces and tunnels.
The Windows equivalent of `ip` is ipconfig.

Use the `addr` command to display all information about network interfaces on your system

```sh
ip addr
```

It will return an easily parseable list of interfaces
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:dc:90:f2 brd ff:ff:ff:ff:ff:ff
    inet 172.27.226.6/20 brd 172.27.239.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fedc:90f2/64 scope link 
       valid_lft forever preferred_lft forever
```

To query a specific interface by name, add the `show` command with the interface name

```
ip addr show eth0
```

Will print 

```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:dc:90:f2 brd ff:ff:ff:ff:ff:ff
    inet 172.27.226.6/20 brd 172.27.239.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fedc:90f2/64 scope link 
       valid_lft forever preferred_lft forever
```

### Adding an IP address to an interface

Use the `add` command to assign an IP address (with a subnet mask) to an interface

```sh
ip addr add <ip_address/msk> dev <device>
```

To assign IP 192.168.1.100 with the subnet mask of 255.255.255.0 to the `eth0` interface

```sh
ip addr add 192.168.1.100/24 dev eth0
```

### Removing an IP from an interface

To remove an IP address from an interface use the `del` command

```sh
ip addr del 192.168.1.100/24 dev eth0
```

### Configuring a default Gateway

To set the default gateway, use the `route` command

```sh
ip route add default via 192.168.1.1 dev eth0
```