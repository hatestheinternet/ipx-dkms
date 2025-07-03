# ipx-dkms

Combined with `debuild`, this repository ~~will~~ should check out [pasis' IPX repository](https://github.com/pasis/ipx) and use it to create a DKMS-aware .deb so the module will always work as kernels update. It will also forcibly load the module on boot because I don't 100% know if auto-loading will work down the road.

Note there is no guarantee this will do anything but waste space and time, but it works kind of as expected when built and served using my [krapt](https://github.com/hatestheinternet/krapt) repo manager.

Eventually, the easiest path to this will be:
```
sudo curl https://apt.hatestheinternet.com/apt.hatestheinternet.com.gpg -o /etc/apt/trusted.gpg.d/apt.hatestheinternet.com.gpg
echo 'deb [arch=amd64] http://apt.hatestheinternet.com retro main' | sudo tee /etc/apt/sources.list.d/hti-retro.list
sudo apt update && sudo apt install ipx-dkms
```
