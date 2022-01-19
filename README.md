# Script for setting up the fingerprint reader on pop_os

* Is your device supported? 

List of fingerprint readers https://fprint.freedesktop.org/supported-devices.html

If you are unsure about your reader id, in the USB standards, there is a well-defined way to get Vendor ID and Product ID numbers from any USB device. 
lsusb just looks them up in a big table and displays the human-readable texts associated with those entries. 
The table is typically located at /usr/share/misc/usb.ids or /var/lib/usbutils/usb.ids.

* Troubleshooting

If you have issues with registering a fingerprint where the dialog says Fingerprint reader disconnected, 
I have found that this is usually related to previously trying to register the fingerprint through the cli or other means and not clearing it before trying to register again.
This python script can show you any registered fingerprint and adding the -d flag will delete these fingerprints.
