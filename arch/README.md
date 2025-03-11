# my Arch Linux setup

## 1. base setup
```bash
# (arch server install)
curl -fsSL https://christitus.com/linux | sh

# REBOOT

sudo localectl set-keymap be-latin1 azerty
```

## 2. SSH *(optional)*

```
sudo pacman -S openssh
sudo systemctl start sshd
sudo systemctl enable sshd
```

## 3. terminal setup (nerd-fonts, fastfetch, starship)


### nerd-fonts

```
sudo pacman -S nerd-fonts
```

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

## 4. DWM (alacritty, DWM, DMenu)

### alacritty

```bash
sudo pacman -S alacritty
```


<details>
  <summary>  
  
### optionA: DWM: my-dwm repo
  
  </summary>

```bash
cd ~
git clone [https://git.suckless.org/dwm](https://github.com/teacher-svb/my-dwm.git)
cd my-dwm
```

</details>

<details>
  <summary>  
  
### option B: DWM: Build and Patch from scratch  
  
  </summary>

### build DWM

#### prerequisites (TODO: are they all needed?)
```bash
sudo pacman -S --needed --noconfirm xorg-xinit xorg-server base-devel libx11 libxinerama libxft git unzip lxappearance curl nano libxcb meson libev uthash libconfig xcb-util
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

Generate and open `config.h`.
```
cd ~/dwm
sudo make clean install
sudo nano config.h
```

change termcmd to use alacritty:
```bash
static const char *termcmd[] = { "alacritty", NULL };
```

change MODKEY to use the Meta key (Mod4Mask) and add ALTKEY to use the Alt key (Mod1Mask)
```bash
/* key definitions */
#define MODKEY Mod4Mask
#define ALTKEY Mod1Mask
```
- change terminal shortcut to use:
```bash
ALTKEY|ControlMask, XK_t, ...
```

</details>

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

first test with:
```bash
startx
```

if everything works fine, add the following to `~/.bashrc`

```bash
# Auto-start DWM if we're on TTY1 and .xinitrc contains "exec dwm"
if [[ "$(tty)" == "/dev/tty1" ]] && [ -f "$HOME/.xinitrc" ] && grep -q "^exec dwm" "$HOME/.xinitrc"; then
    startx
fi
```

---
# Additional Setup

## A. Additional Package Managers

### YAY AUR Helper

CTT Linux tool, go to `Arch > Yay AUR Helper`

```bash
curl -fsSL https://christitus.com/linux | sh
```

### Flatpak / Flathub

CTT Linux tool, go to `Applications Setup > Flatpak / Flathub`

```bash
curl -fsSL https://christitus.com/linux | sh
```

### Snap

```
yay -S snapd
systemctl enable snapd
```

reboot

```
sudo ln -s /var/lib/snapd/snap /snap
```

## B. Additional Software

### vs code (as snap)

`sudo snap install code --classic`


### Browser (Brave)

```bash
curl -fsS https://dl.brave.com/install.sh | sh
```

### Docker

CTT Linux tool, go to `Applications Setup > Docker`

```bash
curl -fsSL https://christitus.com/linux | sh
```

## C. Additional Configuration

### Alacritty

create config file
```
mkdir -p ~/.config/alacritty
cd ~/.config/alacritty
touch alacritty.toml
```

open alacritty.toml file and add the following config:

```
[font]
normal.family="FiraCode Nerd Font"
```

### Bash

### Starship



### DWM

```
sudo pacman -S wireplumber bc
```

#### DWM blocks async

```
git clone https://github.com/UtkarshVerma/dwmblocks-async.git
cd dwmblocks-async
sudo nano config.h
sudo make install
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

### screen resolution (CLI)

```
sudo pacman -S xorg-xrandr arandr autorandr
```

open `arandr`, change resolution/position

call `autorandr --save <profilename>` (to set a specific profile as default, also call `autorandr --default <profilename>`)
