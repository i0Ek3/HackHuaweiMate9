# Hack HUAWEI Mate 9

## TL;DR

- if you want to play with geek, don't use huawei's smartphone
- get the unlock code: buy the service on Taobao.com with 20~30RMB or calculate the code by this project, you can change the base number to find it out rapidly
- unlock the phone: use [PotatoNV](https://github.com/mashed-potatoes/PotatoNV) and the code to unlock your device or run command `fastboot oem unlock your_code`
    - our huawei mate9's code is: 9750470288808895
    - if you want to use PotatoNV, please check [this post](https://github.com/mashed-potatoes/PotatoNV/issues/20) and use file Huawei_drivers_testpoint.zip to shortcruit your smartphone [ps: I got failed]
- flash the twrp recovery, ref [here](https://forum.xda-developers.com/t/recovery-27-09-2017-3-1-1-0-twrp-for-the-huawei-mate-9-hi3660.3515617/), files you can find in /tools
- flash treble GSI ROM, please go to [here](https://github.com/phhusson/treble_experimentations/releases) to download treble rom

## Issues in Upgrade
 
The purpose of unlock the phone is flash third ROM what I liked. But when TaoBao seller unlock the phone, the system version is back to EMUI 5.0(Android 7.0), this version is so lag and unsafety and he is never told me this version cannot upgrade again, I can't believe this, so I try to upgrade it to the latest version EMUI 8.0, but I got failed whatever. Fuck it, I find the solution what I can find on the internet, and the last I found one, [this post](https://club.huawei.com/thread-17096431-1-1.html?extra=filter%3Dtypeid%26typeid%3D4298%26page%3D1) let me get into the next level, the twrp recovery flash message told me I flashed successful, but my phone dead: she is never boot again. `>_<!!!!` I don't why, she is so quiet without any response when I press the power button. So sad! The operation of cause this problem is when twrp flash done, I do not reboot it into recovery mode, in this suation I just press volume+ and power to get it, and then she got black screen without any response. So be careful.  

Relife today through taobao seller.

## Summary

After closing the official EMUI website,
which allowed you to retrieve the code to unlock the bootloader of Huawei/Honor phones, 
here is a python script to test many possible codes.

It uses a bruteforce method, based on the IMEI identifier to generate unlocking codes.

This will most likely only work on European versions, 
because these only use numbers in the bootloader unlock code.
Actually Chinese version also wrok yet.

I've only had the opportunity to test it on European versions:
- Honor  5x 8x and 9x
- Honor  view 10 and 20
- Honor  10 lite
- Huawei p20 lite
- Huawei Y6 2019
- Huawei p30
- Huawei Mate 9


## Instructions

1. Enable developer options in Android.
1. Enable USB debugging in Android.
1. Connect your device to the computer and launch the script.

    Windows:
    ```batch
    C:\WINDOWS\system32> python unlock.py
    ```
    Linux/macOS:
    ```shell
    $ python3 unlock.py
    ```
    The device is going to ask for authorisation, which you'll have to allow.  
    Please also check the checkbox "Always allow from this computer".
1. Wait for the application to detect your device. The device info should appear.
1. Enter the (first) IMEI.
1. Start the bruteforce.  
    (this may take several ~~hours~~ days) so get a cup of coffee ☕ and go to sleep. 💫 
1. If the correct code is found, your phone will either be instantly unlocked or prompt you with an additional confirmation dialogue on the target device.  
    (all data will be erased on unlock!)


## FAQ & Troubleshooting

**- The application doesn't work. Is there anything I should have installed?**  
Yes, it was developed in python so it needs it to run, version 3. You can install the latest version from [here](https://www.python.org/downloads/) or by using Windows Store.

**- The app on Windows doesn't detect my device even though it's connected and USB debugging is enabled. What could be the issue?**  
Windows most likely doesn't recognise your device in ADB mode. Install the universal ADB drivers from [here](http://dl.adbdriver.com/upload/adbdriver.zip), reboot your PC and try again.

**- My phone reboots every 5 failed attempts**  
We are aware of this and have implemented an automatic intentional reboot after 4 attempts.  
You can manually enable this feature in the code.  
The script will also automatically detect this behaviour. For this to work reliably, please check the checkbox "Always allow from this computer" in the adb dialogue.

**- The script displays "command invalid"**  
Huawei has removed the unlock command in EMUI 10.  
Downgrade your software and try again.
