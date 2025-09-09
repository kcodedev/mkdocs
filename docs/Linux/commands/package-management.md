# Package Management

## apt (Debian/Ubuntu)

Update package list.

- `sudo apt update` : Update package list

Install package.

- `sudo apt install package` : Install package

Remove package.

- `sudo apt remove package` : Remove package
- `sudo apt purge package` : Remove package and config

Search for package.

- `apt search package` : Search packages

Show package info.

- `apt show package` : Package information

Upgrade system.

- `sudo apt upgrade` : Upgrade packages
- `sudo apt dist-upgrade` : Distribution upgrade

## yum/dnf (Red Hat/CentOS/Fedora)

Install package.

- `sudo yum install package` : Install (yum)
- `sudo dnf install package` : Install (dnf)

Remove package.

- `sudo yum remove package` : Remove (yum)
- `sudo dnf remove package` : Remove (dnf)

Update system.

- `sudo yum update` : Update (yum)
- `sudo dnf update` : Update (dnf)

Search package.

- `yum search package` : Search (yum)
- `dnf search package` : Search (dnf)

## pacman (Arch Linux)

Synchronize package databases.

- `sudo pacman -Sy` : Sync

Install package.

- `sudo pacman -S package` : Install

Remove package.

- `sudo pacman -R package` : Remove

Update system.

- `sudo pacman -Syu` : Sync and upgrade

## snap (Universal)

Install snap package.

- `sudo snap install package` : Install

Remove snap package.

- `sudo snap remove package` : Remove

List installed snaps.

- `snap list` : List snaps

## flatpak (Universal)

Install flatpak.

- `flatpak install flathub org.example.App` : Install

Run flatpak app.

- `flatpak run org.example.App` : Run

List installed flatpaks.

- `flatpak list` : List