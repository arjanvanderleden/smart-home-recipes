# Install Home assistant

```
update apt-get
sudo apt-get update
sudo apt-get upgrade -y
```

## dependencies

```
sudo apt-get install -y python3 python3-dev python3-venv python3-pip libffi-dev libssl-dev libjpeg-dev zlib1g-dev autoconf build-essential libopenjp2-7 libtiff5 tzdata
```

## Python environment

- Add user for home assistant

```
sudo useradd -rm homeassistant -G dialout,gpio,i2c
```

- Make folder

```
sudo mkdir /srv/homeassistant
sudo chown homeassistant:homeassistant /srv/homeassistant
```

- Create virtual environment

```
sudo -u homeassistant -H -s
cd /srv/homeassistant
python3 -m venv .
source bin/activate
```

- Install wheel (python)

```
python3 -m pip install wheel
```

- Install home assistant

```
pip3 install homeassistant
```

## Finish

- Start home assistant (will take 10+ minutes)

```
hass
```
