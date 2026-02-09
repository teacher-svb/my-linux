# my Arch Linux setup

## 1. base setup

use the archinstall script to launch the installer.
```bash
archinstall
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

# Additional Setup

## A. Additional Package Managers

### YAY AUR Helper

CTT Linux tool, go to `Arch > Yay AUR Helper`

```bash
curl -fsSL https://christitus.com/linux | sh
```

### Flatpak / Flathub

```bash
sudo pacman -S flatpak
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

### Bash

add the following to `/etc/inputrc`:

```
set completion-ignore-case on
```

