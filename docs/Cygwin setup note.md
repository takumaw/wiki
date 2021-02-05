Cygwin Setup Note
========================================================================

Installation
------------------------------------------------------------------------

```cmd
setup-x86_64.exe -q ^
 --root C:¥Cygwin64 --local-package-dir C:¥Cygwin64¥packages ^
 --arch x86_64 --no-desktop --disable-buggy-antivirus --upgrade-also --no-desktop ^
 --categories="Admin,Base" ^
 --packages="afio,arc,bzip2,cabextract,hdf5,lrzip,lzip,lziprecover,makeself,p7zip,par2,rsnapshot,sharutils,unzip,xz,zip,zziplib,mediainfo,postgresql,sqlite3,autobuild,autoconf,automake,check,clang,make,cppunit,ddd,doxygen,gcc-core,gcc-g++,gdb,git,git-svn,gperf,help2man,make,mercurial,nasm,openssl-devel,patch,patchutils,pkg-config,subversion,subversion-tools,texinfo,yasm,bvi,emacs,nano,vim,ImageMagick,gawk,llvm,python,ruby,corkscrew,curl,iperf,nc,nghttp2,openssh,ping,rsync,tftp,whois,bash-completions,chere,zsh,attr,expect,untex,convmv,ddrescue,screen,symlinks,time,tmux,w3m,wget,wput,xorg-server"
 ```
 
Configuration
------------------------------------------------------------------------
 
```bash
rm /etc/passwd
rm /etc/groups
```

```bash
vi /etc/nsswitch.conf
```

```
db_home: windows
db_shell: desc
db_gecos: windows
```

```cmd
net user takumaw /comment:"<cygwin shell =\"/bin/zsh\"/>"
```

Ref.

 * https://cygwin.com/cygwin-ug-net/ntsec.html
 
Environmental Variables
------------------------------------------------------------------------

 * `CYGWIN`=`winsymlinks:nativestrict`

Explorer Tweaks
------------------------------------------------------------------------

`Cygwin Here.reg`:

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\zsh]
@="Open Cygwin Here"

[HKEY_CLASSES_ROOT\Directory\shell\zsh\command]
@="C:\\cygwin64\\bin\\mintty.exe -i /Cygwin-Terminal.ico -e /bin/xhere /bin/zsh.exe"

[HKEY_CLASSES_ROOT\Drive\shell\zsh]
@="Open Cygwin Here"

[HKEY_CLASSES_ROOT\Drive\shell\zsh\command]
@="C:\\cygwin64\\bin\\mintty.exe -i /Cygwin-Terminal.ico -e /bin/xhere /bin/zsh.exe"

[HKEY_CLASSES_ROOT\Directory\Background\shell\zsh]
@="Open Cygwin Here"

[HKEY_CLASSES_ROOT\Directory\Background\shell\zsh\command]
@="C:\\cygwin64\\bin\\mintty.exe -i /Cygwin-Terminal.ico -e /bin/xhere /bin/zsh.exe"

[HKEY_CLASSES_ROOT\LibraryFolder\Background\shell]

[HKEY_CLASSES_ROOT\LibraryFolder\Background\shell\zsh]
@="Open Cygwin Here"

[HKEY_CLASSES_ROOT\LibraryFolder\Background\shell\zsh\command]
@="C:\\cygwin64\\bin\\mintty.exe -i /Cygwin-Terminal.ico -e /bin/xhere /bin/zsh.exe"
```
