# TWRP for Samsung Galaxy A32 5G (a32x/A326B)

# Issues / Todo
- Check if all the mount points are correct
- Fix issue with kernel not compiling (Currently using prebuilt kernel extracted from original OS)
- In fastboot mode, ADB is working but Fastboot is not

# Building
## Step 0 - Minimum Requirements
- Relatively recent x86_64 processor (Like after a 2nd gen Intel processor)
- 16GB RAM
- 40GB HDD Space
- Ubuntu 22.04 LTS
- An A326B Phone with it's bootloader unlocked, and ADB enabled (I will not be covering this here)

## Step 1 - Preparing the build environment
Install the dependencies:
```
sudo apt install git-core git git-lfs python3 python3-pip python-is-python3 gnupg flex bison build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig repo heimdall-flash
```

Create a build directory:
```
mkdir ~/twrp
cd ~/twrp
```
From now on, this whole guide takes place in this build directory.

## Step 2 - Downloading the base TWRP sources
Initialize repo.
```
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
```

Now, download the sources.
```
repo sync
```
Note: This will take a while as it has to download roughly 30 GB.

## Step 3 - Apply the a32x Kernel and Device tree
Create the folder ```.repo/local_manifests/``` if it does not exist already. <br>
Take the ```a32x.xml``` from this repo and put it in ```.repo/local_manifests/``` <br>
Resync the repo with ```repo sync``` <br>
Note: This won't take nearly as long because it only has to download 2 new repositories.

## Step 4 - Build the recovery image
Configure the build:
```
lunch twrp_a32x-eng
```

Compile the recovery image:
```
mka recoveryimage
```

Note: You can change the output directory by running the command below before Step 4:
```
export OUT_DIR=out_directory
```

Note: This could take up to an hour depending on processor speed.

## Step 5 - Flash the recovery image
The compiler will tell you where the ```recovery.img``` is, but if you didn't change the output directory, it will be in ```out/target/product/a32x/recovery.img``` <br>
Copy the ```recovery.img``` to an empty folder. <br>
Download the ```vbmeta.img``` in this repo to the same empty folder. <br>
With the phone in android, boot it into download mode: ```adb reboot download``` <br>
Now flash the ```vbmeta.img``` and the ```recovery.img``` to the phone: <br>
```sudo heimdall flash --vbmeta vbmeta.img --recovery recovery.img``` <br>
The phone will automatically reboot back into android. <br>
Congratulations! TWRP is now flashed to the phone.

## Step 6 - Booting into TWRP
With ADB: ```adb reboot recovery``` <br>
Without ADB: Hold the volume up button and the power button. Once the phone powers on, let go of the power button.

# NOTICE
I am not responsible for you bricking your phone. <br>
Also please backup for phone's ROM or at least have a ROM you can flash back onto your phone in the case of a brickage.

# References
blah
