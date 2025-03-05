# my Arch Linux setup

```bash
# (arch server install)
curl -fsSL https://christitus.com/linux | sh

sudo localectl set-keymap be-latin1 azerty

sudo pacman -S --needed --noconfirm xorg-xinit xorg-server base-devel libx11 libxinerama libxft git unzip lxappearance curl nano
sudo pacman -S --needed --noconfirm libxcb meson libev uthash libconfig

git clone https://git.suckless.org/dwm

cd dwm

sudo make clean install

cd ~ && touch .xinitrc # add exec dwm

startx # starts x-server and will initialize system with .xinitrc, which starts DWM

# (yay AUR Helper & Virtualization)
curl -fsSL https://christitus.com/linux | sh

# (software install: browser, docker, alacritty, fastfetch)
curl -fsSL https://christitus.com/linux | sh
```



```
sudo pacman -S wireplumber bc
```

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
sudo pacman -S xorg-xrandr arandr autorandr
```

open `arandr`, change resolution/position

call `autorandr --save <profilename>` (to set a specific profile as default, also call `autorandr --default <profilename>`)

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
