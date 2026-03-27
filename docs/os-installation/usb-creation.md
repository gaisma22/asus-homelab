# Bootable USB Creation

## Tool Used
dd (data duplicator) - raw byte-level copy tool

## Command
sudo dd if=~/debian-12.12.0-i386-netinst.iso of=/dev/sdb bs=4M status=progress oflag=sync

## Device
- USB drive: /dev/sdb (29.7GB)
- Previous contents: Ubuntu 24.04.3 LTS bootable image (wiped)
- Written: Debian 12.12.0 i386 netinst ISO

## Why dd and not a GUI tool
dd writes directly to the device at the byte level, skipping the
filesystem entirely. Bootable media requires this because the boot
sector and partition structure have to be written exactly as the
ISO defines them. A regular file copy would not produce a bootable drive.

## After Writing
sudo eject /dev/sdb was run to flush all write buffers before
physically removing the drive.
