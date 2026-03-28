# Drive Configuration

## Drive Layout
- `sda` (4GB SSD) — OS drive
  - `sda1` 2.8GB — root filesystem `/`
  - `sda2` 1K — extended partition container
  - `sda5` 975MB — swap partition
- `sdb` (7.5GB SSD) — data drive
  - `sdb1` 7.5GB — mounted at `/mnt/data`

## Why Separate Drives
OS and data are intentionally separated. If the OS drive
fails or needs reinstalling, data on `sdb` is untouched.
This mirrors how production servers are configured.

## Filesystem
- Type: `ext4`
- Formatted with: `mkfs.ext4 /dev/sdb1`
- Mount point created: `sudo mkdir -p /mnt/data`

## Persistent Mount
Added to `/etc/fstab` using UUID so mount survives reboots.
Device names like `/dev/sdb` can shift after adding new drives.
UUID never changes regardless of device name assignment.

## Verified With
- `sudo umount /mnt/data`
- `sudo mount -a` — no errors
- `df -h` — confirmed mounted correctly
