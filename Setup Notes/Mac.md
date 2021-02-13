Mac Setup Note
========================================================================

Initial Setup
------------------------------------------------------------------------

### System Preferences

 * Setup FileVault2
 * Setup Networks (Wi-Fis, VPNs, ...)
 * Setup Printers
 * Install Applications
 * Restore Home Directory (`~/Library`, ...)

Graphical Applications
------------------------------------------------------------------------

### Web & Email

 * Google Chrome
 * GPGTools
 * Mozilla Firefox
 * Mozilla Thunderbird
 * TorBrowser

### Communication

 * Discord
 * LINE
 * Skype
 * Slack
 
### Multimedia

 * Spotify

### Office & Documents

 * LyX
 * MacTeX
 * Microsoft Office
 * Microsoft OneNote
 * Microsoft To-Do
 
### Text Editors

 * TextMate
 * Typora

### Creativity

 * Adobe Creative Cloud
 * Audacity
 * Blender
 * GarageBand
 * GIMP
 * HandBrake
 * Inkscape
 * Kid3
 * MuseScore 2

### Cloud Storage

 * Dropbox

### Utilities

 * Amphetamine
 * AppCleaner
 * balenaEtcher
 * Battery Monitor
 * DaisyDisk
 * iTerm2
 * JamWiFi
 * MacUpdater
 * The Unarchiver
 * TripMode
 * WiFi Explorer
 * XQuartz

### Development

 * Burp Suite
 * DBeaver
 * Docker Desktop for Mac
 * Electron Fiddle
 * Eclipse
 * Emacs
 * Fork
 * IntelliJ IDEA
 * MacVim
 * MongoDB Compass
 * MongoHub
 * MySQL Workbench
 * Sourcetree
 * VirtualBox
 * Visual Studio
 * Visual Studio Code
 * Wireshark
 * Xcode

### Scientific

 * CoqIDE
 * Isabelle/HOL

Automater Snippets
------------------------------------------------------------------------

### Reset Launchpad Layout

```bash
/usr/bin/defaults write com.apple.dock ResetLaunchPad -bool true; /usr/bin/killall Dock
```

Console Config
------------------------------------------------------------------------

### Enable Touch ID for sudo

```bash
sudo vim /etc/pam.d/sudo
```

```
auth       sufficient     pam_tid.so
```

### Make sudo to ask password everytime

```bash
sudo visudo
```

```
Defaults        env_reset,timestamp_timeout=0
```

Console Applications (Homebrew)
------------------------------------------------------------------------

### Prerequisites

```bash
xcode-select --install
```

Then, install [Homebrew](http://brew.sh/).

```bash
brew update && brew upgrade
```

### Homebrew Taps

```bash
brew tap brewsci/bio
brew tap brewsci/science
brew tap homebrew/cask
brew tap homebrew/command-not-found
brew tap homebrew/services
```

### Essentials

```bash
brew install \
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
brew install \
  aria2 \
  fdupes \
  grep \
  pstree \
  rename \
  renameutils \
  watch
```

### macOS-specific

```bash
brew install \
  brew-cask-completion \
  launchctl-completion \
  open-completion \
  zsh-completions
```

### Source Code Management

```bash
brew install \
  git \
  subversion
```

### VMs & Containers

```bash
brew install \
  ansible
```

```bash
brew install \
  docker-completion \
  docker-compose-completion \
  docker-machine-completion \
  packer-completion \
  vagrant-completion
```

### Documents & Visualization

```bash
brew install \
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
brew install \
  graphicsmagick \
  graphviz \
  imagemagick
```

### Networking

```bash
brew install \
  corkscrew \
  iperf \
  nmap \
  socat
```

### Databases

```bash
brew install \
  mysql \
  postgresql \
  sqlite
```

### Build Tools

```bash
brew install \
  autoconf \
  autogen \
  automake \
  cmake \
  libtool
```

### Programming Languages

```bash
brew install \
  go \
  ocaml \
  opam \
  r \
  rust
```

```bash
brew install \
  rustc-completion
```

### Haskell-specific

```bash
brew install \
  cabal-install \
  ghc \
  haskell-stack
```

### Python-specific

```bash
brew install \
  python \
  pypy3
```

```bash
brew install \
  pip-completion \
  numpy \
  scipy \
  matplotlib
```

### Java-specific

```bash
brew tap adoptopenjdk/openjdk
```

```bash
brew cask install \
  adoptopenjdk8 \
  adoptopenjdk8-openj9 \
  adoptopenjdk8-openj9-jre \
  adoptopenjdk11 \
  adoptopenjdk11-openj9
```

```bash
brew install \
  ant \
  gradle \
  maven
```

```bash
brew install \
  gradle-completion \
  maven-completion
```

```bash
brew install \
  tomcat \
  tomcat@8
```

### Node-specific

```bash
brew install \
  node \
  yarn
```

```bash
brew install \
  yarn-completion
```

### Swift-specific

```bash
brew install \
  carthage \
  cocoapods \
  swiftlint
```

### Web Development

```bash
brew install \
  jq \
  mitmproxy
```

### Project Management

```bash
brew install \
  cloc \
  sloccount
```
