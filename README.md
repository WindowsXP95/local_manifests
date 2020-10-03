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

## Building Lineage for narnia

Follow the instructions below

First of all, follow step 1 and continue from there

        # repo init -u git://github.com/LineageOS/android.git -b cm-14.1
        
        # Go to your .repo folder in the directory your source is in. 
        The folder is hidden in your work dir, so enable hidden files to view it. Make a new folder called 'local_manifests'. Then enter 'git clone https://github.com/WindowsXP95/local_manifests_narnia.git'
        
        # repo sync
        
        # cd device/quanta/narnia/patches/patch.sh
        
        # . build/envsetup.sh

        # lunch lineage_narnia-eng

        # make clean && make bacon
        
 ###### Maintainers
-mac2612 [github](https://github.com/mac2612)

-Kaijones23 [xda](https://forum.xda-developers.com/member.php?u=9605864)|[github](https://github.com/488315)

-huckleberrypie [xda](http://forum.xda-developers.com/member.php?u=4092918)|[github](https://github.com/huckleberrypie)

-R0rtiz [xda](https://forum.xda-developers.com/member.php?u=8978978)|[github](https://github.com/R0rt1z2)

-Stricted [xda](https://forum.xda-developers.com/member.php?u=8184192)|[github](https://github.com/Stricted)

-WindowsXP95 
        
        
