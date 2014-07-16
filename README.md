Setting up Linux, LaTeX, git and Eclipse
=================

Setup instructions for starting with a bare-metal machine and setting up Linux, LaTeX, Eclipse and git

# Install Linux

### Linux Mint 17 Qiana, XFCE edition

Based on Ubuntu 14.04 LTS, but with fewer kernel updates; XFCE desktop is fast, easy to use, widespread. 

1. Download .iso or .usb, and make bootable DVD / USB stick
2. Run updates and restart.

# Synaptic package manager

In **Synaptic Package Manager** (`apt-get`), install packages:

+ git
+ pcmanfm
+ alacarte

_Optional packages_ 

+ nfs-common
+ laptop-mode-tools
+ powerstat

# 4. Install LaTeX distribution

### TexLive 2014

Modern distribution, flexible. Must download the latest from texlive.org (Ubuntu packages are way out of date). Extract archive, then run

```
sudo ./install_tl
```

This launches the text-based installer. A good minimum installation (about 700 MB) uses the **scheme-basic** scheme, letter size instead of A4, and adds the following packages:

+ recommended fonts, 
+ Chinese, 
+ Chinese/Japanese/Korean (base), 
+ Latex recommended packages

After installation completes, add the RevTeX-4.1 packages for Physical Review

```
/usr/local/texlive/2014/bin/x86_64-linux $ sudo ./tlmgr install revtex
```
# 5. Generate SSH keys to interact with repository

```
ssh-keygen -t rsa -C "plu@fas.harvard.edu"
```

# 6. Eclipse Luna C++ IDE
unzip, move to /opt, change permission

# 7. Texlipse: help->install new software, with path http://texlipse.sourceforge.net
Window->Preferences->Texlipse->Builder Settings
path: /usr/local/texlive/2014/bin/x86_64-linux

# 8. Configure git for first usage
```
git config --global user.name "Peter J. Lu"
git config --global user.email plu@fas.harvard.edu
```

# 9. Install lastpass for Chrome, login to bitbucket.org
Upper right corner, drop down "manage account"
SSH keys option on left
add text from id_rsa.pub

# 10. in ~/workspace/
```
git init
git clone git@bitbucket.org:peterjlu/aot_xl.git
````

# 11. In eclipse: file->import->general->existing projects into workspace

# 12. Updating a git repository
```
git add -A
git commit -m 'name of update'
git push
```
