# Install Geary 0.11.0 on Ubuntu 

First, download the tarball from https://download.gnome.org/sources/geary/0.11/. You can also open up a terminal window and copy the following command to download.

`wget https://download.gnome.org/sources/geary/0.11/geary-0.11.0.tar.xz`

Then extract the tarball. 

`tar xvf geary-0.11.0.tar.xz`

Install build dependencies for Geary in Ubuntu 16.04. intltool is used to generate .desktop file.

`sudo apt-get install valac libgirepository1.0-dev intltool cmake desktop-file-utils gnome-doc-utils libcanberra-dev libgee-0.8-dev libglib2.0-dev libgmime-2.6-dev libgtk-3-dev libsecret-1-dev libxml2-dev libnotify-dev libsqlite3-dev libunique-3.0-dev libwebkitgtk-3.0-dev libmessaging-menu-dev libunity-dev libgcr-3-dev`

`cd geary-0.11.0`

`./configure`

`sudo make install`
