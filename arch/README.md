# my Arch Linux setup

## basic server setup

open linutil from christitus:

```
curl -fsSL https://christitus.com/linux | sh
```

select `System Setup > Arch Linux > Arch Server Setup`

reboot

## Add AUR

open linutil from christitus:

```
curl -fsSL https://christitus.com/linux | sh
```

select `System Setup > Arch Linux > Yay AUR helper`

## Install DWM

## Install Snapd

```
yay -S snapd
systemctl enable snapd
```

reboot

```
sudo ln -s /var/lib/snapd/snap /snap
```

reboot

## Install base software

### through Linutil

### terminal

### bash

### browser

### through CLI

```
sudo pacman -S nano xorg-xrandr arandr
```

### screen resolution

```
sudo pacman -S xorg-xrandr arandr
```

### nano

```
sudo pacman -S nano
```

### vs code (as snap)

`sudo snap install code --classic`

## Settings

### fix keyboard layout for BE keyboard

```
sudo localectl set-keymap be-latin1 azerty
```

reboot
