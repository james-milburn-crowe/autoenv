# Autoenv

The default environment file is `ENV_in`/`ENV_out`.

#### Autoenv automatically sources (known/whitelisted) `ENV_in` and `ENV_out` files.

This plugin supports enter and leave events. By default `ENV_in` is used for entering, and `ENV_out` for leaving. And you can set variable `CLICOLOR=1` for enabling colored output.

![](term.png)

## Example of use

- If you are in the directory `/home/user/dir1` and execute `cd /var/www/myproject` this plugin will source following files if they exist

```
/home/user/dir1/ENV_out
/home/user/ENV_out
/home/ENV_out
/var/ENV_in
/var/www/ENV_in
/var/www/myproject/ENV_in
```

- If you are in the directory `/` and execute `cd /home/user/dir1` this plugin will source following files if they exist

```
/home/ENV_in
/home/user/ENV_in
/home/user/dir1/ENV_in
```

- If you are in the directory `/home/user/dir1` and execute `cd /` this plugin will source following files if they exist

```
/home/user/dir1/ENV_out
/home/user/ENV_out
/home/ENV_out
```

## Examples of `ENV_in` and `ENV_out` files

### For node.js developing:

### ENV_in

```sh
nvm use node
OLDPATH=$PATH
export PATH=`pwd`/node_modules/.bin:$PATH

```

### ENV_out

```sh
nvm use system
export PATH=$OLDPATH

```

### For projects with `.env` or/and `.env.local`

```sh
source .env*
```


## Installation

### Using [zpm](https://github.com/zpm-zsh/zpm)

Add `zpm load zpm-zsh/autoenv` into `.zshrc`

### Using [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

Execute `git clone https://github.com/zpm-zsh/autoenv ~/.oh-my-zsh/custom/plugins/autoenv`. Add `autoenv` into plugins array in `.zshrc`

### Using [antigen](https://github.com/zsh-users/antigen)

Add `antigen bundle zpm-zsh/autoenv` into `.zshrc`

### Using [zgen](https://github.com/tarjoilija/zgen)

Add `zgen load zpm-zsh/autoenv` into `.zshrc`
