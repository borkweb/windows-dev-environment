# CLI Utilities

## Pre-requisites

Create a `~/bin` directory and add it to your `$PATH`.

```
mkdir bin
```

Add it to your `.bashrc` or `.zshrc`:

```
export PATH=$HOME/bin:$PATH
```

## Utilities

### Bat, a better `cat`

Install and link it:

```
sudo apt install bat
ln -s /usr/bin/batcat ~/bin/bat
```

Add to `.bashrc` or `.zshrc`:

```
# .bashrc
echo "alias cat='bat'" >> ~/.bashrc

# .zshrc
echo "alias cat='bat'" >> ~/.zshrc
```

### Exa, a better `ls`

Install `exa` via direct downloading the binary from the **Releases** page of the [exa repo](https://github.com/ogham/exa) and moving it to `~/bin`.