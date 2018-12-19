Recovering U-Boot routers WRT3200ACM and WRT32X

-------------------------------------------------------------------------------
uboot-v004-wrt3200.bin	- The U-Boot file is only for the router WRT3200ACM
			  with NAND AMD/Spansion (S34ML02G2)
			  Boot version : v0.0.4

uboot-v100-wrt3200.bin	- U-Boot file is intended for WRT3200ACM routers.
			  This version works correctly with NAND AMD/Spansion
			  and Winbond/MXIC (S34ML02G2 and W29N02GV)
			  Boot version : v1.0.0

uboot-v209-wrt32.bin	- The U-Boot file is only for the router WRT32X 
			  with NAND Winbond/MXIC (W29N02GV)
			  Boot version : v2.0.9
-------------------------------------------------------------------------------
Attention, do not try to load U-boot not intended for your chip, it can lead to
inoperability of your router.
-------------------------------------------------------------------------------

1. To recovery the loader U-boot, copy the kwboot and file U-boot
to any folder in your PC running Linux.

2. Log into the PC terminal and navigate to folder files kwboot and U-boot.

3. Connect the USB-TTL adapter to the USB port on your computer and
to the router's serial port. In the terminal execute the command - 
	dmesg | grep -i ttyusb
to determine the sequence number of the initialized adapter
ttyUSB<N> (N = 0,1, ...) and set the access rights of -
	chmod 666 /dev/ttyUSB<N>

4. Execute the command -
	sudo ./kwboot -f -t /dev/ttyUSB<N> -b uboot-vXXX-wrt32NN.bin -B 115200 -p
and turn on the power router.
After the power is on the router and before the load starts,
it may take more than one minute.
When the download is complete, the router will be automatically
overloaded. To log on to the U-boot system, press any key on your
computer for a 3-second pause.

5. There are two possible options for loading the U-boot file into the memory
of the router, using the TFPT server or from the external USB Flash storage
connected to the USB2/eSATA connector.

Option A. (TFPT)
  A.1. Set the wired LAN-Port of your PC to static IP (for example, 192.168.1.99).
  A.2. Connect the Ethernet cable between yours computer and any LANRouter port
  and run TFPT-Server on the PC.
  A.3. In the terminal, following these commands -
	setenv ipaddr 192.168.1.1; setenv serverip 192.168.1.99
	tftp 0x8000000 uboot-vXXX-wrt32NN.bin

Option B. (USB)
  B.1. Format the USB Flash storage to the EXT4 type - 
	mkfs.ext4 -O ^64bit /dev/sdX
  and copy the uboot-vXXX-wrt32NN.bin file to the root.
  B.2. Insert the USB Flash storage into the USB2/eSATA connector of the router.
  B.3. In the terminal, following these commands -
	usb reset
	ext4load 0:1 0x8000000 uboot-vXXX-wrt32NN.bin

6. After loading the image of the U-boot file into the memory of the router,
run the following commands -
	nand device 0
	nand erase.spread 0 0x200000
	nand write 0x8000000 0 0xf4000
	resetenv
	reset

/ "kwboot" taken here - https://forum.armbian.com/index.php?/topic/4444-solved-kwboot-on-armada-38x/  /
