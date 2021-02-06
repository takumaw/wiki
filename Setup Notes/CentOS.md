CentOS Setup Note
========================================================================

Initial Setup
------------------------------------------------------------------------

 * Language & Keyboard
   * Japanese
 * Software
   * GNOME Desktop / Development and Creativity Workstation
 * Destination
   * Local drive with encryption
 * Networking
   * Enable
 * Security Policy

Initial Setup
------------------------------------------------------------------------

### Software Repository

```bash
vi /etc/yum/pluginconf.d/fastestmirror.conf
```

```
include_only=.jp
```

```bash
yum install -y epel-release yum-utils
```

### Essentials

```bash
apt install -y zsh byobu tmux htop vim
```

### Automatic Update

```bash
yum install -y yum-cron
```

```bash
vim /etc/yum/yum-cron.conf
```

```
apply_updates = yes
```

```bash
systemctl enable yum-cron
systemctl restart yum-cron
```

### Time Syncing

```bash
yum install -y chrony
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

Place certs under `/etc/pki/ca-trust/source/anchors/`.

Then,

```
update-ca-trust extract
```

### Network Filesystems

```bash
yum install -y cifs-utils nfs-utils
```

### Optional: Cockpit

```bash
yum install -y cockpit
```

### Optional: Basic Securities

```bash
yum install -y logwatch fail2ban
```

### Optional: Update Folder Names

```bash
LANG=C xdg-user-dirs-gtk-update
```

### Development Tools

```bash
yum groups install -y "Development Tools"
```

```bash
yum install -y \
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
sudo yum update -y; sudo yum autoremove -y
```

```bash
sudo reboot
```
