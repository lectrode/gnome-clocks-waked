# gnome-clocks-waked
gnome-clocks with waked support (arch linux PKGBUILD)

## Description
This provides an Arch Linux (and derivatives) PKGBUILD for `gnome-clocks` that has been patched to use [`waked`](https://aur.archlinux.org/packages/waked-git) to wake up the device for alarms, as well as other small patches as needed.

This uses and updates the following pieces:
* original [pkgbuild](https://gitlab.com/seath1/pkgbuild) by seath
* updated [patches](https://gitlab.alpinelinux.org/alpine/aports/-/tree/master/community/gnome-clocks) from postmarketOS ([implementation tracker](https://gitlab.com/postmarketOS/pmaports/-/issues/1170)).
* current `gnome-clocks` [pkgbuild](https://github.com/archlinux/svntogit-packages/blob/packages/gnome-clocks/trunk/PKGBUILD)

Additional patch(es):
* Add [support](https://gitlab.gnome.org/GNOME/gnome-clocks/-/issues/277) for lock-screen actions in Phosh (`0003-add-lock-screen-actions.patch`)

## License
* Should be GPL - let me know if there are any overlooked conflicts from sources

## Installation
* This depends on [`waked`](https://aur.archlinux.org/packages/waked-git), which in turn depends on [`sdbus-ccp`](https://aur.archlinux.org/pkgbase/sdbus-cpp) (both in the AUR)
* `git clone https://github.com/lectrode/gnome-clocks-waked; cd gnome-clocks-waked`
* `makepkg -si`
* `sudo systemctl enable waked --now` #required for alarms to wake up device from suspend
* reboot or run `/etc/xdg/autostart/gnome-clocks.desktop`

## Usage
* This is a backend implementation utilizing an existing interface. As such, all you need to do to use/test this is
   * launch `gnome-clocks`
   * set an alarm (i.e. for a minute from now)
   * suspend
   * Your device should wake up in short order for the alarm you just set
