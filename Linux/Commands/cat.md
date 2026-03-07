The `cat` command concatenates files and print on the standard output.

#### Examples:

This will print to stdout the contents of the file `/etc/passwd`.
`
```sh
cat /etc/passwd
```

This will print (will make copy of) the contents of a file and move it to `less` as standard input.

```sh
cat .bashrc | less
```

Prints environment variables.

```sh
cat $PATH$
```
