Prints the history of all commands ran by current user

Usage:

```sh
history
```

### Examples

An entry number will be prepended to the command, 1 is the earliest command ran.

```sh
root@netmachine:/mnt/c/Users/nick# history                                                                                                                 
1  cd /etc/opt/    
2  ls        
3  ls -la     
4  cd ../
5  exit
...
43  history
```

### Tips

`history` is very useful when combined with the command line `!` argument. appending the `!` before the command entry number will run this command

If running `history` prints
```sh
43  history
```

then entering `!43` will run this command, in this case `history`.

If the list is too long you can combine with `less`

```sh
history | less
```

If you only care for a history of a specific command type, use grep

```sh
history | grep "ps"
```
