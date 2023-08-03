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
- Optional `livecd` user, if you prefer not to use root
- [`sudo`](https://www.sudo.ws/) and
[`polkit`](https://gitlab.freedesktop.org/polkit/polkit/)
rules for `livecd` user
- Boot option to use 25% of RAM for root partition
- Boot option to prevent loading the nvidia* modules: should be useful for older
nvidia cards unsupported by the latest drivers.
- NetworkManager applet for GUI network config in XFCE
- codecs and thumbnailers
- `en_GB` locale

### Comparing with upstream

Install [`meld`](https://meldmerge.org/) (or your favourite diff tool),
compare with e.g:

```shell
→ meld /usr/share/archiso/configs/releng releng
```

## Important notes

If using the `livecd`, become `root` with e.g. `sudo -i` **before** starting the
installation.

One should not generally install software when booting as a live disk.
The "use 25% of RAM as root fs space" option is for those who know what they're
doing.

### Build notes

Use disk label `ARCHZFS` for the ISO, e.g:

```shell
sudo mkarchiso -w /tmp/archiso-tmp -o /some/path/for/iso/ -L ARCHZFS -v $(pwd)/releng
```

## Known issues

Some of the XFCE icons are missing: this is due to the DE's default icon theme.
