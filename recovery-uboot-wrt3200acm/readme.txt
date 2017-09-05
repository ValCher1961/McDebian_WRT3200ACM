1. To recovery the loader U-boot, copy the kwboot and image
mtdblock0 to any folder in your PC running Linux.

2. Log into the PC terminal and navigate to folder with
files kwboot and mtdblock0.

3.Plug the USB-TTL adapter into the USB port PC and Serial
interface WRT3200ACM. In the terminal execute the command - 
    dmesg | grep -i ttyusb
to determine the sequence number of the initialized adapter
ttyUSB<N> (N = 0.1 ...) and set the access rights of -
    chmod 666 /dev/ttyUSB<N>

4. Set the wired LAN-port of your PC to static IP 
(for example, 192.168.1.99).

5. Connect the ethernet cable between the PC and any LAN-port
in WRT3200ACM.

6. Run TFPT-Server on the PC.

7. Execute the command-
    sudo ./kwboot -f -t /dev/ttyUSB<N> -b mtdblock0 -B 115200 -p
and turn on the power WRT3200ACM.
After the power is on the WRT3200ACM and before the load starts,
it may take more than one minute to complete.
When the download is finished, the WRT3200ACM will automatically
reboot. To log in to U-boot, press any key on the PC during the
3 second him wait.

8. In the terminal, follow these commands:
    setenv ipaddr 192.168.1.1; setenv serverip 192.168.1.99
    nand device 0
    tftp 8000000 mtdblock0
    nand erase.spread 0 200000
    nand write 8000000 0 f3000
    reset


/ "kwboot" taken here - 
7. Execute the command-
    sudo ./kwboot -f -t /dev/ttyUSB<N> -b mtdblock0 -B 115200 -p
and turn on the power WRT3200ACM.
After the power is on the WRT3200ACM and before the load starts,
it may take more than one minute to complete.
When the download is finished, the WRT3200ACM will automatically
reboot. To log in to U-boot, press any key on the PC during the
3 second him wait.

8. In the terminal, follow these commands:
    setenv ipaddr 192.168.1.1; setenv serverip 192.168.1.99
    nand device 0
    tftp 8000000 mtdblock0
    nand erase.spread 0 200000
    nand write 8000000 0 f3000
    reset


/ "kwboot" taken here - 
7. Execute the command-
    sudo ./kwboot -f -t /dev/ttyUSB<N> -b mtdblock0 -B 115200 -p
and turn on the power WRT3200ACM.
After the power is on the WRT3200ACM and before the load starts,
it may take more than one minute to complete.
When the download is finished, the WRT3200ACM will automatically
reboot. To log in to U-boot, press any key on the PC during the
3 second him wait.

8. In the terminal, follow these commands:
    setenv ipaddr 192.168.1.1; setenv serverip 192.168.1.99
    nand device 0
    tftp 8000000 mtdblock0
    nand erase.spread 0 200000
    nand write 8000000 0 f3000
    reset


/ "kwboot" taken here - https://forum.armbian.com/index.php?/topic/4444-solved-kwboot-on-armada-38x/  /






