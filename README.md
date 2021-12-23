# Build your own Arch Linux ISO with ZFS support

Can be used as a live/rescue disk, or as an Arch Linux installation disk.

## Prerequisites

### Build Prerequisites

- Working Arch Linux installation
- [archiso](https://wiki.archlinux.org/title/Archiso) installed
- Sufficient free disk space and RAM: 16GB of both is fine.

## Notable changes from upstream

- ZFS support
- Added "live CD" type XFCE4 graphical user environment with useful (to me)
desktop software and basic "rescue CD" functionality
- Current proprietary nvidia driver, since nouveau is pretty useless on modern
hardware (don't buy nvidia for Linux!)
- Removed older `ntfs-3g`: use in-kernel `ntfs3` instead
- Starts with `livecd` user, not `root`
- [`sudo`](https://www.sudo.ws/) and
[`polkit`](https://gitlab.freedesktop.org/polkit/polkit/)
rules for `livecd` user
- 
- New boot option to user 25% of RAM for root partition

### Important notes

If using as an install medium, become `root` with e.g. `sudo -l` **before**
starting the installation.

One should not generally install software when booting as a live disk.
The "use 25% of RAM as root fs space" option is for those who know what they're doing.

### Comparing with upstream

Install [`meld`](https://meldmerge.org/) (or your favourite diff tool),
compare with e.g:

```shell
→ meld /usr/share/archiso/configs/releng releng
```
