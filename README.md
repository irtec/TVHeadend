# Note: Linux Ubuntu 16.04 Architecture accepted: 

- i386
- amd64
- armhf 
- arm64

________________________________________________________________________________________________

# 1. install GPG keys:
<p>Bintray :
 <p>sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61 

<p>Doozer (apt.tvheadend.org):
 <p>wget -qO- https://doozer.io/keys/tvheadend/tvheadend/pgp | sudo apt-key add -
<p>
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
 echo "deb https://dl.bintray.com/tvheadend/deb xenial stable-4.2" | sudo tee /etc/apt/sources.list.d/tvheadend.list

# Doozer:
 echo "deb http://apt.tvheadend.org/unstable xenial main" | sudo tee -a /etc/apt/sources.list.d/tvheadend.list

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

=====================================================================================================================================================================================================================================================================================================================================================================================================================

# Building TVHEADEND :
# 1. Installing dependencies
$ sudo apt install build-essential git libpcre2-dev pkg-config libssl-dev bzip2 wget libavahi-client-dev zlib1g-dev libavcodec-dev libavutil-dev libavformat-dev libswscale-dev libavresample-dev gettext cmake libiconv-hook-dev liburiparser-dev debhelper libcurl4-gnutls-dev python-minimal libdvbcsa-dev python-requests
 <p>OPTIONAL :
<p>$ sudo apt install dvb-apps libva-dev libva-drm1 libva-x11-1</p>

# 2. Download the latest stable
$ git clone https://github.com/tvheadend/tvheadend.git

# 3. Configuring the build tool
$ cd tvheadend
<p>$ ./configure --enable-libffmpeg_static --disable-dvbscan
<span><p>$ sudo make
<span><p>$ sudo make install

# start tvh :
sebelumnya cek terlebih dahulu binary di directory /usr/local/bin/ atau /usr/bin/ jika sudah menemukan langsung eksekusi

# 4. Config TVH 
$ tvheadend -C (default)

# 5. accsess webif
http://ip:9981

==================================================================================================================================================================
<p>
Selanjutnya :
<p>Copy/paste Script Start/Stop "tvheadend" ke directory /etc/init.d
<p>berikan hak akses 755
<p>chmod 755 /etc/init.d/tvheadend
 <p><p>
 Untuk autostart pada saat booting silahkan edit rc.local dan input perintah seperti di bawah :
 <p>sleep 5
<p>/etc/init.d/tvheadend start
 <br>=================================================================================
 <br>=================================================================================
<br><br>
 <p>rebuild $ make distclean
<p>by <i>https://github.com/irtec</i>
