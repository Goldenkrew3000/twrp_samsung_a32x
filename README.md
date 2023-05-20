# twrp_samsung_a32x
TWRP Recovery for Samsung A32 5G (a32x/A326B)

# Issues / Todo
- Check if all the mount points are correct
- Fix issue with kernel not compiling (Currently using prebuilt kernel extracted from original OS)

# Building
## Step 0 - Minimum Requirements
- 64-bit x86_64 processor
- 16GB RAM
- 40GB HDD Space
- Ubuntu 22.04 LTS

## Step 1 - Preparing the build environment
Install the dependencies:
```
sudo apt install git-core git git-lfs python3 python3-pip python-is-python3 gnupg flex bison build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig repo
```

Create a build directory:
```
mkdir ~/twrp
cd ~/twrp
```

# Step 2 - Downloading the base TWRP sources
In your build directory, initialize repo.
```
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
```

Now, download the sources.
```
repo sync
```
Note: This will take a while as it has to download roughly 30 GB.

# Step 3 - Apply the phone (A326B) Kernel and Device tree.


# References
blah
