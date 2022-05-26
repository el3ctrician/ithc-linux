
# Steps

## Updating Time 

`sudo date -s "$(wget --method=HEAD -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f2-7)"`

## Installing Kernel
- ```wget -qO - https://raw.githubusercontent.com/linux-surface/linux-surface/master/pkg/keys/surface.asc \
    | gpg --dearmor | sudo dd of=/etc/apt/trusted.gpg.d/linux-surface.gpg```
- ```echo "deb [arch=amd64] https://pkg.surfacelinux.com/debian release main" \
	| sudo tee /etc/apt/sources.list.d/linux-surface.list```

- `sudo apt update`
- `sudo apt install linux-image-surface linux-headers-surface`
- `sudo apt install linux-surface-secureboot-mok`
- `sudo update-grub`
- `sudo reboot`

## Installing Touch

- `sudo apt install git dkms build-essential`
- `git clone https://github.com/quo/ithc-linux.git`
- `cd ithc-linux`
- `make`
- `sudo make dkms-install`
- `sudo modeprobe ithc`
