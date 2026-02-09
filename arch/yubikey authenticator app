```bash
sudo pacman -S pcsclite ccid pcsc-tools yubikey-personalization
sudo systemctl enable --now pcscd

sudo udevadm control --reload-rules
sudo udevadm trigger
sudo systemctl restart pcscd

flatpak override --user --filesystem=/run/pcscd --device=all com.yubico.yubioath
flatpak run com.yubico.yubioath
```
