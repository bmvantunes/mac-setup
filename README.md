# This is my (new) Mac Setup

## Update
```sh
softwareupdate --all --install --force
```

## Instal Homebrew
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Now follow the instructions to add homebrew to the path!

## Make sure Homebrew is correctly installed in your computer
```sh
brew doctor
```

## Install latest version of Git
```sh
brew install git
brew link --overwrite git
```
close and open the terminal again.

## Install latest version of Vim
```sh
brew install vim
brew link --overwrite vim
```
close and open the terminal again.

## Install Node.js
```sh
brew install node
```

## Install Browsers
```
brew install --cask microsoft-edge
brew install --cask firefox
brew install --cask google-chrome
```

## Install oh-my-zsh 

### Install iTerm2
```sh
brew install --cask iterm2
```

## Install Rectangle
### rectangle will allow you to snap windows to the sides like on windows!
```sh
brew install --cask rectangle
```

Please now open the application and it will request some permissions :)

You can also make iTerm2 the default if you prefer iTerm

### Open iTerm and paste
```sh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

It will start the terminal with oh-my-zsh, then
```sh
export ZSH="$HOME/.oh-my-zsh"
omz plugin enable git vscode npm z
omz theme set mh
```

## Install vscode
```sh
brew install --cask visual-studio-code
vscie esbenp.prettier-vscode
vscie dbaeumer.vscode-eslint
vscie eamodio.gitlens
vscie EditorConfig.EditorConfig
vscie Prisma.prisma
vscie WallabyJs.quokka-vscode
vscie wix.vscode-import-cost

## if you have wallaby license
vscie WallabyJs.wallaby-vscode

## in case you don't have wallaby license
vscie Orta.vscode-jest
```

## Install Docker
```sh
https://docs.docker.com/desktop/mac/install/
```

## GitHub Authentication

```sh
git config --global user.name "Bruno Antunes"
```

```sh
git config --global user.email "bmvantunes@users.noreply.github.com"
```

### Create SSH key
```sh
ssh-keygen -t rsa
```

### Copy public key
```sh
pbcopy < ~/.ssh/id_rsa.pub
```

[GitHub Settings - Add SSH key](https://github.com/settings/keys)

## Sign GitHub commits to show "verified"

### Instal GPG
```sh
brew install gnupg
```

my email address will be: bmvantunes@users.noreply.github.com
Generate GPG Key using the defaults:
```sh
gpg --full-generate-key
```

See the Key:
```sh
gpg --list-secret-keys --keyid-format=long
```
You'll see something like:
```sh
$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot 
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

then:
```sh
gpg --armor --export 3AA5C34371567BD2
```

Copy that and past into the [GitHub GPG Keys](https://github.com/settings/keys)

then:
```sh
git config --global user.signingkey 3AA5C34371567BD2
```

```sh
if [ -r ~/.zshrc ]; then echo 'export GPG_TTY=$(tty)' >> ~/.zshrc; else echo 'export GPG_TTY=$(tty)' >> ~/.zprofile; fi
```

```sh
git config --global commit.gpgsign true
```

Only in case you want to change the last commit, because you committed it with wrong config:
```sh
git commit --amend --author="Bruno Antunes <bmvantunes@users.noreply.github.com>"
```

If you are prompted for the password all the time, follow this:
```
https://gist.github.com/bmvantunes/a2ec9e7f63240509a35b033177a138c2
```
