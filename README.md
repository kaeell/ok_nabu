# ok_nabu

## préparer rasp pi


## wm8960

https://www.waveshare.com/wiki/WM8960_Audio_HAT

tester les commandes arecord et aplay pour noter les paramètres corrects
arecord -D hw:1,0 -f S16_LE -r 16000 -c 2 test.wav
aplay -Dhw:1 test.wav

## wyoming satellites
https://github.com/rhasspy/wyoming-satellite
https://github.com/rhasspy/wyoming-satellite/blob/master/docs/tutorial_2mic.md
https://github.com/rhasspy/wyoming-openwakeword/


script/run  \
--name 'my satellite' \
--uri 'tcp://0.0.0.0:10700'  \
--mic-command 'arecord -D hw:1,0 -r 16000 -c 1 -f S16_LE -t raw'  \
--snd-command 'aplay -Dhw:1 -r 22050 -c 1 -f S16_LE -t raw' \
--wake-uri 'tcp://127.0.0.1:10400' \
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
