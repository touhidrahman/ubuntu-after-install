# UBUNTU AFTER INSTALL

A personal ubuntu after install list by [Touhidur Rahman](http://de.linkedin.com/in/touhidrahman)

### Jump to Section
* [Essential Repositories](#essential-repos)
* [Essential Installs](#essential-installs)
* [Development](#development)
	* [JDK](#java)
	* [Docker](#docker)
	* [LAMP Stack](#lamp)
	* [NodeJS](#nodejs)
	* [MongoDB](#mongodb)
* [Multimedia](#multimedia)
* [Graphics](#graphics)
* [Internet](#internet)
* [Utilities](#utilities)
* [Office](#office)

## ESSENTIAL REPOS (1-CLICK INSTALL)<a name="essential-repos"></a>
---
### Dev
`sudo add-apt-repository ppa:webupd8team/atom && sudo add-apt-repository ppa:webupd8team/java && sudo add-apt-repository ppa:nginx/stable && sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make`

### Internet
`sudo add-apt-repository ppa:webupd8team/tor-browser && sudo add-apt-repository "http://dl.google.com/linux/chrome/deb/ stable main"`

### Multimedia
`sudo add-apt-repository ppa:rvm/smplayer && sudo add-apt-repository ppa:videolan/stable-daily`
 
### System & Utilities
`sudo add-apt-repository ppa:noobslab/apps && sudo add-apt-repository ppa:wine/wine-builds && sudo add-apt-repository ppa:graphics-drivers/ppa`
 
### Others
`sudo add-apt-repository ppa:libreoffice/ppa`
 
 
## ESSENTIAL INSTALLS<a name="essential-installs" ></a>
---
`sudo apt-get install synaptic ppa-purge curl git build-essentials`

`sudo apt install ubuntu-restricted-extras`

`sudo apt install libavcodec-extra`
 
 
## DEVELOPMENT<a name="development" ></a>
---
### IDE
#### SublimeText 3
`sudo add-apt-repository ppa:webupd8team/sublime-text-3`

#### Atom
`sudo apt-get install atom`

#### Ubuntu Make Dev Env/IDE Installer
`sudo apt-get install ubuntu-make`
 
### IntelliJ IDEA (Set Update Possible by Default)
`sudo chown -R $(whoami) /opt/idea`


### Java JDK <a name="java" ></a>
From Oracle

`sudo add-apt-repository ppa:webupd8team/java
sudo apt-get install oracle-java8-installer`

From Ubuntu Repo (Open JDK)

`sudo apt-get install openjdk-8-jdk`


### Meteor
`curl https://install.meteor.com/ | sh`


### Dart
`sudo apt-get install apt-transport-https`

Get the Google Linux package signing key.

`sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'`

Set up the location of the stable repository.

`sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'`

`sudo apt-get update`

`sudo apt install dart`


# Docker <a name="docker"></a>

`sudo apt-get install     apt-transport-https     ca-certificates     curl     software-properties-common`

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

Verify that the key fingerprint is `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`.

`sudo apt-key fingerprint 0EBFCD88`

```bash
pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22
```
Install repository
```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

`sudo apt update`

`sudo apt-get install docker-ce`


## LAMP STACK <a name="lamp" ></a>
### MariaDB
`sudo apt-get -y install mariadb-server mariadb-client`

`mysql_secure_installation`

### Apache2
`sudo apt-get -y install apache2`

### PHP7
`sudo apt-get -y install php7.0 libapache2-mod-php7.0`

`sudo apt-get -y install php-pear php-imagick php-memcache  php7.0-pspell php-gettext php7.0 php7.0-cli php7.0-common php7.0-curl php7.0-gd php7.0-imap php7.0-intl php7.0-json php7.0-mbstring php7.0-mcrypt php7.0-mysql php7.0-opcache php7.0-pspell php7.0-readline php7.0-recode php7.0-sqlite3 php7.0-tidy php7.0-xml php7.0-xmlrpc php7.0-xsl php7.0-common php7.0-gd php7.0-mbstring php7.0-mcrypt php7.0-mysql php7.0-xml`
 
`systemctl restart apache2`
 
### PHPmyAdmin
 
`sudo apt-get install phpmyadmin`

_Allow phpmyadmin to login using root without sudo [* insecure for production]_
```
sudo mysql -u root
use mysql;
update user set plugin='' where User='root';
flush privileges;
Exit;
```

### Composer
`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`

`php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`

`php composer-setup.php`

`php -r "unlink('composer-setup.php');"`
 
`sudo mv composer.phar /usr/local/bin/composer`
 
#### Optional
Install PHP Accelerator
```
apt-get -y install php-apcu
systemctl restart apache2
a2enmod ssl
a2ensite default-ssl
systemctl restart apache2
```
Give Write Permission in ‘www’ dir [* Insecure method]
```
sudo adduser $USER www-data 
sudo chown -R www-data:www-data /var/www 
sudo chmod -R g+rw /var/www
```

### NginX (Removes Apache2)
[instructions article](http://www.unixmen.com/how-to-install-lemp-stack-on-ubuntu-16-x/)
```
sudo service apache2 stop
sudo apt-get remove --purge apache2 apache2-utils apache2.2-bin apache2-common -y
sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -Rf /etc/apache2 /usr/lib/apache2 /usr/include/apache2
sudo add-apt-repository ppa:nginx/stable 
sudo apt-get update
sudo apt-get install nginx
```

### NodeJS <a name="nodejs"></a>
#### V6-LTS
`curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`

`sudo apt-get install -y nodejs`

#### V8
`curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -`

`sudo apt-get install -y nodejs`
 
 
### MongoDB <a name="mongodb"></a>
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
sudo apt-get update
sudo apt-get install -y mongodb-org
sudo service mongod start
``` 
 
## MULTIMEDIA <a name="multimedia"></a>
### DVD Playback Essentials
```
sudo apt install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg
sudo apt-get install ffmpeg gxine libdvdread4 icedax tagtool libdvd-pkg easytag id3tool lame libxine2-ffmpeg nautilus-script-audio-convert libmad0 mpg321 libavcodec-extra gstreamer1.0-libav
```

### Exmplayer (SMPlayer Alternative)
`sudo add-apt-repository ppa:exmplayer-dev/exmplayer`

`sudo apt-get install exmplayer`

### Sayonara (Audio Player)
`sudo apt-add-repository ppa:lucioc/sayonara`

`sudo apt-get install sayonara`

### VLC
`sudo add-apt-repository ppa:videolan/stable-daily`

`sudo apt-get install vlc`
 
### SMPlayer
#### Qt4
`sudo apt-get install smplayer smplayer-themes smplayer-skins`
 
#### Qt5
`sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/smplayerdev/xUbuntu_16.04/ /' > /etc/apt/sources.list.d/smplayer.list"`

`sudo apt-get update`

`sudo apt-get install smplayer`
 
`wget -nv http://download.opensuse.org/repositories/home:smplayerdev/xUbuntu_16.04/Release.key -O Release.key`

`sudo apt-key add - < Release.key`

`sudo apt-get update`


### Handbrake
`sudo add-apt-repository ppa:stebbins/handbrake-releases`

`sudo apt-get install handbrake-gtk`

### Openshot
 
`sudo add-apt-repository ppa:openshot.developers/ppa`

`sudo apt-get install openshot openshot-doc`
 
### Screen Recorder
`sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder`

`sudo apt-get install simplescreenrecorder`
 
`sudo add-apt-repository ppa:mhsabbagh/greenproject`

`sudo apt install green-recorder`


### Youtube Downloader
`sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`

`sudo chmod a+rx /usr/local/bin/youtube-dl`

Update _youtube-dl_

`sudo youtube-dl -U`


### Radio
`sudo add-apt-repository ppa:haecker-felix/gradio-daily`

`sudo apt install gradio`
 
 
## GRAPHICS <a name="graphics"></a>
---
### GIMP
`sudo apt-get install gimp gimp-data gimp-plugin-registry gimp-data-extras`

### PhotoQT
`sudo apt-add-repository ppa:lumas/photoqt`

`sudo apt install photoqt`

### Darktable
`sudo add-apt-repository ppa:pmjdebruijn/darktable-release`

`sudo apt install darktable`


 
## UTILITIES <a name="utilities"></a>
---
`sudo apt-get install ubuntu-restricted-extras`

### File Compressors

`sudo apt-get install unace unrar zip unzip p7zip-full p7zip-rar sharutils rar uudeview mpack arj cabextract file-roller`


### WINE
```
sudo add-apt-repository ppa:wine/wine-builds
sudo apt-get update
sudo apt-get install --install-recommends wine-staging
sudo apt-get install winehq-staging
```

### PlayOnLinux
```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add - 
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux winbind
```
 
### Clean Repos
`sudo sh -c "apt-get update;apt-get dist-upgrade;apt-get autoremove;apt-get autoclean"`

### Redshift (Brightness Controll)
`sudo apt-get install redshift`

### Power Management
```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
sudo apt-get install tp-smapi-dkms acpi-call-dkms
sudo tlp start
```

`sudo apt-get install thermald`

`sudo apt-get install powertop`

`sudo apt-get install intel-microcode`


### Virtual Printer
`sudo add-apt-repository -y ppa:boomaga/ppa`

`sudo apt-get update && sudo apt-get install boomaga`

### Graphics Driver (Nvidia)
`sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic`

### Kernel Updater
`sudo apt-add-repository -y ppa:teejee2008/ppa`

`sudo apt-get update && sudo apt install ukuu`
```
Ukuu-gtk
```

### Boot Repair
`sudo add-apt-repository ppa:yannubuntu/boot-repair`

`sudo apt-get update && sudo apt-get install -y boot-repair`

```
Boot-repair
```
 
### Y-PPA-Manager
`sudo add-apt-repository ppa:webupd8team/y-ppa-manager`

`sudo apt install y-ppa-manager`

### Virtual Box
#### From Ubuntu
`sudo apt install virtualbox virtualbox-guest-additions-iso`
 
#### From Oracle (better)
`sudo sh -c "echo 'deb http://download.virtualbox.org/virtualbox/debian '$(lsb_release -cs)' contrib non-free' > /etc/apt/sources.list.d/virtualbox.list" && wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install virtualbox-5.1`

### KDE Connect (Allow Firewall)
```
sudo ufw allow 1714:1764/udp
sudo ufw allow 1714:1764/tcp
sudo ufw reload
```

### KVM
`sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
sudo apt-get install virt-manager`


## INTERNET <a name="internet"></a>
---
### Google Chrome

`sudo add-apt-repository "http://dl.google.com/linux/chrome/deb/ stable main"`

`sudo apt-get install google-chrome-stable`

### Xtreme Download Manager
`sudo apt-get install xdman`
 
### Google Drive
[instructions article](http://www.omgubuntu.co.uk/2017/04/mount-google-drive-ocamlfuse-linux)

`sudo add-apt-repository ppa:alessandro-strada/ppa`

`sudo apt update && sudo apt install google-drive-ocamlfuse`

Start 

``google-drive-ocamlfuse``

**only first-time** 

``mkdir ~/googledrive``
``google-drive-ocamlfuse ~/googledrive``

Unmount

``fusermount -u ~/google-drive``

### Iridium Browser
`wget -qO - https://downloads.iridiumbrowser.de/ubuntu/iridium-release-sign-01.pub|sudo apt-key add -`
```
cat <<EOF | sudo tee /etc/apt/sources.list.d/iridium-browser.list
deb [arch=amd64] https://downloads.iridiumbrowser.de/deb/ stable main
#deb-src https://downloads.iridiumbrowser.de/deb/ stable main
EOF
```
`sudo apt-get install iridium-browser`
 
### I2P Anonymous Browsing
`sudo apt-add-repository ppa:i2p-maintainers/i2p`

``sudo apt-get install i2p``
 
## THEMES/ICONS
`sudo apt-get install gnome-colors`
 
`wget -qO- https://raw.githubusercontent.com/PapirusDevelopmentTeam/papirus-icon-theme/master/install-papirus-home-kde.sh | sh`
 
 
## OFFICE <a name="office"></a>
---
### OnlyOffice
`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys CB2DE8E5`

Edit /etc/apt/sources.list and add
`deb http://download.onlyoffice.com/repo/debian squeeze main`

`sudo apt update && sudo install onlyoffice-desktopeditors`
 
### Calibre (eBook Management)
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
```
 
### LibreOffice
```
sudo add-apt-repository ppa:libreoffice/libreoffice-5-3
sudo apt-get update
sudo apt-get install libreoffice libreoffice-style-breeze
```

### Avro [Bangla Input Method]
#### Official
`sudo apt-get install git automake autoconf gjs ibus`

```
git clone git://github.com/sarim/ibus-avro.git
cd ibus-avro
aclocal && autoconf && automake --add-missing
./configure --prefix=/usr
sudo make install 
```

#### For KDE
`sudo apt install ibus-qt`

```
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
```
Finally,
1. Add ibus-daemon at System Settings > autostart
2. Uncheck “Embed preedit text in application window”
3. You may set a Bengali font in custom font field for nicer preview


#### Variant (* buggy)
`sudo apt install ibus-m17n avro-m17n`
 
 
