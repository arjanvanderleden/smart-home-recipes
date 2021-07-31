# Screen rotation

## Rotate screen
- Change orientation of screen (for portraitmode kiosks)
```
sudo nano /boot/config.txt
```
```
# uncomment if black border
# disable_overscan=1
# comment out for rPi 4# dtoverlay=vc4-fkms-V3D

display_rotate=1 #1：90；2: 180； 3: 270
```
## Rotate touch
```
sudo apt install xserver-xorg-input-synaptics
sudo mkdir /etc/X11/xorg.conf.d
sudo cp /usr/share/X11/xorg.conf.d/40-libinput.conf /etc/X11/xorg.conf.d/
```
```
sudo nano /etc/X11/xorg.conf.d/40-libinput.conf
```

Find section for touch devices (Identifier "libinput touchpad catchall") and add line with Option "CalibrationMatrix"

```
    ...
    Option "CalibrationMatrix" "0 1 0 -1 0 1 0 0 1"
    ...
```
￼
- 90 degree: Option "CalibrationMatrix" "0 1 0 -1 0 1 0 0 1"
- 180 degree: Option "CalibrationMatrix" "-1 0 1 0 -1 1 0 0 1"
- 270 degree: Option "CalibrationMatrix" "0 -1 1 1 0 0 0 0 1"
