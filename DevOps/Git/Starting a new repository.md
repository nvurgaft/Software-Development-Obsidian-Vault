To initialize a new local git repository simple run the following command on your designated directory

```bash
git init
```

If successful, a `.git` directory will appear.

To copy and existing remove repository to the current directory run

```bash
git clone <remove address>
```

A `.git` directory will appear if one didn't already exist.

### .gitignore

A common best practice is to have a `.gitignore` file inside your main project directory, this file contains every file and directory that should be be managed by git. These resources will not be monitored be git, they will not be added to the repository, nor committed, and will not be uploaded to the remote in case of a push.

Always have this file

```bash
touch .gitignore
ls -la
drwxr-xr-x  7 nick nick  4096 Mar  1 14:56 .git
-rw-r--r--  1 nick nick     0 Mar  1 15:04 .gitignore
```