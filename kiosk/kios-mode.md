# Kiosk mode
```
sudo apt-get update
sudo apt-get upgrade -y
```

set option to auto login into the console of raspberry pi
```
sudo raspi-config
```

## openbox
```
sudo apt-get install --no-install-recommends xserver-xorg x11-xserver-utils xinit openbox
```

## chromium
```
sudo apt-get install --no-install-recommends chromium-browser
```

## openbox config
```
sudo nano /etc/xdg/openbox/autostart
```

```
xset -dpms			# turn off display power management system
xset s noblank		# turn off screen blanking
xset s off			# turn off screen saver

#Remove exit errors from the config files that could trigger a warning

sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'

sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Preferences
# if the host name is changed take care of existing profile locks
rm -rf ~/.config/google-chrome/Singleton*


# Run Chromium in kiosk mode
chromium-browser  --noerrdialogs --disable-infobars --kiosk $KIOSK_URL --check-for-update-interval=31536000
```

## openbox environment
```
sudo nano /etc/xdg/openbox/environment
```
```
export KIOSK_URL=https://tikkie.me
```

## edit bash_profile
- test if `~/.bash_profile` exists
- edit profile
```
ls -la ~/.bash_profile
touch ~/.bash_profile
sudo nano ~/.bash_profile
```
```
[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && startx -- -nocursor
```
- test bash_profile
```
source ~/.bash_profile
```
- if there are no errors reboot
```
sudo reboot
```

