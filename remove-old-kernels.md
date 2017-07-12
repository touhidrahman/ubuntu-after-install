## Remove Old Kernels from Ubuntu

Get the list of Kernels

`dpkg --get-selections | grep linux-image`

Choose one from the listed and do an apt purge

`sudo apt-get purge linux-image-3.19.0-25-generic`
