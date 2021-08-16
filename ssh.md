# SSH and friends

## Generate or copy over an id_rsa into `~/.ssh`

```
ssh-keygen
```

* Add the `id_rsa.pub` to [GitHub](https://github.com/settings/keys).

## Create a `~/.ssh/config` file

We'll need to place all the relevant server connection info in the config file.

## Auto-launch `ssh-agent`

`ssh-agent` keeps your keys and certificates in memory so they can be used by various processes. We need to make sure the agent starts when we open the terminal. GitHub has some [nice documentation](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/working-with-ssh-key-passphrases#auto-launching-ssh-agent-on-git-for-windows) on the matter. The gist is, put the following in your `.bashrc` or `.zshrc`:

```
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2=agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```