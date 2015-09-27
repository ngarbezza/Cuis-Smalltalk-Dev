## Setting up and starting Cuis using a command line

What follows are instructions for setting up Cuis on Linux or Mac OS X using the command line. If you are familiar with Git, you can use it, but that is not described here. If you are on Windows, there are instructions for using the Windows file explorer in another document. This document is intended for beginners, and tries to require as little previous knowledge as possible.

### On Linux ###
```
$ mkdir MyProject
$ cd MyProject
$ wget https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev/archive/master.zip
$ unzip master.zip
$ wget -O coglinuxht.tgz www.mirandabanda.org/files/Cog/VM/VM.r3370/coglinuxht-15.22.3370.tgz
$ tar -zxvf coglinuxht.tgz
```
If this is the first time you run Cuis Smalltalk on this system, add 32 bit libraries:
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6-i386
# This (libc6-i386) was needed to make ldd work on 32 bit programs and dynamic libraries
# So, we can do stuff like       $ ldd coglinuxht/lib/squeak/4.5-3370/squeak       to find about missing libraries
sudo apt-get install libuuid1:i386
sudo apt-get install libX11-6:i386
sudo apt-get install libXext6:i386
sudo apt-get install libsm6:i386
# Next 3 are only needed if you want to play with OpenCL (you also need Catalyst driver for AMD GPU, or similar for Intel/Nvidia)
sudo apt-get install mesa-common-dev:i386
sudo apt-get install libgl1-mesa-dev:i386
cp /usr/lib/i386-linux-gnu/libOpenCL.so.1 libOpenCL.so
```
```
$ coglinuxht/squeak Cuis-Smalltalk-Dev-master/Cuis4.2-2505.image
```

### On Mac OS X ###
```
$ mkdir MyProject
$ cd MyProject
$ curl -L -o master.zip  https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev/archive/master.zip
$ unzip master.zip
$ curl -o Cog.app.tgz www.mirandabanda.org/files/Cog/VM/VM.r3370/Cog.app-15.22.3370.tgz
$ tar -zxvf Cog.app.tgz
$ Cog.app/Contents/MacOS/Squeak Cuis-Smalltalk-Dev-master/Cuis4.2-2505.image
```