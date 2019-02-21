# Autoenv

The default environment file is `ENV.in`/`ENV.out`.

#### Autoenv automatically sources (known/whitelisted) `ENV.in` and `ENV.out` files.

This plugin supports enter and leave events. By default `ENV.in` is used for entering, and `ENV.out` for leaving. And you can set variable `CLICOLOR=1` for enabling colored output.

![](term.png)

## Example of use

- If you are in the directory `/home/user/dir1` and execute `cd /var/www/myproject` this plugin will source following files if they exist

```
/home/user/dir1/ENV.out
/home/user/ENV.out
/home/ENV.out
/var/ENV.in
/var/www/ENV.in
/var/www/myproject/ENV.in
```

- If you are in the directory `/` and execute `cd /home/user/dir1` this plugin will source following files if they exist

```
/home/ENV.in
/home/user/ENV.in
/home/user/dir1/ENV.in
```

- If you are in the directory `/home/user/dir1` and execute `cd /` this plugin will source following files if they exist

```
/home/user/dir1/ENV.out
/home/user/ENV.out
/home/ENV.out
```

## Examples of `ENV.in` and `ENV.out` files

### For node.js developing:

### ENV.in

```sh
nvm use node
OLDPATH=$PATH
export PATH=`pwd`/node_modules/.bin:$PATH

```

### ENV.out

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
