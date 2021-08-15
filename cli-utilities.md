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

### [Powerline](https://github.com/powerline/powerline)

#### Install
```
sudo apt install powerline
```

#### Fonts
You'll need [powerline fonts](https://github.com/powerline/fonts) and use those within your terminal. Follow [this blog post](https://medium.com/@slmeng/how-to-install-powerline-fonts-in-windows-b2eedecace58) for installing on WSL.

#### [Adding the prompt](https://www.ricalo.com/blog/install-powerline-windows/)

If using bash, add the following to your `.bashrc`:

```
if [ -f /usr/share/powerline/binding/bash/powerline.sh ]; then
	powerline-daemon -q
	source /usr/share/powerline/bindings/bash/powerline.sh
fi
```

If using zsh, add the following to your `.zshrc`:

```
if [ -f /usr/share/powerline/binding/zsh/powerline.zsh ]; then
	powerline-daemon -q
	source /usr/share/powerline/bindings/zsh/powerline.zsh
fi
```

#### Adding the prompt in vim or nvim

In `~/.vimrc` or `~/.config/nvim/init.vim`:

```
python3 from powerline.vim import setup as powerline_setup
python3 powerline_setup()
python3 del powerline_setup

set laststatus=2
```

#### Add git status colors in powerline

Rather than replay the steps here, I'll just point to [this blog post](https://kentakodashima.medium.com/customize-your-terminal-prompt-with-powerline-ed6eb884fabb).