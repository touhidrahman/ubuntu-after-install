# GNOME

### Install

Minimal:

```
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-add-repository ppa:gnome3-team/gnome3-staging
sudo apt-get update
sudo apt-get install gnome-shell
```

Full:

```
sudo apt install ubuntu-gnome-desktop
```

### Uninstall

```
sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get remove gnome-shell
sudo apt-get remove --auto-remove ubuntu-gnome-desktop
```

### Reconfigure login screen

```
sudo apt-get install lightdm
sudo dpkg-reconfigure gdm [# select lightdm ]
sudo apt-get remove gdm
```


# XFCE

### Install

Minimal


`sudo apt install xfce4 xfce4-goodies`


Full

`sudo apt install xubuntu-desktop`


### Uninstall

`sudo apt remove xubuntu-desktop xfce4 xfce4-goodies`


# KDE

### Install

Minimal

```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt install plasma-desktop
```

Full

`sudo apt install kubuntu-desktop`

# LXDE

`sudo apt install lxde`


# Cinnamon

### Install

```
sudo add-apt-repository ppa:embrosyn/cinnamon
sudo apt-get update
sudo apt-get install cinnamon
```

### Uninstall

```
sudo apt-get remove cinnamon
sudo apt-get autoremove
```

# Pantheon

Method 1:

```
sudo add-apt-repository ppa:elementary-os/daily
sudo add-apt-repository ppa:elementary-os/os-patches
sudo add-apt-repository ppa:elementary-os/testing
sudo add-apt-repository ppa:mpstark/elementary-tweaks-daily
sudo apt update
sudo apt dist-upgrade
sudo apt install elementary-theme elementary-icon-theme elementary-default-settings elementary-desktop
```

Or,

```
sudo add-apt-repository ppa:elementary-os/daily
sudo apt-get update
sudo apt-get install elementary-desktop
```

# Mate

Minimal

`sudo apt install mate-desktop-environment`

Full

`sudo apt install ubuntu-mate-desktop`


# Budgie

```
sudo add-apt-repository ppa:budgie-remix/ppa
sudo apt-get update
sudo apt-get install budgie-desktop
```

