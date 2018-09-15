# Note: Linux Ubuntu 16.04 Architecture accepted: 

- i386
- amd64
- armhf 
- arm64

________________________________________________________________________________________________

# 1. install GPG keys:
Bintray :
 sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61 

Doozer (apt.tvheadend.org):
 wget -qO- https://doozer.io/keys/tvheadend/tvheadend/pgp | sudo apt-key add -

If you see something like the following:
Executing: /tmp/apt-key-gpghome666/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
gpg: failed to start the dirmngr '/usr/bin/dirmngr': No such file or directory
gpg: connecting dirmngr at '/run/user/0/gnupg/d.1234/S.dirmngr' failed: No such file or directory
gpg: keyserver receive failed: No dirmngr
>>>>>>>>>>>>>>>>>>>>>>>>

# You need to install dirmngr:
 sudo apt-get install dirmngr

>>>>>>>>>>>>>>>>>>>>>>>>

# 2. Pick a build type, add the repository accordingly:

# Bintray:
 echo "deb https://dl.bintray.com/tvheadend/deb trusty stable-4.2" | sudo tee /etc/apt/sources.list.d/tvheadend.list

# Doozer:
 echo "deb http://apt.tvheadend.org/unstable trusty main" | sudo tee -a /etc/apt/sources.list.d/tvheadend.list

>>>>>>>>>>>>>>>>>>>>>>>>

# 3. Update:
 sudo apt-get update

>>>>>>>>>>>>>>>>>>>>>>>>

# 4. Installation TVHeadend:
 sudo apt-get install tvheadend -y

# 5. Restart
 service tvheadend restart

>>>>>>>>>>>>>>>>>>>>>>>>
Login: 
http://IP:9981
(User/ Password will be asked during installation )

========================================================================================================================================================================================================================================================================================================================================================================================================================

# Building TVHEADEND :
# 1. Installing dependencies
 sudo aptitude install build-essential git pkg-config libssl-dev bzip2 wget
 OPTIONAL :
 sudo aptitude install libavahi-client-dev zlib1g-dev libavcodec-dev libavutil-dev libavformat-dev libswscale-dev libavresample-dev

# 2. Download the latest stable
 git clone https://github.com/tvheadend/tvheadend.git

# 3. Configuring the build tool
 AUTOBUILD_CONFIGURE_EXTRA=--enable-libffmpeg_static\ --enable-trace\ --enable-debug ./Autobuild.sh

# 4. Compiling
 make

# 5. Installing the binaries
 sudo make install
 ./build.linux/tvheadend

# 6. Config TVH 
 tvheadend -C
