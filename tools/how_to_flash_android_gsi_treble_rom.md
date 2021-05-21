# Steps to Flash Android 11 by GSI Treble ROM

- 1. base 9.0.x and unlock the phone
    - use command `fastboot oem get-bootinfo` to check it
    - use command `fastboot oem unlock unlock_code` to unlock the phone 
- 2. download gsi treble rom from GitHub and rename it to system.img
- 3. reboot to bootloader mode then run command `fastboot flash system system.img`
- 4. reboot to recovery mode and reset factory
- 5. reboot
