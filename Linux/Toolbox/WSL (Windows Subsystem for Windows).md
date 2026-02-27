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