#!/bin/bash

sudo apt update
sudo apt upgrade -y

## Path correction for python (solved a compilation issue)
export PATH="/home/$USER/.local/bin:$PATH"

## Fingerprint reader
sudo apt purge --auto-remove fprintd libfprint-2-2 -y
sudo apt install gtk-doc-tools libfprint-2-dev libgirepository1.0-dev libgusb-dev libgudev-1.0-dev libpam-wrapper libpam0g-dev libpamtest0-dev libpolkit-gobject-1-dev libxml2-utils python3-pip python3-pypamtest git gettext valgrind -y
sudo apt install build-essential cmake gettext libdbus-1-dev libdbus-glib-1-dev libdebconfclient0 libglib2.0-dev libnss3-dev libpixman-1-dev libsystemd-dev meson python3-dbusmock libpam-fprintd udev libcairo2-dev -y
sudo pip install meson
pip install ninja gobject python-dbusmock

git clone https://gitlab.freedesktop.org/libfprint/fprintd.git
git clone https://gitlab.freedesktop.org/libfprint/libfprint.git

cd libfprint/
git fetch
latestTag=$(git describe --tags `git rev-list --tags --max-count=1`)
echo $latestTag
git checkout $latestTag
sudo chown $USER.$USER -R .
meson setup builddir
meson setup --wipe builddir
sudo ninja -C builddir install

cd ../fprintd/
git fetch
latestTag=$(git describe --tags `git rev-list --tags --max-count=1`)
echo $latestTag
git checkout $latestTag
sudo chown $USER.$USER -R .
meson setup builddir
meson setup --wipe builddir
sudo ninja -C builddir install

cd ..

sudo pam-auth-update

echo "You can now go to Settings -> Users to enroll your fingerprints"
echo "If the option does not appear, then there must have been an error in one of the steps above (probably the compilations, lines 31-34)"
