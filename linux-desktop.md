# Linux desktop and desktop apps

[Reference](https://codeburst.io/how-to-install-ubuntu-desktop-with-a-graphical-user-interface-in-wsl2-95911ee2997f)

## Install [PowerToys](https://github.com/microsoft/PowerToys)

This gives you some nice shortcuts and helpful tools for Windows. The alt+space keys brings up a quick bar that includes Ubuntu applications.

## Install [VcXsrv](https://sourceforge.net/projects/vcxsrv/)

This is an X11 Server.

Navigate through the options and be sure to check the box where it asks you to _Disable access control_.

## Poke a hole in your firewall

Go to the Windows Defender firewall and add a new rule to open **TCP port 6000**. After creating the rule, select it in the rule list and go to properties. Navigate to the **Scope** tab and in the bottom section, add the following IP: `172.16.0.0/12`.

## Add this to your `.zshrc` file

```
# WSL2 GUI
export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0.0 # in WSL 2
export LIBGL_ALWAYS_INDIRECT=1
```

## Install a desktop environment

```
sudo apt update
sudo apt --yes install ubuntu-desktop
```
