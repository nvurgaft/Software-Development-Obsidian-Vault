`less` is a better version of `more`, it's a content reader with pagination. It can read files and standard output piped to it.

To read a file using less

```sh
less ./server.js
```

You can redirect content into less using the pipe operator `|` 

```sh
cat /etc/passwd | less
```

You can `echo` into less

```sh
echo $PATH | less
```

Inside less, you can scroll the contents using the arrows keys and the page-up and page-down keys.

To quit less, simply type `q`