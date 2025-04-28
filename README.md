# gnome-clocks-waked
gnome-clocks with waked support (arch linux PKGBUILD)

## Description
This provides an Arch Linux (and derivatives) PKGBUILD for `gnome-clocks` that has been patched to use [`waked`](https://aur.archlinux.org/packages/waked-git) to wake up the device for alarms, as well as other small patches as needed.

This incorporates the following:
* base `gnome-clocks` [pkgbuild](https://gitlab.archlinux.org/archlinux/packaging/packages/gnome-clocks/-/commits/main) ([old](https://github.com/archlinux/svntogit-packages/blob/packages/gnome-clocks/trunk/PKGBUILD))
* waked ([original](https://gitlab.com/seath1/pkgbuild) by seath) ([updated](https://gitlab.alpinelinux.org/alpine/aports/-/tree/master/community/gnome-clocks) from [postmarketOS](https://gitlab.com/postmarketOS/pmaports/-/issues/1170))
* lockscreen actions [support](https://gitlab.gnome.org/GNOME/gnome-clocks/-/issues/277)
* custom default sounds ([alarm-clock-elapsed.oga](https://gitlab.gnome.org/GNOME/gnome-clocks/-/issues/60#note_920725), [complete.oga](https://gitlab.gnome.org/GNOME/gnome-clocks/-/issues/10#note_613136))

## License
* Code/patches should be mostly GPL - let me know if there are any overlooked conflicts from sources
* Included sound files sources and info can be found in "extra-sources" (Public domain and Unlicensed - provided by community)

## Installation
AUR Helper:
* `pikaur -S gnome-clocks-waked`

Manual:
* This depends on [`waked`](https://aur.archlinux.org/packages/waked-git), which in turn depends on [`sdbus-ccp<=1.5.0`](https://gitlab.archlinux.org/archlinux/packaging/packages/sdbus-cpp/-/tree/7ee4ab989a61165d60783e327cfeaf8a5076b031)
* `git clone https://github.com/lectrode/gnome-clocks-waked; cd gnome-clocks-waked`
* (Optional: replace sound files - see "Howto" below)
* `makepkg -si`
* `sudo systemctl enable waked --now` #required for alarms to wake up device from suspend
* reboot or run `/etc/xdg/autostart/gnome-clocks.desktop`

## Usage
* This does not change the interface of `gnome-clocks`. As such, using it is exactly the same.
* To test waking from suspend:
   * launch `gnome-clocks`
   * set an alarm (i.e. for a minute from now)
   * suspend
   * Your device should wake up in short order for the alarm you just set


## Replacing default sounds
As of this [merge request](https://gitlab.gnome.org/GNOME/gnome-clocks/-/merge_requests/253), `gnome-clocks` no longer respects the sounds included in the provided sound theme. This PKGBUILD replaces the bundled defaults for the following reasons:
* The replacement sound files are pretty sweet (credit to the original artists)
* This pkgbuild can be used as a semi-convenient way of bundling your own sound files (since they are now compiled into the main binary)
* While the [ability](https://gitlab.gnome.org/GNOME/gnome-clocks/-/issues/10) to customize the alarm sound is [in progress](https://gitlab.gnome.org/GNOME/gnome-clocks/-/merge_requests/252), it seems the main dev working on that has [stated](https://gitlab.gnome.org/GNOME/gnome-clocks/-/merge_requests/252#note_1827871) it "won't happen in the near future" - this is provided as a workaround

### Howto replace the sound files:
1) Clone this repo
2) Overwrite the included sound files with your own (make sure they are named the same)
3) Replace the b2sum hashes with "SKIP" in the PKGBUILD
4) Continue manual install steps

