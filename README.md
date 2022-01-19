# Enable-fingerprint-reader-for-pop_os
Script for setting up the fingerprint reader on pop_os

List of supported devices https://fprint.freedesktop.org/supported-devices.html

In the USB standards, there is a well-defined way to get Vendor ID and Product ID numbers from any USB device. 
lsusb just looks them up in a big table and displays the human-readable texts associated with those entries. 
The table is typically located at /usr/share/misc/usb.ids or /var/lib/usbutils/usb.ids.

If you have issues with registering a fingerprint where the dialog says Fingerprint reader disconnected, 
I have found that this is usually related to previously trying to register the fingerprint through the cli or other means and not clearing it before trying to register again.
This python script can show you any registered fingerprint and adding the -d flag will delete these fingerprints.
