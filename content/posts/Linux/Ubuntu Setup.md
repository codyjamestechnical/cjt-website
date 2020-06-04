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

### Install Support for ExFat

```Shell
sudo apt install exfat-fuse exfat-utils
```

***

### Install earylyoom (Early Out Of Memory) Daemon

[View on :(fab fa-github): GitHub](https://github.com/rfjakob/earlyoom)

```shell
sudo apt install earlyoom && \
sudo systemctl enable earlyoom && \
sudo systemctl start earlyoom
```

***

### Install Applications

* [Dropbox (deb)](https://www.dropbox.com/install-linux)
* [Visual Studio Code (snap)](https://snapcraft.io/code)
* [Spotify (snap)](https://snapcraft.io/spotify)
* [Mailspring (snap)](https://snapcraft.io/mailspring)
* [Enpass (deb)](https://www.enpass.io/support/kb/general/how-to-install-enpass-on-linux/)
* [Docker (deb)](https://docs.docker.com/engine/install/)
* [Kitematic (deb)](https://github.com/docker/kitematic/releases)
* [Private Internet Access (deb)](https://www.privateinternetaccess.com/pages/download)

***

### Finish Docker Snap Setup

```shell
    sudo addgroup --system docker && \
    sudo adduser $USER docker && \
    newgrp docker && \
    sudo snap connect docker:account-control :account-control && \
    sudo snap connect docker:home :home && \
    snap disable docker && \
    snap enable  docker && \
    newgrp docker-snap
```

***

### Setup Dropbox clipboard sync

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

###### Then enable in Systemd and adjust permissions & groups for the Notes folder:

```shell
sudo systemctl enable resilio-sync && \
sudo usermod -aG cody rslsync && \
sudo usermod -aG rslsync cody && \
mkdir /home/cody/Notes && \
sudo chown -R cody:rslsync /home/cody/Notes && \
sudo chmod g+rw /home/cody/Notes
```

###### Then goto the web interface and setup Resilio sync:

Remember to logout and back in before finishing setup!!

Don't forget to unlink the identity first, and link it to the unified identity.

go to the [Web Gui](http://localhost:8888/gui/) to set it up

***

#### Setup Typora for Notes

```shell
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add - && \
sudo add-apt-repository 'deb https://typora.io/linux ./' && \
sudo apt-get update && \
sudo apt-get install typora -y && \
```

###### Open preferences and:

* General
  * On Launch: Open custom folder
    * /home/cody/Notes
  * Save & Recover: "Auto Save" = true
* Image
  * When Insert...
    * Copy image to custom folder
    * /home/cody/Notes/images
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

#### Setup the custom .desktop files for Nautilus and VS Code

```shell
cp ~/Dropbox/Ubuntu\ Customizations/Custom\ Launcher\ Files ~/.local/share/applications/ 
```

***

#### Install Sushi

[View on  :(fab fa-github): GitHub](https://github.com/GNOME/sushi)

Sushi is a quick preview app for Nautilus. Similar to the quick preview in Mac OS.

```shell
sudo apt install gnome-sushi
```

#### Install Yaru Dark theme for VLC

[View on :(fab fa-gitlab): GitLab](https://gitlab.com/NovaQC/vlc-yaru-dark/)

The Yaru Dark theme makes VLC look like a native app.

{{< image src="https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/VLC_video.gif" caption="Image from NovaQC on gitlab"  src-l="https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/VLC_video.gif" linked=true  >}}

[Download Theme](https://gitlab.com/NovaQC/vlc-yaru-dark/-/raw/master/YaruDark.vlt)

To enable the theme just open VLC and go to:

Preferences > Interface, click the radial button that says "Use Custom Skin," and select the "YaruDark.vlt" file.

{{< image src="/images/screenshot-vlc-skin-prefs.png" caption="VLC Skin Preferences"  src-l="/images/screenshot-vlc-skin-prefs.png" linked=true  >}}

Then restart VLC and the skin will be active.