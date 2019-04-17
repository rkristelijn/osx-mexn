# Install MongoDB, Express [Angular, React, Vue, DHTMLX, ...] and Node (MExN) on OSX

I recently switched to OSX from Ubuntu and now need to install all the stuff I need to work. Next to the bare minimal of software I will note down any transition material from Windows/Ubuntu to OSX.

## Visual Studio Code

[download Visual Studio Code](https://code.visualstudio.com/docs/?dv=osx) and open the .app file. I'm now typing this file from this very instance. See [Visual Studio Code Tips](#visual-studio-code-tips) below for more information.

I need the following list of software:

- MongoDB
- git
- Node / NPM / Yarn
- MongoDB

Additional I need:

- Slack - (app store)

## Git

Git is natively installed, you may need xcode installation

```bash
git --version
git version 2.17.2 (Apple Git-113)
```

Alternatively you can go here:
[download](https://nl.atlassian.com/git/tutorials/install-git): `git-2.21.0-intel-universal-mavericks.dmg` seems the latest version on Sourceforge. However when you download, you will need to accept the installer in a special way so it accepts the certificates. I currently go with 2.17.2 as this seems to do the job.

## Node

[source](https://blog.teamtreehouse.com/install-node-js-npm-mac) - Use these steps to install brew and node.\

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install node

node -v
v11.11.0
npm -v
6.7.0
```

if you can't install brew because of privilages, just download Node from [nodejs](https://nodejs.org/en/download/) and install from there.

## MongoDB

[source](https://treehouse.github.io/installation-guides/mac/mongo-mac.html) - Use below steps to install MongoDB. Check the source for more information.

```bash
brew update
brew install mongodb
mkdir -p /data/db
sudo chown -R `id -un` /data/db

mongo --version
MongoDB shell version v4.0.3
git version: 7ea530946fa7880364d88c8d8b6026bbc9ffa48c
allocator: system
modules: none
build environment:
    distarch: x86_64
    target_arch: x86_64

brew services list | grep mongodb
brew services start mongodb
brew services stop mongodb
```

again, if you don't have brew, install using [these steps](https://medium.com/@saurabhkumar_4718/install-mongodb-without-homebrew-on-mac-os-2a98b68ab09c)

## Migrate to OSX from Ubuntu/Windows

# Physical

- Windows-button is now Command, this is also used for copy-pasting.
- I have pressed ` instead of left shift and \ instead of enter several times already
- Where are my function keys? - todo: need to find alternatives
- Home, End, Page Up, Page Down... ?
- Printscreen, lock the screen

## OS

- how do I arrange and maximize my windows?

## Bash

Bash seems a lot nicer than bash on Ubuntu, as copy-paste just works, without having to press shift etc. However by default there are no colors, and the prompt is a but sober. Let's fix that. [This](https://scriptingosx.com/2017/04/about-bash_profile-and-bashrc-on-macos/) isn't helping a lot, and both `~/.bashrc` and `~/.bash_profile` are not there. I've created a new file `~/.bash_profile`.

```bash
git_branch() {
  git branch 2>/dev/null | grep '^*' | colrm 1 2
}

export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h\[\033[33;1m\]\w\[\033[m\](\[\033[33m\]\$(git_branch)\[\033[00m\])\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
alias ls='ls -GFh'
```

to apply these changes, just execute the file: `. ~/.bash_profile`

Old prompt:
`MACHINENAME:~ username$`

New prompt:
`username@MACHINENAME~(gitbranchname)$`

## Visual Studio Code Tips

### Add code to path

- **command+shift+p** - choose `Shell command: install 'code' command in PATH`. This enables typing `code .` from bash, so it opens VSC in this folder.

### My favorite plugins

- **[gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)** - for better git integration
- **[prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)** - when formatOnSave is enabled, default formatting rules are applied
- **[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)** - because code needs to be spelled right
- **[yuml](https://marketplace.visualstudio.com/items?itemName=JaimeOlivares.yuml)** - for diagramming in uml

# Problems installing homebrew?
If you get:
```
/usr/local/Homebrew/.git: Permission denied
Failed during: git init -q
```
Do:
`sudo install -d -o $(whoami) -g admin`
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
