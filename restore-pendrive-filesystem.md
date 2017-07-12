## Restoring your USB key to its original state using Linux:


Generally after making the USB as bootable USB, when you need to make it normal again

A. First we need to delete the old partitions that remain on the USB key.
```
sudo su
fdisk -l
```
and note your USB drive letter.

If you had made arch based boot drive (efi partition or multiple partition), use the following command:

`dd if=/dev/zero of=/dev/sdX bs=512 count=1`

Otherwise...

- `fdisk /dev/sdx (replacing x with your drive letter)`
- `d` to proceed to delete a partition
- Type `1` to select the 1st partition and press enter
- Type `d` to proceed to delete another partition (fdisk should automatically select the second partition)


B. Next we need to create the new partition.

- Type `n` to make a new partition
- Type `p` to make this partition primary and press enter
- Type `1` to make this the first partition and then press enter
- Press enter to accept the default first cylinder
- Press enter again to accept the default last cylinder
- Type w to write the new partition information to the USB key
- Type umount /dev/sdx1 (replacing x with your drive letter)


C. The last step is to create the fat filesystem.

`mkfs.vfat -F32 /dev/sdx1 (replacing x with your USB key drive letter)`

That's it, you should now have a restored USB key with a single fat 32 partition that can be read from any computer.
