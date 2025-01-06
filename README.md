# ok_nabu

## préparer rasp pi

sudo apt update
sudo apt upgrade

## wm8960

https://www.waveshare.com/wiki/WM8960_Audio_HAT
```code bash
git clone https://github.com/waveshare/WM8960-Audio-HAT
```
```code bash
cd WM8960-Audio-HAT
sudo ./install.sh 
```
```code bash
sudo reboot
```
```code bash
sudo dkms status
```
tester les commandes arecord et aplay pour noter les paramètres corrects
arecord -D hw:0,0 -f S16_LE -r 16000 -c 2 test.wav
aplay -Dhw:0 test.wav

## wyoming satellites
https://github.com/rhasspy/wyoming-satellite
https://github.com/rhasspy/wyoming-satellite/blob/master/docs/tutorial_2mic.md
https://github.com/rhasspy/wyoming-openwakeword/

```code bash
sudo apt-get update
sudo apt-get install --no-install-recommends  \
  git \
  python3-venv
```

```code bash
git clone https://github.com/rhasspy/wyoming-satellite.git
```

pour système 64bits

```code bash

cd wyoming-satellite/
python3 -m venv .venv
.venv/bin/pip3 install --upgrade pip
.venv/bin/pip3 install --upgrade wheel setuptools
.venv/bin/pip3 install \
  -f 'https://synesthesiam.github.io/prebuilt-apps/' \
  -r requirements.txt \
  -r requirements_audio_enhancement.txt \
  -r requirements_vad.txt
```
pour système 32bits
```code bash

cd wyoming-satellite/
python3 -m venv .venv
.venv/bin/pip3 install --upgrade pip
.venv/bin/pip3 install --upgrade wheel setuptools
.venv/bin/pip3 install \
  -f 'https://synesthesiam.github.io/prebuilt-apps/' \
  -r requirements.txt \
  -r requirements_audio_enhancement.txt \
```
script/run  \
--name 'nabu' \
--uri 'tcp://0.0.0.0:10700'  \
--mic-command 'arecord -D hw:0,0 -r 16000 -c 2 -f S16_LE -t raw'  \
--snd-command 'aplay -Dhw:0 -r 22050 -c 1 -f S16_LE -t raw' \
--wake-uri 'tcp://192.168.1.9:10400' \
--wake-word-name 'ok_nabu' \
--debug


script/run \
  --debug \
  --name 'Nabu Salon' \
  --uri 'tcp://0.0.0.0:10700' \
  --mic-command 'arecord -r 16000 -c 1 -f S16_LE -t raw' \
  --snd-command 'aplay -r 22050 -c 1 -f S16_LE -t raw'

## wyoming satellites enhanced


https://github.com/FutureProofHomes/wyoming-enhancements/blob/master/snapcast/docs/4_modify_wyoming_satellite.md
