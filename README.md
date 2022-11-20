# gnome-clocks-waked
gnome-clocks with waked support (arch linux PKGBUILD)

## Description
This provides an Arch Linux (and derivatives) PKGBUILD for `gnome-clocks` that has been patched to use [`waked`](https://aur.archlinux.org/packages/waked-git) to wake up the device for alarms.

This uses and updates the following pieces:
* original PKGBUILD by seath [here](https://gitlab.com/seath1/pkgbuild)
* updated patches from postmarketOS [1](https://gitlab.com/postmarketOS/pmaports/-/issues/1170),[2](https://gitlab.alpinelinux.org/alpine/aports/-/tree/master/community/gnome-clocks).
* current `gnome-clocks` [pkgbuild](https://github.com/archlinux/svntogit-packages/blob/packages/gnome-clocks/trunk/PKGBUILD)

## License
* Should be GPL - let me know if there are conflicts from sources

## Installation
* This depends on [`sdbus-ccp`](https://aur.archlinux.org/pkgbase/sdbus-cpp) and [`waked`](https://aur.archlinux.org/packages/waked-git) (both in the AUR)
* `git clone https://github.com/lectrode/gnome-clocks-waked; cd gnome-clocks-waked`
* `makepkg -si`
* `sudo systemctl enable waked --now` #required for alarms to wake up device from suspend

