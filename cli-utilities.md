# CLI Utilities

Just a quick note. When you open up a WSL prompt, you may be dropped into your Windows home directory rather than your WSL home directory. Simply type `cd` and you'll relocate yourself.

## Pre-requisites

### `~/bin`

Create a `~/bin` directory and add it to your `$PATH`.

```
mkdir bin
```

Add it to your `.bashrc` or `.zshrc`:

```
export PATH=$HOME/bin:$PATH
```

### Helpful symlinks

I like to have easy access to some of my files in Windows, so I symlink them to my home directory:

```
cd ~/
ln -s /mnt/c/Users/YOUR_WINDOWS_USER/Desktop
ln -s /mnt/c/Users/YOUR_WINDOWS_USER/Documents
ln -s /mnt/c/Users/YOUR_WINDOWS_USER/Downloads
ln -s /mnt/c/Users/YOUR_WINDOWS_USER/Dropbox
```

## Utilities

### `ag` (silversearcher-ag), faster than grep

```
sudo apt install silversearcher-ag
```

### `bat`, a better `cat`

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

### `exa`, a better `ls`

Install `exa` via direct downloading the binary from the **Releases** page of the [exa repo](https://github.com/ogham/exa) and moving it to `~/bin`.

### `fd`, a better `find`

```
sudo apt install fd-find
ln -s $(which fdfind) ~/bin/fd
```

### `tmux`, a terminal multiplexer

```
sudo apt install tmux
```

### `z`, a helpful jump command

If using zsh, rather than using `z` as a separate package, [use zsh-z](https://github.com/agkozak/zsh-z). If using oh-my-zsh, use this approach:

```
git clone https://github.com/agkozak/zsh-z $ZSH_CUSTOM/plugins/zsh-z
```

Then add `zsh-z` to the line of your `.zshrc` that specifies `plugins=()`, e.g., `plugins=( git zsh-z )`.

## Prompt

### [powerlevel10k](https://github.com/romkatv/powerlevel10k)

#### Install

Installing via oh-my-zsh:

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Find `ZSH_THEME` in your `~/.zshrc` and change it to:

```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Close your shell window and re-open to get prompted.

#### Fonts
You'll need [powerline fonts](https://github.com/powerline/fonts) and use those within your terminal. Follow [this blog post](https://medium.com/@slmeng/how-to-install-powerline-fonts-in-windows-b2eedecace58) for installing on WSL.