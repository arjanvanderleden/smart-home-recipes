# Headless install Pi

- Download image zip

[https://www.raspberrypi.org/software/operating-systems/](https://www.raspberrypi.org/software/operating-systems/)

- Unzip, mount .img file
```
sudo hdiutil mount <your-image-file>.img
```

a ssh file in the root will enable ssh

- Add ssh file in root of mounted device
```
cd /Volumes/boot
touch ssh
```
- Add wpa_supplicant.conf file:
```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
scan_ssid=1
ssid="your_wifi_ssid"
psk="your_wifi_password"
}
```
- burn image to sd
- start pi from sd

|  | Default value |
| --- | --- |
| host | raspberrypi
| user | pi@< ipaddress > or pi@raspberrypi |
| pw | raspberry |

- change **host** and **password**:
```
ssh pi@raspberrypi
sudo raspi-config
```

Test password by manual logging in
```
ssh pi@<host>
```
Access the pi with a ssh key:
```
cd ~/.ssh
ssh-keygen
```
- Enter < filename > of keyfile
```
ssh-copy-id -i < filename > user@host
```
- Test:
```
ssh -i < filename > user@host
```
- Add passphrase to keychain:
```
ssh-add -K < filename >
```
- Login
```
ssh -i < filename > pi@< host >
```