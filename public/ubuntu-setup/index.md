# How I setup Ubuntu fresh install

<!--more-->

### Install earylyoom (Early Out Of Memory) Daemon

[View on GitHub](https://github.com/rfjakob/earlyoom)

```shell
sudo apt install earlyoom && \
sudo systemctl enable earlyoom && \
sudo systemctl start earlyoom
```

---

### Install Applications

* [Dropbox (deb)](https://www.dropbox.com/install-linux)
* Visual Studio Code (snap)
* Spotify (snap)
* Mailspring (snap)
* [Enpass (deb)](https://www.enpass.io/support/kb/general/how-to-install-enpass-on-linux/)
* [Docker (deb)](https://docs.docker.com/engine/install/)
* [Kitematic (deb)](https://github.com/docker/kitematic/releases)
* [Private Internet Access (deb)](https://www.privateinternetaccess.com/pages/download)



---

### Finish Docker Snap Setup

```
sudo addgroup --system docker && \
sudo adduser $USER docker && \
newgrp docker && \
sudo snap connect docker:account-control :account-control && \
sudo snap connect docker:home :home && \
snap disable docker && \
snap enable  docker && \
newgrp docker-snap
```



---

### Setup Dropbox clipboard sync

#### Install dependencies:

```bash
sudo apt install xclip xdotool notify-osd yad
```

#### Create keyboard shortcuts:

Create a keyboard shortcut with "ctrl+alt+v" with command:

```bash
bash "/home/cody/Dropbox/Bash Scripts/clip" --copy-from
```

Create a keyboard shortcut with "ctrl+alt+c" with command:

```bash
bash "/home/cody/Dropbox/Bash Scripts/clip" --copy-to
```

Create a keyboard shortcut with "ctrl+alt+b" with command:

```shell
bash "/home/cody/Dropbox/Bash Scripts/clip" --open-in-browser
```



---

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

---

#### Setup Typora for Notes

```shell
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add - && \
sudo add-apt-repository 'deb https://typora.io/linux ./' && \
sudo apt-get update && \
sudo apt-get install typora -y && \
cp -a ~/Notes/Themes/. ~/.config/Typora/themes/
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

###### Last: 

Select the Ursine Umbra theme from the "Themes" menu

---

#### Setup the custom .desktop files for Nautilus and VS Code

```shell
cp ~/Dropbox/Ubuntu\ Customizations/Custom\ Launcher\ Files ~/.local/share/applications/ 
```

---

#### Install Sushi

```shell
sudo apt install gnome-sushi
```


