# Fedora 36 setup

Remove garbage

``` Bash
sudo dnf remove gnome-connections gnome-boxes gnome-contacts gnome-logs gnome-maps gnome-abrt gnome-tour
```

Speed up DNF

``` Bash
echo 'fastestmirror=true' | sudo tee -a /etc/dnf/dnf.conf
echo 'max_parallel_downloads=20' | sudo tee -a /etc/dnf/dnf.conf
echo 'deltarpm=True' | sudo tee -a /etc/dnf/dnf.conf
echo 'defaultyes=True' | sudo tee -a /etc/dnf/dnf.conf
```

System update

``` Bash
sudo dnf update --refresh -y& sudo dnf upgrade --refresh -y
sudo dnf update -y & sudo dnf upgrade -y
```

Install useful tools

``` Bash
sudo dnf install obs-studio gnome-extensions-app tlp tlp-rdw vlc bleachbit gnome-tweaks okular -y
```

Enable TLP

``` Bash
sudo systemctl enable tlp
```

Telegram

``` Bash
wget https://telegram.org/dl/desktop/linux
tar -xvf tsetup.*.*.*.tar.xz
sudo mv Telegram/ /opt
/opt/Telegram/./Telegram
```

Import RPM Fusion Free and NonFree

``` Bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm -y
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm -y
sudo dnf upgrade --refresh
sudo dnf groupupdate core
sudo dnf install -y rpmfusion-free-release-tainted
sudo dnf install -y dnf-plugins-core
```

NVIDIA Drivers

``` Bash
sudo dnf install akmod-nvidia -y
sudo dnf install xorg-x11-drv-nvidia-cuda -y
nvidia-settings
```

Preload

``` Bash
sudo dnf copr enable elxreno/preload -y && sudo dnf install preload -y
```

Better Fonts

``` Bash
sudo dnf copr enable dawid/better_fonts -y
sudo dnf install fontconfig-font-replacements -y
sudo dnf install fontconfig-enhanced-defaults -y
```

Multimedia Plugins

``` Bash
sudo dnf install gstreamer1-plugins-base gstreamer1-plugins-good gstreamer1-plugins-ugly gstreamer1-plugins-bad-free gstreamer1-plugins-bad-free gstreamer1-plugins-bad-freeworld gstreamer1-plugins-bad-free-extras ffmpeg
```

Multimedia Codecs

``` Bash
sudo dnf groupupdate sound-and-video
sudo dnf install -y libdvdcss
sudo dnf install -y gstreamer1-plugins-{bad-\*,good-\*,ugly-\*,base} gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel ffmpeg gstreamer-ffmpeg 
sudo dnf install -y lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
```

Archive formats

``` Bash
sudo dnf install p7zip p7zip-plugins unrar
```

Microsoft Fonts

``` Bash
sudo dnf install -y curl cabextract xorg-x11-font-utils fontconfig
sudo rpm -i https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
```

VS Code

``` Bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
dnf check-update
sudo dnf install code
```

Brackets

``` Bash
flatpak install flathub io.brackets.Brackets
flatpak run io.brackets.Brackets
```

Python

``` Bash
sudo dnf install pycharm-community python-devel python3-pip
python3 -m pip install python-dev-tools --upgrade
```

Flatpak

``` Bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak update
```

Change Flatpak permissions

``` Bash
flatpak install -y flatseal
```

Spotify

``` Bash
sudo flatpak install spotify
```

Snap

``` Bash
sudo dnf install -y snapd
sudo ln -s /var/lib/snapd/snap /snap # for classic snap support
sudo reboot now
sudo snap refresh
```
