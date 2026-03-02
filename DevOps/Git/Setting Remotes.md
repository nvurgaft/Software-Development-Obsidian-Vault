Remotes are different location, usually a different host in your network, where the repository is copied to and from.

When you're cloning a remote repository the source remote is named `origin`.

To list the remotes associated with your repository run

```bash
git remote -v
```

It is important to specify remotes, otherwise you are just working locally and can't use the git network features 

* git push
* git clone
* git pull
* git fetch

When you `clone` a repository is may also specify the remote URL.

To add a remote

```bash
git remote add [name] [URL]
```

And to remove a remote

```bash
git remote remove [name]
```