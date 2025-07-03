# ipx-dkms

Combined with `debuild`, this repository ~~will~~ should check out [pasis' IPX repository](https://github.com/pasis/ipx) and use it to create a DKMS-aware .deb so the module will always work as kernels update. It will also forcibly load the module on boot because I don't 100% know if auto-loading will work down the road.

Note there is no guarantee this will do anything but waste space and time, but it works kind of as expected when built and served using my [krapt](https://github.com/hatestheinternet/krapt) repo manager.

Eventually, the easiest path to this will be:
```
sudo curl https://apt.hatestheinternet.com/apt.hatestheinternet.com.gpg -o /etc/apt/trusted.gpg.d/apt.hatestheinternet.com.gpg
echo 'deb [arch=amd64] http://apt.hatestheinternet.com retro main' | sudo tee /etc/apt/sources.list.d/hti-retro.list
sudo apt update && sudo apt install ipx-dkms
```

## Secure Boot

If your (virtual) machine is using secure boot and this is your first DKMS module you may have to approve a key. Basically, if this happens:

![The first DKMS module built on a secure boot system asking for a password](https://raw.githubusercontent.com/hatestheinternet/ipx-dkms/4ef978332d32fa07e6a8b6cae7b2d6168eda1408/image/secboot.png)

Just remember the crap password you set because, when you reboot that machine, you need to wander down the "Enroll MOK" path and it will eventually ask for it:

![The first step adding a new MOK when an EFI Proxmox virtual machine with secure boot enabled ... umm, reboots](https://github.com/hatestheinternet/ipx-dkms/blob/trunk/image/efimok.png?raw=true)

**NOTE** If this is indeed your first time, you will not be able to load the module until you've rebooted and enrolled the key.
