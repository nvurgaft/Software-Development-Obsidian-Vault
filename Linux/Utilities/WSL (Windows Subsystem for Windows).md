WSL is a subsystem for Windows that allows to run distributions of Linux inside Windows environments without using virtual machines.

To install WSL enable it, go to the Window Features window (Turn Windows Features On or Off) and enable it.

To install a distro, open the command line 

 ```shell
 wsl --install <Distro name>
 ```

Help

```shell
wsl --help
```

Start 

```shell
wsl
```

Shutdown

```shell
wsl --shutdown
```

Run a command without starting the Linux default shell 

```shell
wsl --exec "command"
```

To log in using an existing system user run the `wsl` with the `-u` (or `--user`) argument, e.g. to start with the `www-data` user 

```sh
wsl -u www-data
```

To login using root

```sh
wsl -u root
```

By default wsl required you to create a regular user and using `su` to change into user will not be possible because no root password was set on install. making this the only way to set one and login as root. 