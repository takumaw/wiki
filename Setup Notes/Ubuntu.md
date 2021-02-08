Ubuntu Setup Note
========================================================================

Initial Setup
------------------------------------------------------------------------

 * Language & Keyboard
   * Japanese
 * Updates and other software
   * Minimal Installation
   * Other options
     * NOT retrieve updates
     * Install third-party software
 * Destination
   * Local drive with encryption

Initial Setup
------------------------------------------------------------------------

### Software Repository

```bash
vi /etc/apt/sources.list
```

```
:%s/jp.archive.ubuntu.com/REPOSITORY_HOST\/Linux/g
```

### Essentials

```bash
apt install -y zsh byobu tmux htop vim
```


Update & Restart

### Automatic Update

```bash
apt install -y unattended-upgrades
dpkg-reconfigure -plow unattended-upgrades
```

```bash
vim /etc/apt/apt.conf.d/50unattended-upgrades
```

```
// Unattended-Upgrade::Allowed-Origins をアンコメント
Unattended-Upgrade::Remove-Unused-Dependencies "true";
Unattended-Upgrade::Automatic-Reboot "true";
```

### Time Syncing

```bash
apt install -y chrony
```

```bash
vim /etc/chrony/chrony.conf
# => modify ntp server(s)
```

```bash
systemctl enable chronyd
systemctl restart chronyd
chronyc -a makestep
```

### Root CA Certificates

Place certs under `/usr/local/share/ca-certificates/`.

Then,

```
update-ca-certificates -v
```

### Network Filesystems

```bash
apt install -y cifs-utils nfs-common
```

### Optional: Cockpit

```bash
apt install -y cockpit
```

### Optional: Basic Securities

```bash
apt install -y logwatch fail2ban
```

### Optional: Update Folder Names

```bash
LANG=C xdg-user-dirs-gtk-update
```

### Development Tools

```bash
apt install -y build-essential
```

```bash
apt install -y \
 coreutils \
 netcat \
 p7zip \
 rsync \
 telnet \
 w3m \
 wget
```

Update & Restart
------------------------------------------------------------------------

```bash
sudo apt update; sudo apt upgrade -y; sudo apt autoremove -y; sudo apt autoclean
```

```bash
sudo reboot
```

Console Applications
------------------------------------------------------------------------

### Source Code Management

 * https://git-scm.com/download/linux

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt install git
```

### Python-specific

```bash
sudo apt install \
  python3 \
  python3-pip \
  python3-venv \
  python3-jupyter \
  python3-nbconvert \
  python3-numpy \
  python3-scipy \
  python3-matplotlib \
  python3-pandas \
  python3-requests
```
### Node-specific

https://nodejs.org/ja/download/package-manager/

### TeX Live

```bash
sudo apt install -y \
  texlive \
  texlive-lang-cjktexlive-lang-cjk \
  texlive-fonts-recommended \
  texlive-fonts-extra \
  xdvik-ja
```
