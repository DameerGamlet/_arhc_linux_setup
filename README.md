# Установка и настройка моего Arch Linux откружения

## Цель

Получить удобную установку и настройку Arch Linux приложения с минимальными усилиями.

## Установка

TODO: написать процесс установки с использованием archinstall (от добавление WIFI, до запуска дистрибутива).

## Действия после установки Arch Linux

Настройка интернета:

```shell
sudo systemctl enable --now NetworkManager
```

Это основные опции, которые будут применяться в этой инструкции.

Установка топ первых необходимых инстументов:

TODO: расширить

```shell
sudo pacman -R gnome-maps gnome-weather gnome-tour gnome-connections
```
```shell
sudo pacman -Syu;
```
```shell
sudo pacman -S git neovim ranger tilix tldr gparted bat zsh ark htop cpupower curl dconf dconf-editor eza fastfetch fd ffmpeg firefox flameshot java-runtime-common lazygit obsidian yazi steam syncthing telegram-desktop tldr vim virtualbox vlc fzf obs-studio
```

Настройка git:

TODO: добавить описание от создания  токена до активного использования

```shell
todo
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
paru -S auto-cpufreq cpupower-gui jetbrains-toolbox lazydocker microsoft-edge-stable-bin ocs-url postman-bin stacer sysz ttf-ms-fonts visual-studio-code-bin webcord yandex-browser
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

$ mkdir ~/Repos; cd ~/Repos; git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si

## ! Настройки системы !
		
### Настройка монтирования к HDD

```shell
sudo pacman -S ntfs-3g % мне это было достаточно
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

##### ExtensionManager
Установить:
    - Dash to Dock 
    - AppIndication and KStatusNotifierItem Support
    - Clickboard Indicator
    - Vitals
    - Lock Keys
    
Включить:
    - Applications Menu
    - User Themes
    - Native Window Placement
    
### ! Tweaks !
    - Appearance:
        Курсор: 
        Иконки: 
        Shell: 
        Legacy Applications: 
        
    - Windows:
        Titlebar Buttons:
            Minimize: true
            Senter New Windows: true
## ! Настройка нормального шрифта !
$ mkdir ~/.fonts
Шрифты имеются в HDD

Потом надо указать в терминале шрифт

## ! ZSH !
Установка была ранее

#### Выбрать ZSH как систему по умолчанию:
$ chsh -s $(which zsh)

Дальше перезагрузка и настройка zsh

#### Установка oh my zsh
$ cd ~/Repos
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

#### Установка темы powerlevel10k
$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

#### Настройка powerlevel10k
Добавить в .zshrc

```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Использовать иные настройки из HDD

Будет много конфликтор:

### 1) использовать exa
$ sudo pacman -S exa

### 2) Скачать плагины
[oh-my-zsh] plugin 'zsh-autocomplete' not found
$ cd ~/Repos
$ git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
```
# добавить в .zshrc
source ~/Repos/zsh-autocomplete/zsh-autocomplete.plugin.zsh
```

[oh-my-zsh] plugin 'zsh-autosuggestions' not found
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
[oh-my-zsh] plugin 'zsh-syntax-highlighting' not found
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

## ! NvChad !

$ git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim

## ! Docker !
$ sudo pacman -S docker docker-compose
$ sudo systemctl enable --now docker
$ sudo groupadd docker; sudo usermod -aG docker $USER; newgrp docker

# ! VirtualBox !
$ sudo pacman -S virtualbox
1) virtualbox-host-dkms 2) virtualbox-host-modules-arch
Выбрать 2






















