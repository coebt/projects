sudo apt update && sudo apt upgrade
reboot
sudo apt autoremove
sudo apt install ubuntu-restricted-extras
reboot
sudo apt install tp-smapi-dkms acpi-call-dkms smartmontools
sudo apt install lm-sensors
sudo apt install fancontrol read-edid i2c-tools
sudo apt install libi2c-dev python3-smbus
sudo sensors-detect
sensors
reboot
sudo apt install psensor

-----Disable suspend when logging in-----
Settings > Privacy & Security > Screen Lock > disable Automatic Screen Lock.
https://ubuntuhandbook.org/index.php/2020/05/lid-close-behavior-ubuntu-20-04/
Option 2: Use A Drop-in under /etc/systemd/logind.conf.d
sudo mkdir -p /etc/systemd/logind.conf.d
sudo gnome-text-editor /etc/systemd/logind.conf.d/lid-close-action.conf
*****Paste the following text into the text editor*****
[Login]
HandleLidSwitch=suspend
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore

Restart the machine.
-----Disable suspend when logging in-----

-----Solaar-----
https://pwr-solaar.github.io/Solaar/
sudo add-apt-repository ppa:solaar-unifying/stable
sudo apt update
sudo apt install solaar
reboot
-----Solaar-----

-----Flatpak-----
https://flathub.org/en/setup/Ubuntu
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
reboot
-----Flatpak-----

-----Install from repo-----
sudo apt install gnome-tweaks
sudo apt install gparted
sudo apt install gufw
sudo apt install gdebi
sudo apt install gnome-shell-extension-manager
sudo apt install gnome-shell-extensions
reboot
sudo apt install screenfetch
sudo apt install p7zip-full p7zip-rar
sudo apt install 7zip-standalone
sudo apt install exfat-fuse
sudo apt install mpv
sudo apt install mediainfo-gui
sudo apt install pavucontrol
Ignore suggestion to install pulseaudio.
reboot
-----Install from repo-----

-----Install from DEB or RUN files-----
BleachBit
Chrome
Master PDF
PIA
-----Install from DEB or RUN files-----

-----Stand-alone installations-----
adblink
MegaBasterdLINUX
-----Stand-alone installations-----

EXTRAS
-----Install Numix themes and icons-----
sudo apt install numix-gtk-theme numix-icon-theme numix-icon-theme-circle
reboot
https://numixproject.github.io/
https://packages.ubuntu.com/search?keywords=numix&searchon=names&suite=all&section=all
-----Install Numix icons and themes-----

-----Install tlp and tlp-rdw-----
sudo apt install tlp tlp-rdw
Installing these packages removes power-profiles-daemon, which removes the Power Mode options in Gnome.
https://askubuntu.com/questions/1440208/no-power-options-on-upgrade-to-22-04
Remove tlp and tlp-rdw and install power-profiles-daemon:
sudo apt remove --purge tlp tlp-rdw
sudo apt install power-profiles-daemon
reboot
If you get this message after removing tlp tlp-rdw: 
dpkg: warning: while removing tlp, directory '/var/lib/tlp' not empty so not rem
oved
Then run:
sudo rm /var/lib/tlp/rfkill_saved
-----Install tlp and tlp-rdw-----

-----Install Guix-----
sudo apt install guix
guix pull
-----Install Guix-----

-----Install Icecat-----
guix install icecat
-----Install Icecat-----

FIRMWARE
-----Update firmware-----
If your system supports firmware update delivery through lvfs, update your device firmware by:
sudo fwupdmgr refresh --force
Lists devices with available updates:
sudo fwupdmgr get-devices
Fetches list of available updates:
sudo fwupdmgr get-updates
sudo fwupdmgr update
-----Update firmware-----

FIXES
-----Gnome shell SIGSEGV-----
If you see this error:
gnome-shell crashed with SIGSEGV in meta_monitor_get_gamme_lut_size()
Upgrade NVIDIA driver metapackage from nvidia-driver-353 to the latest.
https://askubuntu.com/questions/1523706/gnome-apps-crash-with-sigsegv-error-after-switching-to-wayland-on-ubuntu-24-04

If you see this error:
gnome-shell crashed with SIGSEGV in g_hash_table_find()
This error occured after choosing to show the trash icon on the desktop in the Desktop Icons NG (DING) extension.
-----Gnome shell SIGSEGV-----

-----Remove this package if Gnome apps take too long to start-----
https://atchison.dev/ubuntu-24-terminal-not-starting-immediately/
sudo apt remove xdg-desktop-portal-gnome
-----Remove this package if Gnome apps take too long to start-----

-----Install Chromium from a repo-----
The suspend on log in and the slow Gnome app opening problems started after installing Chromium as a snap.
https://ubuntuhandbook.org/index.php/2024/05/install-chromium-ubuntu-2404/
https://xtradeb.net/apps/chromium/#lp-package-details
sudo add-apt-repository ppa:xtradeb/apps
sudo apt update
sudo apt install chromium
-----Install Chromium from a repo-----

DO NOT USE
Do not enable Automatic Screen Lock
-----Gnome extensions-----
Go to https://extensions.gnome.org/, install the GNOME Shell extension, and close the browser.
sudo apt install chrome-gnome-shell
Log out
Start the browser, click GNOME Shell extension, and allow the browser to start the WebExtension backends.
-----Gnome extensions-----

-----Install Chromium as a Snap-----
The slow Gnome app opening problems started after installing Chromium as a snap.
sudo apt install chromium-browser
-----Install Chromium as a snap-----

-----Use dbus-broker instead of dbus-daemon-----
https://www.reddit.com/r/openSUSE/comments/137adlo/heres_how_to_use_dbusbroker_instead_of_dbusdaemon/
systemctl --user status dbus.service
sudo apt install dbus-broker
systemctl enable dbus-broker.service
sudo systemctl --global enable dbus-broker.service
systemctl --user status dbus.service

This caused an error but it fixed slow Gnome app opening problem.
-----Use dbus-broker instead of dbus-daemon-----
