# Установка и настройка моего Arch Linux откружения

## Цель

Получить удобную установку и настройку Arch Linux приложения с минимальными усилиями.

## Установка

1. скачать дистрибутив, добавить установочную флешку:

`sudo dd if=./archlinux-2023.06.01-x86_64.iso of=/dev/sdb conv=fsync oflag=direct status=progress`

Настроить вай фай:

```shell
iwctl
[iwd]# station wlan0 get-networks
[iwd]# station wlan0 connect <Name of WiFi access point>
[iwd]# exit
ping 1.1.1.1
```

## Действия после установки Arch Linux

Настройка интернета:

```shell
sudo pacman -Syyu;
sudo pacman -S networkmanager;
sudo systemctl enable --now NetworkManager;
```

Это основные опции, которые будут применяться в этой инструкции.

### Установка топ первых необходимых инстументов:

Обновить:

```shell
sudo pacman -Syu;
```

Базовые приложения к удалению:

```shell
sudo pacman -R gnome-maps gnome-weather gnome-tour gnome-connections gnome-software gnome-contacts gnome-music
```

Базовые приложения к установке во время установки: 

```shell
sudo pacman -S git tilix firefox vim
```

Базовые приложения к установке после установки: 

```shell
sudo pacman -S neovim ranger tldr gparted bat zsh ark cpupower dconf-editor fastfetch fd flameshot java-runtime-common lazygit obsidian yazi steam syncthing telegram-desktop tldr virtualbox vlc fzf obs-studio exa shotwell libreoffice-still libreoffice-still-ru
```


Установить paru:

```shell
mkdir ~/repos;
cd ~/repos;
git clone https://aur.archlinux.org/paru.git;
cd paru;
makepkg -si;
```

Нужные пакеты:

```shell
paru -Syu;
paru -S auto-cpufreq \
    cpupower-gui \
    jetbrains-toolbox \
    lazydocker \
    microsoft-edge-stable-bin \
    ocs-url \
    postman-bin \
    stacer \
    sysz \
    ttf-ms-fonts \
    visual-studio-code-bin \
    webcord \
    yandex-browser \
    extension-manager
```

### zsh как систему по умолчанию:

```shell
chsh -s $(which zsh)
```
ohmyzsh:

```shell
cd ~/repos;
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)";
```

powerlevel10k:

```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k;
```
(настройка `p10k configure`)

Решение конфликтов:

```shell
cd ~/repos;
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete;
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions;
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting;
```

Настройка git:

TODO: добавить описание от создания  токена до активного использования

```shell
todo
```

### Добавить раскладку клавиатуры

```shell
gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Alt>Shift_L']";
gsettings set org.gnome.desktop.wm.keybindings switch-input-source-backward "['<Shift>Alt_L']";
gsettings set org.gnome.desktop.peripherals.touchpad send-events disabled-on-external-mouse;
```

### Настройка Pacman
$ sudo nvim /etc/pacman.conf

В конфигурационном файле раскоментировать:
```
# раскоментировать
Color
ParallelDownloads=5
# добавить
ILoveCandypacman -S ntfs-3g
```

#### Yay
Репо: https://github.com/Jguer/yay

```shell
mkdir ~/Repos;
cd ~/Repos; 
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

## ! Настройки системы !
		
### Настройка монтирования к HDD

```shell
sudo pacman -S ntfs-3g
```

### SDKMAN

```shell
curl -s "https://get.sdkman.io" | bash
```

TODO: установить java. gradle

## Расширения

- AppIndicator and KStatusNotifierItem Support
- Color Piker (disable)
- Custom Hot Corners - Extended
- Dash to Dock
- Disable unredirect fullscreen windows
- Grand Theft Focus
- Lock Keys
- Pano - Clipboard Manager
- Quick Lang Switch
- Vitals
- Windows Gestures
- WTMB (Windows Thumbnails)

## Tweaks
    - Windows:
        Titlebar Buttons:
            Minimize: true
            Senter New Windows: true
    
## ! Настройка нормального шрифта !
$ mkdir ~/.fonts
Шрифты имеются в HDD

Потом надо указать в терминале шрифт

## ! NvChad !

```shell
git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim
```

## ! Docker !

```shell
sudo pacman -S docker docker-compose;
sudo systemctl enable --now docker;
sudo groupadd docker; 
sudo usermod -aG docker $USER;
newgrp docker
```

# ! VirtualBox !
$ sudo pacman -S virtualbox
1) virtualbox-host-dkms 2) virtualbox-host-modules-arch
Выбрать 2


