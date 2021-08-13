# SSH and friends

## Generate or copy over an id_rsa into `~/.ssh`

```
ssh-keygen
```

* Add the `id_rsa.pub` to [GitHub](https://github.com/settings/keys).

## Create a `~/.ssh/config` file

We'll need to place all the relevant server connection info in the config file.