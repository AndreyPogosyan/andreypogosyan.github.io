---
title: Customize the Linux Terminal
date: 2022-01-14 22:10:00 -400
categories: [linux, terminal]
tags: [linux,terminal]      # TAG names should always be lowercase
---

In order to customize the terminal, we are going to download a few packages as well as cusomtize the .zshrc file in order to make the terminal a alot better on the eyes :) . 

Let's begin!

## Intalling and switching to ZSH

Download and install ZSH with the following command:

```bash
Install ZSH
sudo pacman -S zsh
```
Once installed, in order to switch to zsh, we need to run the following command:

```bash
chsh
# when prompted, type the command below:
/bin/zsh
```

Once this step has been completed, in order to get the ZSH prompt, we need to log off and log back in.

## Configure PowerLevel10k

Source: <a href="Source: https://github.com/romkatv/powerlevel10k#installation">https://github.com/romkatv/powerlevel10k#installation</a>

To install this addon, simply navigate to the git hub repo in the link above and git clone the repo on to your local machine

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```
Once the step above has been configured, we can return to the terminal and type the following command to start the configuration part of PowerLevel10k

```bash
p10k configure
```
Then go through the prompts to customise your terminal:

<img src="/assets/img/powerlevel10k.png">
<img src="/assets/img/powerlevel10k_1.png">
<img src="/assets/img/powerlevel10k_2.png">
<img src="/assets/img/powerlevel10k_3.png">

## Install Neoftech

To install neofetch, simply run the following command:

```bash
sudo pacman -S neofetch
```

## Install MesloLGS Fonts

Simply follow the following link to to install the MesloLGS fonts
https://github.com/romkatv/powerlevel10k#fonts


## Install shell-color-scripts Package

To install shell-color-scripts package, do the following:

```bash
# This will install color-scripts from the AUR

yay -S shell-color-scripts
```

## Gogh Color Schemes

To get various different color schemes in the terminal, you can use Gogh found here: https://mayccoll.github.io/Gogh/

## Install LSD package

```bash
sudo pacman -S lsd
```

## Installing BAT package

```bash
sudo pacman -S bat
```

## Syntax Highlighting

In order to configure ZSH syntax highlighting, we need to do the following:

```bash
# STEP 1
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git

# STEP 2
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

## Auto-Suggestions

This is another very useful plugin that allows the terminal to suggest various commands based on your history, in other words, if there are commands that you use often, rather than going through history to find the command, the auto-suggestions plugin can by default suggest the command you’re trying to run vs you having to type it manually yourself. To enable auto-suggestions, we need to do the following:

```bash
# STEP 1
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions

# STEP 2 - add this to the .zshrc file
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```

## Configure the .ZSHRC

In order for all of these settings to be applied, we need to configure the .zshrc config file with things like alias, launch options, etc. Here’s my current .zshrc config file:

```bash
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

source ~/powerlevel10k/powerlevel10k.zsh-theme

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

## History ##
SAVEHIST=1000  # Save most-recent 1000 lines
HISTFILE=~/.zsh_history

## Color Script ##
colorscript -e space-invaders

## Neofetch ##
neofetch

## Misc ##
typeset -g POWERLEVEL9K_INSTANT_PROMPT=off

## Some Aliases ##
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias ll='ls -la'
alias cat='bat'

## colorize Man pages ##
export LESS_TERMCAP_mb=$'\e[1;32m'
export LESS_TERMCAP_md=$'\e[1;32m'
export LESS_TERMCAP_me=$'\e[0m'
export LESS_TERMCAP_se=$'\e[0m'
export LESS_TERMCAP_so=$'\e[01;33m'
export LESS_TERMCAP_ue=$'\e[0m'
export LESS_TERMCAP_us=$'\e[1;4;31m'

## LSD ##
command -v lsd > /dev/null && alias ls='lsd --group-dirs first'

## Syntax highlighting ##
source /home/theprof/Data/Programs/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

## Auto-Suggestions ##
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```