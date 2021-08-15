# Editors and IDEs

1. PHPStorm
1. DataGrip
1. Neovim (`sudo apt install neovim`)
1. [VSCode](https://code.visualstudio.com/) and turn setting sync on.

## Configuration

### PHPStorm

To work with projects within WSL, a Remote PHP Interpreter needs to be configured. You can learn how to do that within the [PHPStorm documentation](https://www.jetbrains.com/help/phpstorm/configuring-remote-interpreters.html). Essentially:

* Go to Settings > Languages & Frameworks > PHP
* Add a CLI Interpreter (3 dots to the right of the field)
* Click Add (the plus at the top left) then the Docker/WSL/etc option.
* Select the Ubuntu virtual machine
* Enter the path to php (find this by going to your WSL terminal and typing `which php`).
* Click OK until everything is saved.

### VSCode

Like PHPStorm, to work with projects in WSL, you need to add the [Remote Development pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack). Once you've installed that, you can access your WSL files. Here's the gist of the setup:

* Install [Remote Development pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
* In the icons on the left of VSCode, select the **Remote Explorer** icon (the one that looks like a monitor)
* From the dropdown at the top, select **WSL Targets**

This will open up a new window under the WSL and you can navigate and open folders as normal.

#### Setting up Xdebug for a Lando-based project

1. Create a `.vscode/` directory in your project root:

```
mkdir .vscode
```

2. Copy the [`launch.json`](editor/vscode/launch.json) file from this repo to the `.vscode/` directory.

That's it! Now you can debug happily in VSCode.