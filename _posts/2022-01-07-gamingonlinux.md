---
title: Gaming on Linux
date: 2022-01-07 22:10:00 -400
categories: [linux, gaming]
tags: [linux]      # TAG names should always be lowercase
---


In this post, I am going to show you how to get gaming working on Linux. To make Gaming happen on Linux, there are a couple of packages that we will need to install:

* <b>Drivers:</b> For your GPU (Very Important)
* <b>Wine:</b> Compatibility layer for running Windows applications on POSIX compliant operating systems like Linux. More information here
* <b>Steam:</b> Game client for downloading games
* <b>Lutris:</b> Game client that allows you to centralize your games in one spot and giving a ton of customization options to get your games to work
* <b>ProtonGE:</b> A fork of wine that allows for Windows games to run on Linux. More information can be found <a href="https://www.protondb.com/">here</a>.

Let’s Begin!

## Pre-Requisites

The first and probably most important part of getting gaming to work, is identifying and figuring out what GPU is presently configured on the machine and if you have the proper driver available. To this, we can run a command in the terminal to view this information:

```bash
lspci | grep "Radeon"
```
or if you have an NVIDIA card, it would be something like this:

```bash
lspci | grep "NVIDIA"
```

<b>NOTE:</b> For AMD Cards, there’s no need to install any proprietary drivers, if you have a card that is from at least the last 5 years, the drivers for those AMD GPUs will be already in kernel, so there’s nothing to do. These drivers are open source. However, if you’re using an NVIDIA GPU, you will need to download the proprietary drivers yourself. The good news, is that there are a few Linux distros that will include the NVIDIA driver installation when you first intsall the Linux distro, so chances are, if you picked to install Linux with the proprietary drivers, you just need to validate if you’ve installed the latest drivers.

## Validate if the NVIDIA drivers are installed

To do this, we can simply issue something like this in the terminal to see what drivers are currently installed:

```bash
# NVIDIA Drivers
nvidia-smi
```
Once confirmed that the drivers are installed, we can proceed to the next steps.

## Installing WINE

To install WINE, it is actually quite simple, we just need to run the following command:

```bash
# For Wine run commmand

sudo pacman -S wine

# For Wine-staging run command

sudo pacman -S wine-staging
```

One Installed, we can move on to Steam.

## Installing Steam

To install Steam, it is the same as installing Wine, we simply run the following command:

```bash
sudo pacman -S steam
```

<b>NOTE:</b> When you’re installing Steam, you’ll get a prompt to chose the proper provider for the vulkan driver, you will need to chose the proper provider depending on your GPU

```bash
::There are 5 providers available for vulkan-driver:
::Repository extra
  1) amdvlk  2) nvidia-utils  3) vulkan-intel  4) vulkan-radeon  5) vulkan-swrast
```

In our case, we are using Radeon so this is what we will go with, <b>“vulkan-radeon“</b>, however, for nvidia, it would be <b>“nvidia-utils“</b>

After selecting the proper provider above, you will be asked to select the proper library to use next, with a similar output:

```bash
::There are 4 providers available for lib32-vulkan-driver:
::Repository multilib
  1) lib32-amdvlk  2) lib32-nvidia-utils  3) lib32-vulkan-intel  4) lib32-vulkan-radeon
```

Multilib is basically going to give us the capability to run 32bit apps on amd64. So in our case, we’re going with <b>lib32-vulkan-radeon</b> and if you have an NVIDIA card, it would be <b>lib32-nvidia-utils</b>.

## Installing Lutris

Installing Lutris is just as simple as installing Wine, we just issue the command:

```bash
sudo pacman -S lutris
```
Now, let’s look at how we can install ProtonGE.

## Installing ProtonGE custom Proton

Navigate to the following github page and download the appropriate version of ProtonGE for your games. I recommend to look at protondb.com for what other users are saying when using ProtonGE for a specific game. To install ProtonGE, follow this procedure.

<b>NOTE:</b> Steam needs to be installed and opened at least once before doing this procedure in order to avoid issues.

## Configure Steam with Proton

This step is very easy, once Steam is installed, we’re going to need to launch it and do the following:

Steam –> Settings –> Steam Play and click on <b>“Enable Steam Play for supported titles”</b> and <b>“Enable Steam Play for all other titles“</b>. Once these settings are applied, Steam will need to be restarted.

<img src="/assets/img/steam.png">
