Setting up Linux, LaTeX, git and Eclipse
=================

Setup instructions for starting with a bare-metal machine and setting up Linux, LaTeX, Eclipse, git and JabRef. These tools are all free, open-source and are designed for multi-user asynchronous authoring and collaborative editing of documents with references, and far exceed the capabilities of the typical Windows-style tools of previous decades (Windows, EndNote, MathType) which as far as I am concerned should be avoided.

# Linux

Most open-source tools are designed to work with Linux first and foremost, usually with reasonable Mac OS X support (though none of this is tested on that platform). Windows support is generally less developed, and frankly instead of using the Windows-Linux hybrid tools, it's much easier to just install VirtualBox and run everything in an Linux virtual machine.

### Linux Mint 17 Qiana, XFCE edition

Based on Ubuntu 14.04 LTS, but with fewer kernel updates; XFCE desktop is fast, easy to use, and widespread. Either bare-metal install or virtual machine (e.g. VirtualBox) is fine for this demo.

1. Download .iso or .usb from http://www.linuxmint.com/download.php, and make bootable DVD / USB stick. 

2. Run updates and restart.

### Synaptic package manager

In **Synaptic Package Manager** (`apt-get`), install packages:

+ git
+ pcmanfm
+ alacarte

_Optional packages that I find useful_ 

+ nfs-common
+ laptop-mode-tools
+ powerstat

# LaTeX

Everyone should use LaTeX for all scientific and technical publications. 

### TexLive 2014

This is a large, modern, updated and full-featured distribution, with a great deal of flexibility. Although you can install it through Synaptic, for some reason the packages that Ubuntu releases are always way, way out of date. Instead:

1. Download the latest from http://tug.org/texlive/
2. Extract the archive, either using the desktop or command-line. 
3. Run the installation script with root permissions:

```
sudo ./install_tl
```

This launches the text-based installer. A good minimum installation (about 700 MB) uses the **scheme-basic** scheme, letter size instead of A4, and adds the following packages:

+ recommended fonts
+ Latex recommended packages

_For Asian names_:
+ Chinese 
+ Chinese/Japanese/Korean (base)

The installer will download all of the packages you specify, so you must be online, and depending on the server traffic, can be very slow.

4. After installation completes, add the RevTeX-4.1 packages for _Physical Review_ journals.

```
/usr/local/texlive/2014/bin/x86_64-linux $ sudo ./tlmgr install revtex
```

# Eclipse

Eclipse is a large software integrated development environment (IDE), open-sourced by IBM. Current version is Eclipse 4.4 "Luna". To install:

1. download from http://eclipse.org/downloads/ 
2. extract archive, which places all files in single folder
3. for convenience, move to a system directory

```
sudo mv eclipse /opt/
sudo chmod 777 /opt/eclipse
```

### Texlipse

LaTeX integration for Eclipse, which controls the document build process. When you modify any file and save it, Eclipse will automatically execute the right programs to rebuild the document. To install in Eclipse:

1. help->install new software, with path http://texlipse.sourceforge.net

2. Window->Preferences->Texlipse->Builder Settings, set path: /usr/local/texlive/2014/bin/x86_64-linux

# Git

Git is the version-control system used to manage the Linux kernel, and was written by Linux Torvalds himself (the creator of Linux).  

### Configure git for first usage

```
git config --global user.name "Peter J. Lu"
git config --global user.email plu@fas.harvard.edu
```

### SSH keys 
In order to manage identities and security, git (like many modern Linux tools) requires authentication, and does so via SSH keys. This will allow modifications from your machine to change a remote repository in the cloud, and replaces login credentials. To generate the SSH keys to allow you to `push` to remote git repository:

```
ssh-keygen -t rsa -C "plu@fas.harvard.edu"
```

### Add SSH key to bitbucket.org repository 

1. login to https://www.bitbucket.org
2. In upper right corner, drop down "manage account", SSH keys option on left: add text from id_rsa.pub

# Working with Git, Eclipse and LaTeX

The first step is to clone a repository from the remote location to the local machine and then import into a new Eclipse project. In the workspace directory (typically `~/workspace`):

```
git clone git@bitbucket.org:peterjlu/aot_xl.git
````

In Eclipse: file->import->general->existing projects into workspace

This will create a new project that Eclipse is aware has a remote git-repository. Eclipse has great integration with git, so that you can use either the command-line or the internal GUI-based tools, with the same results and no conflicts. 

### Updating a git repository: command-line

```
git add -A
git commit -m 'name of update'
git push
```
### Updating a git repository: inside Eclipse

Right click on the project name in the _Project Explorer_, Team->commit. Enter the text

