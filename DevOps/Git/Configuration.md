Git can be configured on 3 levels, the global level uses the global config file, system uses the system config file and local level that uses the repository config file.

A list of configuration options is listed at

```bash
git config
```

To set up the user name and email at the global level run:

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"
```

Use `--get` to read the property

```bash
git config --get user.name
```

Use `--set` to set a value to a property and `--unset` to unset it. 

The user's `.gitconfig` file is located the user home directory

```bash
cd ~
vim ./.gitconfig
```

