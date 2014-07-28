Setting up Linux, LaTeX, git and Eclipse
=================

Setup instructions for starting with a bare-metal machine and setting up Linux, LaTeX, Eclipse and git

# Linux: install and configure

### Linux Mint 17 Qiana, XFCE edition

Based on Ubuntu 14.04 LTS, but with fewer kernel updates; XFCE desktop is fast, easy to use, widespread. 

1. Download .iso or .usb from http://www.linuxmint.com/download.php, and make bootable DVD / USB stick

2. Run updates and restart.

## Synaptic package manager

In **Synaptic Package Manager** (`apt-get`), install packages:

+ git
+ pcmanfm
+ alacarte

_Optional packages_ 

+ nfs-common
+ laptop-mode-tools
+ powerstat

# Install LaTeX distribution

### TexLive 2014

Modern distribution, flexible. Must download the latest from http://tug.org/texlive/ (Ubuntu packages are way out of date). Extract archive, then run

```
sudo ./install_tl
```

This launches the text-based installer. A good minimum installation (about 700 MB) uses the **scheme-basic** scheme, letter size instead of A4, and adds the following packages:

+ recommended fonts
+ Latex recommended packages

_For Asian names_:
+ Chinese 
+ Chinese/Japanese/Korean (base)

After installation completes, add the RevTeX-4.1 packages for _Physical Review_ journals.

```
/usr/local/texlive/2014/bin/x86_64-linux $ sudo ./tlmgr install revtex
```
# SSH keys 
Generate SSH keys to be able to `push` to remote git repository.

```
ssh-keygen -t rsa -C "plu@fas.harvard.edu"
```

# Eclipse IDE

Large software integrated development environment (IDE), open-sourced by IBM. Current version is Eclipse 4.4 "Luna". Download from http://eclipse.org/downloads/ and extract archive, which places all files in single folder.

```
sudo mv eclipse /opt/
sudo chmod 777 /opt/eclipse
```

# Texlipse

LaTeX integration for Eclipse, runs all tools, etc. In Eclipse:

1. help->install new software, with path http://texlipse.sourceforge.net

2. Window->Preferences->Texlipse->Builder Settings, set path: /usr/local/texlive/2014/bin/x86_64-linux

# Configure git for first usage

```
git config --global user.name "Peter J. Lu"
git config --global user.email plu@fas.harvard.edu
```

# Add SSH key to bitbucket.org repository 

1. login to https://www.bitbucket.org
2. In upper right corner, drop down "manage account", SSH keys option on left: add text from id_rsa.pub

# Clone repository and import into Eclipse

In the workspace directory (typically `~/workspace`):

```
git clone git@bitbucket.org:peterjlu/aot_xl.git
````

In Eclipse: file->import->general->existing projects into workspace

# Updating a git repository
```
git add -A
git commit -m 'name of update'
git push
```
