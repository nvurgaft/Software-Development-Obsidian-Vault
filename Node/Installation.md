### Installing Node LTS on Linux/WSL

First you will need to install the [Node Version Manager](https://github.com/nvm-sh/nvm) (`nvm`).

Using `curl`

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
```

Or using `wget`

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
```

For more information and other methods of installation, visiting the _Installation_ section at https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating

Then use `nvm` to install the latest, stable version of node.

```bash
nvm install --lts
```

Switch to the newly installed version

```bash
nvm use --lts
```

To verify your installation

```bash
node version
node -v

npm version
npm -v
```

### New Project

Create a new directory and `cd` into it, then initiate a new Node project by running 

```bash
npm init 
```

This will prompt you with a series of questions about your new project, after which it will create a new `package.json` file in the current directory.

To generate a project name, without questions

```bash
npm init -y
```
