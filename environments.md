# Environments

## Before you get rolling

Ensuring Docker runs swimmingly for Lando, there are a few hoops that need to be jumped through. Here are some steps that are typical:

1. Start Docker Desktop.
2. Go to Docker Desktop Settings and ensure that _Use the WSL 2 based engine_ is checked.
3. Restart your computer (yeah, I know. This step is lame.)
4. Start Docker Desktop _again_ and you'll receive a notification that Docker is connecting to the WSL2 Backend engine
5. You'll then (likely) get a System Security Network prompt asking if you want to let Docker use the network connection. The answer is: Yes, only on private networks.

That's it. Now you can proceed to the Lando setup!

## [Lando](https://github.com/lando/lando)

Do _not_ install the Windows install of Lando. Instead, you'll be installing the relevant package for your Linux distribution. In this example, we'll be using the `.deb` files.

**NOTE:** There's a neat project that Lando has called  [Hyperdrive](https://github.com/lando/hyperdrive). Sadly you _cannot_ use it for WSL and have xdebug function appropriately. **Do not use it.**

### Step 1 - Download and install the `.deb` package

1. Head to [Lando releases](https://github.com/lando/lando/releases).
2. Copy the link to the `.deb` file.
3. Head to your WSL home directory in command line.
4. Download the package.

```
wget THE_LINK_YOU_JUST_COPIED
```

5. Install the package, but ignore the hard docker-ce dependency because we'll be using the Windows Docker Desktop for docker magic.

```
sudo dpkg -i --ignore-depends=docker-ce WHATEVER.deb
```

_Replace `WHATEVER.deb` with the file you downloaded via wget._

### Step 2 - Start up Windows Docker Desktop

Open the Docker Windows app.

### Step 3 - Put your lando files in place on a new or pre-existing environment

#### Creating a new WordPress dev environment

1. Make the relevant directories for your dev environment:

```
# Make all directories in that path as needed.
mkdir -p ~/sites/dev

# Make a directory for Lando config files.
mkdir ~/sites/dev/.lando
```

2. Place the [`php.wsl.ini`](lando/.lando/php.wsl.ini) file that is included in this repo into the `~/sites/dev/.lando/` directory that you just created. This `php.wsl.ini` is just a `php.ini` file that has xdebug settings that are compatible with WSL2.

3. Place the [`.lando.yml`](lando/.lando.yml) file in the `~/sites/dev` directory.

4. Download WordPress and rename the directory to `wp`.

```
wget https://wordpress.org/latest.tar.gz

tar -xzf latest.tar.gz

mv wordpress wp

rm latest.tar.gz
```

5. Place the [`wp-config.php`](lando/wp/wp-config.php) file that is included in this repo into the `~/sites/dev/wp/` directory. This wp-config.php is set to dynamically grab the lando database connection info and sets the appropriate defines.

#### Adding override Lando files to a WordPress environment that has Lando already but isn't geared toward WSL.

1. Ensure there's a `.lando/` directory in the root of the project.

```
mkdir .lando
```

2. Place the [`php.wsl.ini`](lando/.lando/php.wsl.ini) file that is included in this repo into the `~/sites/dev/.lando/` directory that you just created. This `php.wsl.ini` is just a `php.ini` file that has xdebug settings that are compatible with WSL2.

3. Place the [`.lando.local.yml`](lando/.lando.local.yml) file in the project root. This will override the already existing `.lando.yml` to include the bits necessary for WSL / Xdebug compatibility.

### Step 4 - Start your project!

```
lando start
```
