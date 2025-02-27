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

### Install DWM (with Linutil)

#### adding ALT as modkey

```
/* key definitions */
#define MODKEY Mod4Mask
#define ALTKEY Mod1Mask
```

#### change terminal to alacritty

```
static const char *termcmd[] = { "alacritty", NULL };
```

#### fix for BE Azerty shortcuts:

```
static Key keys[] = {
    ...
    TAGKEYS(                        XK_ampersand,              0)
    TAGKEYS(                        XK_eacute,                 1)
    TAGKEYS(                        XK_quotedbl,               2)
    TAGKEYS(                        XK_apostrophe,             3)
    TAGKEYS(                        XK_parenleft,              4)
```

```
sudo make clean install
```

### terminal

### bash

### browser

### screen resolution (CLI)

```
sudo pacman -S xorg-xrandr arandr
```

open `arandr`, change resolution/position and save file to ~/.screenlayout

open `~/.xinitrc` and add `sh ~/.screenlayout/<filename>.sh &` (replace with your filename)

### nano (CLI)

```
sudo pacman -S nano
```

#### vs code (as snap)

`sudo snap install code --classic`

## Settings

### fix keyboard layout for BE keyboard

```
sudo localectl set-keymap be-latin1 azerty
```

reboot
