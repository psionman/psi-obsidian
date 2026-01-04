
## Create ISO on USB

Download ISO from [MS Windows](https://www.microsoft.com/en-gb/software-download/windows10ISO)

Install[Ventoy](https://www.ventoy.net/en/download.html) on the USB

Copy the Windows so in file manager.

## Prepare target disk

On laptop install another copy of Manjaro and create a 1Gb partition (sda3)

To see partitions, use:

```bash
sudo fdisk -l
```

Identify */dev/sda3* as the windows partition

Format as Fat32

```bash
sudo mkfs.vfat /dev/sda3
```


## Grub rescue

if we encounter *unknown file system* - grub rescue, [try this page](https://geekyshacklebolt.wordpress.com/2018/03/13/how-to-boot-from-grub-rescue-fixederror-no-such-partition/)

(my manjaro partition is/was (hd0,gpt6). Manjaro on sda6

However, can still get to grub menu by F2

Start Manjaro and connect to wifi

In terminal change to superuser

```bash
su
```

Use Manjaro-chroot

```bash
pamac install manjaro-tools-base
manjaro-chroot -a
```


Re-install grub

```bash
pacman -Syu grub
```

Install grub

```bash
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=manjaro --recheck
```

Update grub config

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

got error *Root system is not btrfs*

But just re-installed manjaro into the 1gb partition and it's ok

When installing windows delete the partition and then select it.

## Change file system in KDE partition manager

Unmount the partition

Right-click and go to Properties

Select file system from the dropdown box

Didn't seem to be satisfactory Windows wouldn't load

Unmount the file system

```bash
sudo umount /dev/sdX1
```


try
```bash
sudo mkfs.ntfs -Q /dev/sdX1
```
To display file system Type
```bash
df -T, --print-type
```
