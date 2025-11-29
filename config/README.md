copy [`.bashrc`](./.bashrc) to `~/.bashrc`

copy [`starship.toml`](./starship.toml) to `~/.config/starship.toml`

copy [`fastfetch.jsonc`](./fastfetch.jsonc) to `~/.config/fastfetch/config.jsonc`


```bash
mkdir -p ~/.config/fastfetch
mv ./.bashrc ~/.bashrc
mv ./starship.toml ~/.config/starship.toml
mv ./.fastfetch.jsonc ~/.config/fastfetch/config.jsonc
```