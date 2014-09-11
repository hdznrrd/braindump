http://stackoverflow.com/questions/20021300/usb-devices-are-not-recognized-in-virtualbox-linux-host



* Close virtualbox
* Execute in bash: sudo adduser YOURUSERNAME vboxusers
* Log out and log in again
* Attach to your PC the USB devices you want to be automatically mounted in the VM (virtual machine).
* Open Virtualbox
* Select your VM and go to "Machine" -> "Settings" -> "USB".
* Check "Enable USB Controller"; click on the icon with the USB plug and the plus, and click on the devices you want to be automatically mounted in the VM. Click "Ok".
* Click on "Start" toolbar button, and ensure your USB devices are recognized and mounted by the VM. Remember that you have to unmount them in the host OS too if you have to disconnect them after you exit the VM.

