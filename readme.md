# Install MongoDB, Express [Angular, React, Vue, DHTMLX, ...] and Node (MExN) on OSX

I recently switched to OSX from Ubuntu and now need to install all the stuff I need to work. Next to the bare minimal of software I will note down any transition material from Windows/Ubuntu to OSX.

## Visual Studio Code
[download Visual Studio Code](https://code.visualstudio.com/docs/?dv=osx) and open the .app file. I'm now typing this file from this very instance.

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