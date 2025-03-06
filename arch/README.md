# my Arch Linux setup

```bash
# (arch server install)
curl -fsSL https://christitus.com/linux | sh

sudo localectl set-keymap be-latin1 azerty

# (arch install: yay AUR helper)
# (terminal install: alacritty, fastfetch, bash)
curl -fsSL https://christitus.com/linux | sh

sudo pacman -S --needed --noconfirm xorg-xinit xorg-server base-devel libx11 libxinerama libxft git unzip lxappearance curl nano libxcb meson libev uthash libconfig

git clone https://git.suckless.org/dwm

cd dwm
# apply patches:
# - cool autostart (patch fail can be ignored)
# - statuscmd (manually fix patch after applying)
# then
sudo make clean install

cd ~ && touch .xinitrc # add exec dwm

# start x-server and will initialize system using .xinitrc, which starts DWM
startx

# (yay AUR Helper & Virtualization)
curl -fsSL https://christitus.com/linux | sh

# (software install: browser, docker)
curl -fsSL https://christitus.com/linux | sh
```



```
sudo pacman -S wireplumber bc
```


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
