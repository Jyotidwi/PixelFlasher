# PixelFlasher
A Powershell script to update a rooted Pixel phone with new factory image and retain root.

## DESCRIPTION
This is a Powershell script to flash a rooted Pixel phone with patched factory image to retain root.
The script automates the following steps:
- Checks for the factory image
- Unpacks factory image
- Checks for dependencies (adb, fastboot, 7zip, ...)
- Unzips the factory image
- Extracts unpatched boot.img
- Deletes flash-all.sh and flash-base.sh (just for extra precaution)
- Patches flash-all.bat and removes the wipe option
- Checks and validates phone connection
- Checks and validates that the phone model matches the factory image
- Transfers stock boot.img to the phone
- Launches Magisk
- Waits for the user to complete the patch on the phone
  - TODO: automate the previous step to magisk patch programatically
- Transfers patched boot.img to the PC
- Replaces stock boot.img with patched boot.img
- Repackages the image zip with patched boot.img
- Reboots to bootloader and pauses
- Launches flash_all.bat to update the phone

## Prerequisites
- [Android SDK Platform-Tools](https://developer.android.com/studio/releases/platform-tools.html)
- [Android Pixel phone factory image](https://developers.google.com/android/images)
- [7z.exe from 7-Zip](https://www.7-zip.org/)

## Setup
- Download or clone the repository
- Make sure the prerequisities are met

The easiest way to run this 
- copy the factory image into the script directory, 
- make sure, adb.exe, fastboot.exe, and 7z.exe are in the environment path
- start powershell in the script directory
- run `./PixelFlasher.ps1` and follow the prompts.

Optionally pass arguments to the script to specify the various options.
See `./PixelFlasher.ps1 -help` for usage.