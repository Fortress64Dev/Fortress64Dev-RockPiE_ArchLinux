# Arch Linux ARM (aarch64) image for the Rock Pi E

* This is an up-to-date stock based Arch Linux aarch64 image including:
* mc, screen, base-devel, git, linux-headers, iw, networkmanager, rtl8821cu-morrownr-dkms-git, rtw88-dkms-git, rtl8812au-aircrack-ng-dkms-git and YAY AUR Helper.
* Included DKMS hardware (Monitor / Aircrack) support for the RTL8821CU, RTLl8723DU and RTL8812AU Wifi/Bluetooth chipsets.

Installation
------------------
Unpack the image file and copy the image to an 4GB or larger SD card: (assuming SD card at /dev/mmcblk0):

    tar -xvf RockPiE_ArchLinux_aarch64-*.img.xz
    dd if=RockPiE_ArchLinux_aarch64-*.img of=/dev/mmcblk0 bs=4M

or unpack it directly to the SD card:

    xzcat RockPiE_ArchLinux_aarch64-*.img.xz > /dev/mmcblk0
    
Default Login
------------------
login: 'root', password 'root'

user login: 'alarm', password 'alarm' (sudo enabled user for the YAY AUR Helper)

Increase partition size
------------------
The root partition has a default size of 3GB, to increase it
    cfdisk /dev/mmcblk0
    
Move to ' /dev/mmcblk0p1 ' and resize the partition to the desired size, save and exit.

Resize filesystem to max partition size:

    resize2fs /dev/mmcblk0p1

Cleanup
------------------
To reduce compilation time during updates

Remove the RTL8821CU module if unused:

    pacman -Rns rtl8821cu-morrownr-dkms-git
    
Remove the RTLl8723DU module if unused:

    pacman -Rns rtw88-dkms-git
    
Remove the RTL8812AU module if unused:

    pacman -Rns rtl8812au-aircrack-ng-dkms-git

Debug
------------------
    Pin 6   is GRD
    Pin 8   is RTX (UART2_TX_M1)
    Pin 10  is TXD (UART2_RX_M1)
