# Intro
This repo contains a local_manifest file for the narina device aka, The Leapfrog Epic. 

# Device Info
The LeapFrog Epic (codenamed "narnia/UYT") is an Android-powered mini tablet computer developed and marketed by LeapFrog and manufactured by Quanta Computer. As with all of LeapFrog's devices, the Epic is designed and marketed primarily as an educational device for children ages 3-9, with bespoke software designed to teach children about elementary school subjects such as language, maths and geography amongst other things. Under the bonnet, it shares a lot in common with entry-level, discount-price tablets such as the Amazon Fire line of tablets and was even made by the same OEM.

It was announced on August 2015 and released on September 2015. Updated variants of the device such as the LeapFrog Epic Academy Edition and the LeapPad Academy were also released in 2017 and 2019 respectively; they are essentially identical to the base model apart from (slightly) updated firmware, redesigned bumpers and access to the LeapFrog Academy programme.

## Device Picture

![Leapfrog Epic](https://i.imgur.com/1Pr3fzG.png)

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | 1.3GHz Quad-Core MT8127
GPU     | Mali-450MP
Memory  | 1GB RAM
Shipped Android Version | 4.4.2
Kernel  | 3.4.67
Storage | 16GB
Display | 7" 1024 x 600 px
Cameras | 2.0MP front, 2.0MP rear

## Whats working/ not working 

Not Working

* NVRAM has issues (SELinux permissions?)
* Video recording crashes the camera app
* Battery life is pathetically horrible and needs optimisation
* Some performance issues due to certain services
* HWC/ION error log spam
* 1080p video lag (codec issues? LOS14.1 for ford also has similar problems apparently. Videos are rendered through software) 
* FM Radio

Working

* HWC
* Wifi/Bluetooth
* 2D/3D acceleration
* Accelerometer
* Touchscreen
* Audio (internal and headset)
* Internal microphone

﻿Build guide


1) get Xubuntu 16.04 installed on your machine somehow, like via burning it to a CD or USB and booting from it.  I will mostly leave this part up to you since some people want to dual boot it beside windows and some people want to replace windows entirely.  I won't be saying how to install it here, that's up to you.  I will say this though, make sure you have AT LEAST 4GB OF PHYSICAL RAM AT MINIMUM, and that you have AT LEAST 200GB OF HARD DRIVE SPACE AT MINIMUM


http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/xubuntu-16.04.5-desktop-amd64.iso


2) you'll want to add a new swap file or supplement your existing swap file.  Swap acts like slower RAM when all your real RAM is used up and this is necessary if your computer has less than 16GB of real physical RAM.  Make a swap file with the following commands


sudo fallocate -l 16G /myswapfile
sudo chmod 600 /myswapfile
sudo mkswap /myswapfile
sudo swapon /myswapfile


3) install all the dependencies for building with the following really long command


sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev rep openjdk-8-jdk imagemagick schedtool flex jq maven


4) close out from that terminal session once its done and go into your home directory.  make a new folder called "lin14" or something (this assumes you're building lineage 14.1 nougat) and go into that folder younook just made.  Right click somewhere and click Open Terminal Here. Once the terminal opens inside the lin14 folder you made run the following command to get the environment everything synced up


repo init -u https://github.com/LineageOS/android.git -b cm-14.1


5) at this point it will say things like "Error, you need a name and an email to do this" so copy those commands it gives you and modify+paste+run them replacing the "you@example.com" and the "Your Name" with your actual name and email


Note that copying and pasting in the Xubuntu terminal isn't like normal, Ctrl+C and Ctrl+V don't work, you have to use Ctrl+Shift+C and Ctrl+Shift+V


6) once you set up your name and email you have to re-run that repo init command above one more time.  then once it does what it has to do successfully you run the following command below and wait (because this takes a really long time)


repo sync --force-sync


7) after a couple hours it should be done, now you have to add all the device trees and stuff so it knows what phone to build for.  I will assume you want to build for perry so in your terminal type the following command to make the file browser open up in the place we need it to


thunar ~/lin14/.repo


8) inside the new file manager window make a new folder called "local_manifests" and inside THAT make a new file called "roomservice.xml" and open that roomservice with a text editor by clicking on it.  Copy everything you see from the link below and paste/save in the roomservice


https://raw.githubusercontent.com/WindowsXP95/local_manifests_narnia/master/roomservice.xml


9) once you have your roomservice saved you can close out of that file manager, go back to that terminal emulator session you're running (assuming you didn't close out of it, if you did re-open a new one and MAKE SURE IT'S IN THE LIN14 FOLDER YOU MADE), and re-run "repo sync --force-sync" again so it can pull all the device/kernel/vendor trees for perry that you just specified in the roomservice file


10) once it is done the second time we are ready to build.  In the terminal emulator window inside the lin14 folder where everything is, run "source build/envsetup.sh" and then "brunch narnia" to finally initiate the building process.  this will take a very long time.  

 ###### Maintainers
-mac2612 [github](https://github.com/mac2612)

-Kaijones23 [xda](https://forum.xda-developers.com/member.php?u=9605864)|[github](https://github.com/488315)

-huckleberrypie [xda](http://forum.xda-developers.com/member.php?u=4092918)|[github](https://github.com/huckleberrypie)

-R0rtiz [xda](https://forum.xda-developers.com/member.php?u=8978978)|[github](https://github.com/R0rt1z2)

-Stricted [xda](https://forum.xda-developers.com/member.php?u=8184192)|[github](https://github.com/Stricted)

-WindowsXP95 
        
        
