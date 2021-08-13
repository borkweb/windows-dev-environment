# Pre-requisites

## [Hyper-V on Windows 10](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)

Open PowerShell as an Administrator and run:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

## WSL

Install WSL. Open cmd and type the following:

```
wsl --install
wsl --set-default-version 2
```

Next, install the Linux distro of your choice (Ubuntu) via the Microsoft Store.

## [Microsoft Terminal](https://github.com/microsoft/terminal)

Search for Winows Terminal in the Microsoft Store.

## [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

WSL 2 needs to be all set first.