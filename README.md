Setting up Linux, LaTeX, git and Eclipse
=================

Setup instructions for starting with a bare-metal machine and setting up Linux, LaTeX, Eclipse and git

# 1. Install Linux Mint xfce edition

# 2. Run updates and restart.

# 3. Install from synaptic package manager: git, pcmanfm, alacarte, nfs-common, laptop-mode-tools, powerstat

# 4. download and install TexLive:
scheme-basic
added: recommended fonts, Chinese, Chinese/Japanese/Korean (base), Latex recommended packages
use letter size instead of A4 by default
/usr/local/texlive/2014/bin/x86_64-linux $ sudo ./tlmgr install revtex

# 5. SSH key generation
ssh-keygen -t rsa -C "plu@fas.harvard.edu"

# 6. Eclipse Luna C++ IDE
unzip, move to /opt, change permission

# 7. Texlipse: help->install new software, with path http://texlipse.sourceforge.net
Window->Preferences->Texlipse->Builder Settings
path: /usr/local/texlive/2014/bin/x86_64-linux

# 8. git setup
git config --global user.name "Peter J. Lu"
git config --global user.email plu@fas.harvard.edu

# 9. Install lastpass for Chrome, login to bitbucket.org
Upper right corner, drop down "manage account"
SSH keys option on left
add text from id_rsa.pub

# 10. in ~/workspace/
git init
git clone git@bitbucket.org:peterjlu/aot_xl.git

# 11. In eclipse: file->import->general->existing projects into workspace

# 12. git add -A
git commit -m 'name of update'
git push
