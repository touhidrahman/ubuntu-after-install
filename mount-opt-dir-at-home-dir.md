# Mount `opt` dir at `home` dir 

Make a home partition, tell the installer to mount it to /home. After install and on first boot create a directory called /home/opt. Then mount bind it to /opt.

Make sure /opt is empty before you do this. 

`mount -o bind /home/opt /opt`
for a manual mount.

For mounting on boot, edit `/etc/fstab`. Make sure you add below your home mount, which the installer should have added.

`/home/opt /opt none bind 0 0 `
