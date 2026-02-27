Installing Node LTS on Linux/WSL

Install `nvm`

```bash
nvm install --lts
```

Switch to the newly installed version

```bash
nvm use --lts
```

Verify

```bash
node version
node -v

npm version
npm -v
```

### New Project

Initiate a new Node project by running 

```bash
npm init 
```

This will prompt you with questions and create a new `package.json` file in the current directory.

To generate with a project name, without questions

```bash
npm init -y
```
