## Build for Linux
If you prefer to compile your own binary files, then you need the developer packages:

<b>Ubuntu / Debian:</b>
 
 	sudo apt-get install git qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev libssl-dev libdb++-dev libqrencode-dev libminiupnpc-dev

If you have an error installing qt4-qmake (Arises on Ubuntu 14.04.2 and possibly in other versions)

	libcheese-gtk23: Depends: libclutter-gtk-1.0-0 (> = 0.91.8) but it is not going to be installed
	                  Depends: libcogl15 (> = 1.15.8) but it is not going to be installed
	libcheese7: Depends: libclutter-gst-2.0-0 (> = 0.10.0) but it is not going to be installed
	             Depends: gstreamer1.0-clutter but it is not going to be installed
	libclutter-1.0-0: Depends: libcogl-pango15 (> = 1.15.8) but it is not going to be installed
    Depends: libcogl15 (> = 1.15.8) but it is not going to be installed

Then enter:

	sudo apt-get install libglew-dev libcheese7 libcheese-gtk23 libclutter-gst-2.0-0 libcogl15 libclutter-gtk-1.0-0 libclutter-1.0-0 xserver-xorg-input-all

<b>openSUSE (verified on version 13.2):</b>

	 sudo zypper install git gcc-c ++ libqt4-devel boost-devel libopenssl-devel libdb-4_8-devel libqrencode3

After the installation was completed, you can clone the Ammo repository:
	
    git clone https://github.com/AmmoCore/ammoreloaded.git

and finally, compile your client.

<b>Note: for all of the 'make' commands below, it is recommended to speed things up by using the '-j' option followed by the number of cores on your processor. This enables multi-threading. Example:</b>

	make -j4 #4 core processor, utilizes the whole processor and takes much less time to compile


	cd ammoreloaded/src/leveldb/
	make clean
	make
	make libmemenv.a 

To compile the coin daemon:
	
    cd ..
	make -f makefile.unix

To compile the graphical version:

	cd ammoreloaded
	qmake
	make

After compiling both clients, don't forget to strip them, reducing their size by around 90%:

	strip Ammod
	strip Ammo-qt

If you want to build using static libraries:
	
    make -f makefile.unix STATIC=1
	qmake RELEASE=1

And that should be it. If you have any problems compiling please create an issue so it can be fixed ASAP!
