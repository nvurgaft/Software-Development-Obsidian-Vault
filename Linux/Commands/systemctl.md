# systemctl
#linux 

`systemctl` allows you to control system services.

Simply running the `systemctl` command will print all the currently existing services inside the system.

You can look for a specific service and it's description (if exists) using [[grep]]

```sh
systemctl | grep "nginx"
```

You can start a service 

```sh
systemctl start nginx
```

Stop it

```sh
systemctl stop nginx
```

Or Restart it

```sh
systemctl restart nginx
```

If the service fails to start, running status can reveal the cause of the failure.

```sh
systemctl status nginx
```
