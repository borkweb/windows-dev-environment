# Environments

## [Lando](https://docs.lando.dev/guides/setup-lando-on-windows-with-wsl-2.html)

Installing Lando on Windows WSL is a little wonky. Luckily, Lando has a project called [Hyperdrive](https://github.com/lando/hyperdrive) that simplifies everything.

### Step 1 - Add Docker GPG key

First, add [Docker's official GPG key](https://docs.docker.com/engine/install/debian/):

```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Step 2 - [Install relevant packages](https://docs.docker.com/engine/install/debian/)

```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

### Step 3 - Install dependencies via Hyperdrive

```
curl -Ls https://github.com/lando/hyperdrive/releases/download/v0.6.1/hyperdrive > /tmp/hyperdrive \
  && chmod +x /tmp/hyperdrive \
  && /tmp/hyperdrive
```