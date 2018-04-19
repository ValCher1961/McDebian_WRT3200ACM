**A test version of the kernel for WRT3200ACM and WRT32X located in Rootfs on an external drive.**

The location of the kernel in on the external medium allows you to not overwrite the stock firmware of the router, which eliminates the risks of ruining the router at a failed record in NAND, and if necessary, everything is simple and quickly return to its original state.

Since now the location of the kernel is not limited by the size of the selected area in nand, it became possible to include everything in the kernel. In this there are certainly pluses and minuses, but it's still a test core. The only external module of this kernel is the mwlwifi driver, which makes it easy to update.

[Rootfs](https://www.dropbox.com/s/j4tmtrjb6yhcalu/rootfs-armhf-stretch.tar.gz?dl=0) You can use the finished, it is absolutely pure, without any settings, it only has already set the password for the root (password - root) and added the mwlwifi module and driver. You can also collect rootfs yourself. How to do it you can find on the expanses of the Internet.

**So, let's get started.**

1. Mark the media to the number of partitions you need and format the first partition in EXT4.
```
mkfs.ext4 -O ^64bit /dev/sd<X>1
```
Download and unzip in the first section rootfs-armhf-stretch.tar.gz
```
wget --no-check-certificate https://www.dropbox.com/s/j4tmtrjb6yhcalu/rootfs-armhf-stretch.tar.gz
tar xvf rootfs-armhf-stretch.tar.gz
```
2. If you have collected your rootfs, copy the mwlwifi driver module located in the directory `/lib`

3. Load kernel-xxxxx into the root of the disk and rename it.
```
wget https://raw.githubusercontent.com/ValCher1961/McDebian_WRT3200ACM/master/test/kernel-xxxxx
mv ./kernel-xxxxx ./kernel
```
4. Connect the external drive to the USB2/ESATA router slot and connect the serial cable. 

5. Turn on the router and enter the U-boot to change the nandboot and altnandboot variables. 
In the depending of media type, run the following commands:

 For USB
```
setenv nandboot 'usb reset;ext4load usb 0:1 $defaultLoadAddr kernel;bootm $defaultLoadAddr'
setenv altnandboot 'usb reset;ext4load usb 0:1 $defaultLoadAddr kernel;bootm $defaultLoadAddr'
saveenv
```
 For SSD/HDD
```
setenv nandboot 'scsi init;ext4load scsi 0:1 $defaultLoadAddr kernel;bootm $defaultLoadAddr'
setenv altnandboot 'scsi init;ext4load scsi 0:1 $defaultLoadAddr kernel;bootm $defaultLoadAddr'
saveenv
```
6. Reboot and start to configure Debian.

Unfortunately I do not have wr32x and I can not check the health of the kernel on the router.
If anyone tries to install it on the router, tell us your result.
