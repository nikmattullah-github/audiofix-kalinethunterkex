# audiofix-kalinethunterkex
Fix Audio Stream Port vnc/nethunter kex

#Step1 open terminal kaliLinux Tambahkan code ini pada file xstartup
nano.vnc/xstartup

#!/bin/bash
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADRESS
export PULSE_SERVER=127.0.0.1
exec startxfce4

#Step2 open termux install pulseaudio, wget, wget http raw sound_setup
pkg install pulseaudio -y
pkg install wget
wget https://raw.githubusercontent.com/anonymous770/audio-fixed-os/main/sound_setup.sh
chmod +x sound_setup.sh
bash ./sound_setup.sh

#Step3 jalankan command ditermux
pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1

#Step4 jalankan command di kaliLinux nethunter
pulseaudio --start
export PULSE_SERVER=127.0.0.1 && pulseaudio --start --disable-shm=1 --exit-idle-time=-1
crontab -e
# Pilih 1. /bin/nano masukan perintah "@reboot pulseaudio --start" tanpa "

#logout kalilinux nethunter
#logout termux

#Start kembali. 
