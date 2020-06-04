---
title: How I setup Ubuntu fresh install
date: 2020-05-19T17:51:28.000+00:00
description: This details how I like to setup my Ubuntu desktop, everything I like
  to install and settings I like to change.
featuredImage: "/images/optimized-ubuntu-banner.png"
toc: true
linkToMarkdown: true
tags:
- Linux
- Tips & Tricks
- How To
categories:
- Linux
lastmod: 2020-05-20T20:30:12.000+00:00

---
<!--more-->

{{< admonition type=info title="Download Referenced Files" open=true >}} [Click here to download the files referenced in this article from my Dropbox ](https://www.dropbox.com/sh/11olmidp2oyvjz4/AACtmBchqIfxx9MhAjlErJawa?dl=0){{< /admonition >}}

{{< admonition type=note title="File Paths" open=true >}} Note that with some of the commands you will have to change the path to the location that you saved the files, although I did use "\~/" and "$USER" variable where possible. I put the path that I use with my username in it because the main purpose of this post is to make it easier for me to setup my systems in the furtue. However, I thought others might find it useful. {{< /admonition >}}

### Install Applications

* [Visual Studio Code (snap)](https://snapcraft.io/code)
* [Spotify (snap)](https://snapcraft.io/spotify)
* [Mailspring (snap)](https://snapcraft.io/mailspring)
* [Docker (snap)](https://snapcraft.io/docker)
* [Dropbox (deb)](https://www.dropbox.com/install-linux)
* [Enpass (deb)](https://www.enpass.io/support/kb/general/how-to-install-enpass-on-linux/)
* [Kitematic (deb)](https://github.com/docker/kitematic/releases)
* [Private Internet Access (deb)](https://www.privateinternetaccess.com/pages/download)

***

### Install Support for ExFat

By default the linux kernal doesn't ship with support for ExFat. The ExFat filesystem allows you do have files larger than 4GB on a drive and is supported by more systems than EXT or NTFS. I use ExFat on all of my USB drives for this reason.

```Shell
sudo apt install exfat-fuse exfat-utils
```

***

### Install earylyoom (Early Out Of Memory) Daemon

[View on :(fab fa-github): GitHub](https://github.com/rfjakob/earlyoom)

Earlyoom kills processes faster than the kernels oom-killer when the system is running low on memory. This helps keep the system responsive, preventing you from sitting in-front of a computer that has slowed to a crawl while you wait on the kernel to kill the out of control process.

```shell
sudo apt install earlyoom && \
sudo systemctl enable earlyoom && \
sudo systemctl start earlyoom
```

***

### Finish Docker Snap Setup

```shell
    sudo addgroup --system docker && \
    sudo adduser $USER docker && \
    newgrp docker && \
    sudo snap connect docker:account-control :account-control && \
    sudo snap connect docker:home :home && \
    snap disable docker && \
    snap enable docker && \
    newgrp docker-snap
```

***

### Setup Dropbox clipboard sync

I created a custom script to use Dropbox (or really any file sync service) as a clipboard sync system. It only supports text, but that's the main thing I need. I am planning on putting up instructions on how to set this up for MacOS, IOS, and Android soon. It makes a nice universal clipboard sync system.

#### Install dependencies:

```shell
sudo apt install xclip xdotool notify-osd yad
```

#### Create keyboard shortcuts:

Create a keyboard shortcut with "ctrl+alt+v" with command:

```shell
bash "/home/cody/Dropbox/Bash Scripts/clip" --copy-from
```

Create a keyboard shortcut with "ctrl+alt+c" with command:

```shell
bash "/home/cody/Dropbox/Bash Scripts/clip" --copy-to
```

Create a keyboard shortcut with "ctrl+alt+b" with command:

```shell
bash "/home/cody/Dropbox/Bash Scripts/clip" --open-in-browser
```

***

### Setup Resilio Sync for notes and whatever else I want

[Download The Deb](https://help.resilio.com/hc/en-us/articles/206178924)

###### Enable in Systemd and adjust permissions & groups for the Notes folder:

```shell
sudo systemctl enable resilio-sync && \
sudo usermod -aG $USER rslsync && \
sudo usermod -aG rslsync cody && \
mkdir /home/$USER/Notes && \
sudo chown -R $USER:rslsync /home/$USER/Notes && \
sudo chmod g+rw /home/$USER/Notes
```

###### Goto the web interface and setup Resilio sync:

Remember to logout of the DE and back in before finishing setup!!

Don't forget to unlink the identity first, and link it to the unified identity.

go to the [Web Gui](http://localhost:8888/gui/) to set it up

***

### Setup Typora for Notes

```shell
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add - && \
sudo add-apt-repository 'deb https://typora.io/linux ./' && \
sudo apt-get update && \
sudo apt-get install typora -y && \
```

###### Open preferences and:

* General
  * On Launch: Open custom folder
    * \~/Notes
  * Save & Recover: "Auto Save" = true
* Image
  * When Insert...
    * Copy image to custom folder
    * \~/Notes/images
    * Apply above rules to local images = true
    * Apply rules to online images = true
    * User relative path if possible = true
    * Allow upload .... = false
    * Auto escape .... = false
    * Image uploader = none

###### Select the theme:

Close Typora and type this in the Terminal.

```shell
cp -a ~/Notes/Themes/. ~/.config/Typora/themes/
```

Open Typora

Select the Ursine Umbra theme from the "Themes" menu.

***

### Setup the custom .desktop files for Nautilus and VS Code

This allows you to have custom actions when you right click app icons in the GUI. I have set these up with my favorite locations, however when you open the files customizing them should be self explanatory. The launcher files need to be placed in "\~/.local/shere/applications/".

{{< image src="/images/screenshot-nautilus-context-menu.png" caption="Context Menu Example"  src-l="/images/screenshot-nautilus-context-menu.png" linked=true  >}}

```shell
cp ~/Dropbox/Ubuntu\ Customizations/Custom\ Launcher\ Files ~/.local/share/applications/ 
```

***

### Install Sushi

[View on  :(fab fa-github): GitHub](https://github.com/GNOME/sushi)

Sushi is a quick preview app for Nautilus. Similar to the quick preview in Mac OS. You just hit the space-bar to preview a file.

{{< image src="/images/screenshot-sushi.png" caption="Sushi in Action"  src-l="/images/screenshot-sushi.png" linked=true  >}}

```shell
sudo apt install gnome-sushi
```

### Install Yaru Dark theme for VLC

[View on :(fab fa-gitlab): GitLab](https://gitlab.com/NovaQC/vlc-yaru-dark/)

The Yaru Dark theme makes VLC look like a native app.

{{< image src="https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/VLC_video.gif" caption="Image from NovaQC repository on GitLab"  src-l="https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/VLC_video.gif" linked=true  >}}

To enable the theme:

[Download Theme Here](https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/YaruDark.vlt)

Open VLC and go to Preferences > Interface, click the radial button that says "Use Custom Skin," and select the "YaruDark.vlt" file.

{{< image src="/images/screenshot-vlc-skin-prefs.png" caption="VLC Skin Preferences"  src-l="/images/screenshot-vlc-skin-prefs.png" linked=true  >}}

Then restart VLC and the skin will be active.