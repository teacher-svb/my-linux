# my Arch Linux setup

## base setup
```bash
# (arch server install)
curl -fsSL https://christitus.com/linux | sh

# REBOOT

sudo localectl set-keymap be-latin1 azerty
```

## terminal setup (fastfetch, starship)

### FastFetch

```bash
sudo pacman -S fastfetch
```
add the following to `~/.bashrc`
```bash
fastfetch
```

### Starship

```bash
curl -sS https://starship.rs/install.sh | sh
```
add the following to `~/.bashrc`

```bash
eval "$(starship init bash)"
```

## DWM (alacritty, DWM, DMenu)

### alacritty

```bash
sudo pacman -S alacritty
```

### build DWM

#### prerequisites (TODO: are they all needed?)
```bash
sudo pacman -S --needed --noconfirm xorg-xinit xorg-server base-devel libx11 libxinerama libxft git unzip lxappearance curl nano libxcb meson libev uthash libconfig
```

#### Download DWM

```bash
git clone https://git.suckless.org/dwm
cd dwm
```

#### patch DWM

```bash
# cool autostart
curl -O https://dwm.suckless.org/patches/cool_autostart/dwm-cool-autostart-6.2.diff
# ignore patch errors
patch < dwm-cool-autostart-6.2.diff

# statuscmd
curl -O https://dwm.suckless.org/patches/statuscmd/dwm-statuscmd-20210405-67d76bd.diff
# TODO: manual fix needed after applying patch
patch < dwm-statuscmd-20210405-67d76bd.diff
```

#### base configuration DWM

open `config.h` in `dwm` folder.

Create the autostart variable:
static const char *const autostart[] = {
	NULL
};

- change termcmd to use alacritty
- change MODKEY to use the Meta key (Mod4Key)
- add ALTKEY definition to use the Alt key (Mod1Key)
- change terminal startup to use:
  - `ALTKEY|ControlMask, XK_t, ...`

#### build DWM

```bash
sudo make clean install
```
then create `.xinitrc` file, and add DWM startup to file
```bash
cd ~ && touch .xinitrc
```
add the following to `~/.xinitrc`

```bash
exec dwm
```

### DMenu

inside the `dwm` folder:
```bash
git clone https://git.suckless.org/dmenu
cd dmenu
sudo make clean install
```

### start DWM

```bash
startx
```

---

```

# (yay AUR Helper & Virtualization)
curl -fsSL https://christitus.com/linux | sh

# (software install: browser, docker)
curl -fsSL https://christitus.com/linux | sh

# install snapd
yay -S snapd
systemctl enable snapd

# reboot

sudo ln -s /var/lib/snapd/snap /snap

# reboot
```

```
sudo pacman -S wireplumber bc
```

```
# (arch install: yay AUR helper)
# (terminal install: alacritty, fastfetch, bash)
curl -fsSL https://christitus.com/linux | sh
```


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
