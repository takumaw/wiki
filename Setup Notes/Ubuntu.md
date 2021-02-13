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

### Essentials

```bash
sudo apt install -y \
  byobu \
  coreutils \
  dialog \
  htop \
  p7zip \
  pv \
  rsync \
  telnet \
  tmux \
  w3m \
  wget
```

```bash
sudo apt install -y \
  aria2 \
  fdupes \
  pstree \
  rename \
  renameutils
```

### Source Code Management

 * https://git-scm.com/download/linux

```bash
sudo add-apt-repository -y --update ppa:git-core/ppa
sudo apt install git
```

```bash
sudo apt install -y \
  subversion
```

### VMs & Containers

 * https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
 
```bash
sudo apt-add-repository -y --update ppa:ansible/ansible
sudo apt install ansible
```

### Documents & Visualization

```bash
sudo apt install -y \
  asciidoc \
  colordiff \
  docbook \
  dos2unix \
  doxygen \
  help2man \
  lv \
  nkf \
  pandoc \
  qpdf \
  recode \
  sphinx-doc
```

```bash
sudo apt install -y \
  graphicsmagick \
  graphviz \
  imagemagick
```

### Networking

```bash
sudo apt install -y \
  corkscrew \
  iperf \
  nmap \
  socat
```

### Databases

 * https://www.postgresql.org/download/linux/ubuntu/
 * https://dev.mysql.com/downloads/repo/apt/
 
```bash
sudo apt install -y \
  sqlite
```

### Build Tools

```bash
sudo apt install -y \
  autoconf \
  autogen \
  automake \
  cmake \
  libtool
```

### Haskell-specific

```bash
sudo apt install -y \
  cabal-install \
  ghc \
  haskell-platform \
  haskell-stack
```

### Python-specific

```bash
sudo apt install -y \
  python3 \
  pypy3
```

```bash
sudo apt install -y \
  python3-pip \
  python3-venv \
  jupyter \
  jupyter-notebook \
  jupyter-nbconvert \
  python3-numpy \
  python3-scipy \
  python3-matplotlib \
  python3-pandas \
  python3-requests
```

### Java-specific

```bash
sudo apt install -y \
  ant \
  gradle \
  maven
```

### Node-specific

https://nodejs.org/ja/download/package-manager/

### Web Development

```bash
sudo apt install -y \
  jq \
  mitmproxy
```

### Project Management

```bash
sudo apt install -y \
  cloc \
  sloccount
```

### TeX Live

```bash
sudo apt install -y \
  texlive \
  texlive-lang-cjk \
  texlive-fonts-recommended \
  texlive-fonts-extra \
  xdvik-ja
```
