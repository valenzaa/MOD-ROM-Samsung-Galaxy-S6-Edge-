# MOD-ROM-Samsung-Galaxy-S6-Edge-
### MOD ROM บน Samsung Galaxy S6 Edge+ (รุ่น G928C) บน Ubuntu 22.04
### แนวทางการรูทและติดตั้ง MOD ROM บน Samsung Galaxy S6 Edge+ (รุ่น G928C) บน Ubuntu 22.04:
## ขั้นตอนที่ 1: ติดตั้งเครื่องมือที่จำเป็น

```
sudo apt update
sudo apt upgrade
```

## ติดตั้ง ADB และ Fastboot:
`sudo apt install adb fastboot`

## ติดตั้ง Heimdall (โปรแกรมที่ใช้แทน Odin บน Linux):

`sudo apt install heimdall-flash`

## ติดตั้งไลบรารีที่จำเป็น:

`sudo apt install libusb-1.0-0`

## ขั้นตอนที่ 2: ปลดล็อก Bootloader
        โหลด twrp-3.1.0-0-twrp.img
        วางไฟล์ twrp-3.1.0-0-twrp.img ในไดเรกทอรีโฮมของคุณ
        **ตำแหน่ง twrp-3.1.0-0-twrp.img ต้องเข้าถึงง่าย บั๊กได้**
    เปิดใช้งาน Developer Options บนโทรศัพท์ของคุณ:
        ไปที่ Settings > About phone > Software information > แตะที่ Build number 7 ครั้ง
        กลับไปที่ Settings > Developer options > เปิดใช้งาน OEM unlocking และ USB debugging
    เข้าสู่ Download Mode:
        ปิดเครื่องโทรศัพท์ของคุณ
        กดและถือปุ่ม Volume Down + Home + Power พร้อมกันจนกว่าจะเห็นหน้าจอเตือน
        กดปุ่ม Volume Up เพื่อเข้าสู่ Download mode
    ปลดล็อก Bootloader:
        เชื่อมต่อโทรศัพท์ของคุณกับคอมพิวเตอร์ผ่าน USB
        เปิดเทอร์มินัลแล้วรันคำสั่ง:

        
```
heimdall flash --RECOVERY twrp-3.1.0-0.img --no-reboot
# heimdall flash --RECOVERY /home/backswv/Downloads/twrp-3.1.0-0-twrp.img --no-reboot
```
```(base) backswv@unix-backswv:~$ heimdall flash --RECOVERY /home/backswv/Downloads/twrp-3.1.0-0-twrp.img --no-reboot
Heimdall v2.0.2

Copyright (c) 2010-2017 Benjamin Dobell, Glass Echidna
https://www.glassechidna.com.au/

This software is provided free of charge. Copying and redistribution is
encouraged.

If you appreciate this software and you would like to support future
development please consider donating:
https://www.glassechidna.com.au/donate/

Initialising connection...
Detecting device...
Claiming interface...
Initialising protocol...
Resetting device...
Protocol initialisation successful.

Beginning session...

Some devices may take up to 2 minutes to respond.
Please be patient!

Session begun.

Downloading device's PIT file...
PIT file download successful.

Uploading RECOVERY
100%
RECOVERY upload successful

Ending session...
Releasing device interface...

(base) backswv@unix-backswv:~$ *
```

ดึงสาย 
ลดเสียง-ปิดเครื่อง ค้างไว้
ไปกินอาหารฟุตสตรีท 
**น่าจะ Magisk ตามไปเลย เพราะใช้คำสั่ง --no-reboot รอบหน้าเทสใหม่
       
## ขั้นตอนที่ 3: แฟลช Custom Recovery (TWRP)
 

    ดาวน์โหลด ** ubuntu13.04-heimdall-frontend_1.4.0-0_amd64.deb 
[ubuntu13.04-heimdall-frontend_1.4.0-0_amd64.deb](https://https://bitbucket.org/benjamin_dobell/heimdall/downloads/ubuntu13.04-heimdall-frontend_1.4.0-0_amd64.deb)

`sudo dpkg -i ~/Downloads/ubuntu13.04-heimdall-frontend_1.4.0-0_amd64.deb`

        รีบูตโทรศัพท์ของคุณเข้าสู่ Download mode
        ในเทอร์มินัล รันคำสั่ง:
`heimdall flash --RECOVERY twrp-3.4.0-0.img --usb-log-level debug`


    บูตเข้าสู่ Recovery Mode:
        หลังจากแฟลช ให้กดและถือปุ่ม **Volume Up + Home + Power** พร้อมกันเพื่อเข้าสู่ TWRP recovery 
        
        
ขั้นตอนที่ 4: รูทอุปกรณ์

    ดาวน์โหลดไฟล์ Magisk ZIP ล่าสุด:
        จากหน้า [GitHub releases](https://https://github.com/topjohnwu/Magisk/releases) ของ [Magisk](https://github.com/topjohnwu/Magisk/releases)
    ติดตั้ง Magisk:
        คัดลอกไฟล์ Magisk ZIP ไปยังโทรศัพท์ของคุณ
        ใน TWRP ให้แตะ Install แล้วเลือกไฟล์ Magisk ZIP
        สไลด์เพื่อยืนยันการแฟลชและติดตั้ง Magisk
    รีบูต:
        รีบูตโทรศัพท์หลังการติดตั้ง
        
ขั้นตอนที่ 5: ติดตั้ง MOD ROM

    ดาวน์โหลด MOD ROM ที่ต้องการสำหรับ G928C:
        ตรวจสอบว่าเข้ากันได้กับรุ่นอุปกรณ์ของคุณ
    โอน ROM ไปยังโทรศัพท์ของคุณ:
        เชื่อมต่อโทรศัพท์กับคอมพิวเตอร์แล้วโอนไฟล์ ROM ZIP
    ติดตั้ง MOD ROM:
        บูตเข้าสู่ TWRP recovery
        แตะ Wipe > Advanced Wipe แล้วเลือก Dalvik/ART Cache, System, Data, และ Cache
        สไลด์เพื่อทำการลบข้อมูล
        กลับไปที่เมนูหลัก แตะ Install แล้วเลือกไฟล์ ROM ZIP
        สไลด์เพื่อยืนยันการแฟลชและติดตั้ง ROM
    รีบูต:
        รีบูตโทรศัพท์หลังการติดตั้ง การบูตครั้งแรกอาจใช้เวลานาน
        
# หมายเหตุ:

    สำรองข้อมูลสำคัญ: การรูทและติดตั้ง ROM จะลบข้อมูลของคุณ ตรวจสอบให้แน่ใจว่าคุณได้สำรองข้อมูลสำคัญไว้แล้ว
    การยกเลิกประกัน: การรูทและการแฟลช ROM จะทำให้การรับประกันของคุณสิ้นสุดลง
    ทำด้วยความระมัดระวัง: ทำตามขั้นตอนอย่างระมัดระวังเพื่อหลีกเลี่ยงการทำให้โทรศัพท์ของคุณเสียหาย
    
# คำแนะนำ:

    สำหรับ Android เวอร์ชัน 9.0 ขึ้นไป ให้ใช้ twrp-3.4.0-0 หรือ twrp-3.3.1-0
    สำหรับ Android เวอร์ชันระหว่าง 8.0 ถึง 9.0 twrp-3.2.1-0 เหมาะสม
    สำหรับ Android เวอร์ชันระหว่าง 7.0 ถึง 8.0 twrp-3.1.0-0 เหมาะสม
    สำหรับ Android เวอร์ชันระหว่าง 6.0 ถึง 7.0 twrp-3.0.2-0 เหมาะสม
    สำหรับ Android เวอร์ชันระหว่าง 5.0 ถึง 6.0 twrp-2.8.5.0 เหมาะสม
    
https://dl.twrp.me/twrp/twrp-3.4.0-0-twrp.img.html
### twrp-3.4.0-0-twrp.img
### 4.5M
### 2022-10-09 21:53:52 UTC
    
  
https://dl.twrp.me/twrp/twrp-3.3.1-0-twrp.img.html
### twrp-3.3.1-0-twrp.img
### 4.4M
### 2019-05-21 11:22:44 UTC
    
  
https://dl.twrp.me/twrp/twrp-3.2.1-0-twrp.img.html
### twrp-3.2.1-0-twrp.img
### 4.6M
### 2019-04-12 11:28:09 UTC
    
  
https://dl.twrp.me/twrp/twrp-3.1.0-0-twrp.img.html
### twrp-3.1.0-0-twrp.img
### 4.6M
### 2017-12-01 09:24:07 UTC
    
  
https://dl.twrp.me/twrp/twrp-3.0.2-0-twrp.img.html
### twrp-3.0.2-0-twrp.img
### 4.5M
### 2017-02-01 00:21:48 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.8.0.1-twrp.img.html
### twrp-2.8.0.1-twrp.img
### 2.9M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.8.5.0-twrp.img.html
### twrp-2.8.5.0-twrp.img
### 3.3M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.8.0.0-twrp.img.html
### twrp-2.8.0.0-twrp.img
### 2.9M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.7.0.1-twrp.img.html
### twrp-2.7.0.1-twrp.img
### 2.5M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.6.0.0-twrp.img.html
### twrp-2.6.0.0-twrp.img
### 2.3M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.6.3.0-twrp.img.html
### twrp-2.6.3.0-twrp.img
### 2.7M
### 2015-03-14 18:31:55 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.7.0.0-twrp.img.html
### twrp-2.7.0.0-twrp.img
### 2.5M
### 2015-03-14 18:31:54 UTC
    
  
https://dl.twrp.me/twrp/twrp-2.5.0.0-twrp.img.html
### twrp-2.5.0.0-twrp.img
### 2.2M
### 2015-03-14 18:31:54 UTC    
  
    
twrp-3.4.0-0:

    Compatible Android Versions: Android 9.0 (Pie) to Android 10.0 (Q)
    Release Date: October 9, 2022

twrp-3.3.1-0:

    Compatible Android Versions: Android 9.0 (Pie) to Android 10.0 (Q)
    Release Date: May 21, 2019

twrp-3.2.1-0:

    Compatible Android Versions: Android 8.0 (Oreo) to Android 9.0 (Pie)
    Release Date: April 12, 2019

twrp-3.1.0-0:

    Compatible Android Versions: Android 7.0 (Nougat) to Android 8.0 (Oreo)
    Release Date: December 1, 2017

twrp-3.0.2-0:

    Compatible Android Versions: Android 6.0 (Marshmallow) to Android 7.0 (Nougat)
    Release Date: February 1, 2017

twrp-2.8.0.1 to twrp-2.8.5.0:

    Compatible Android Versions: Android 5.0 (Lollipop) to Android 6.0 (Marshmallow)
    Release Date: 2015

twrp-2.7.0.1 to twrp-2.7.0.0:

    Compatible Android Versions: Android 4.4 (KitKat) to Android 5.0 (Lollipop)
    Release Date: 2015

twrp-2.6.0.0 to twrp-2.6.3.0:

    Compatible Android Versions: Android 4.3 (Jelly Bean) to Android 4.4 (KitKat)
    Release Date: 2015

twrp-2.5.0.0:

    Compatible Android Versions: Android 4.2 (Jelly Bean) to Android 4.3 (Jelly Bean)
    Release Date: 2015

# กรณีทำผิด เกิดจากเครื่องดับ หรือเลือกไฟล์ผิด 
![1718101334782](https://github.com/valenzaa/MOD-ROM-Samsung-Galaxy-S6-Edge-/assets/144785020/576ca2eb-ee66-4771-af7f-ab69c556e768)

## เครื่องจะตอบสนองเพียง 
### การกดค้าง (ลดเสียง + ปิด) 
### และการกดค้าง ((ลดเสียง + ปิด + โฮม)+เพิ่มเสียง)
https://github.com/TeamWin/android_device_samsung_zenltetmo
## ถ้าบิดดิ้งไม่ได้ใช้ไฟล์ 2 .img .ตัวใน 
### mkbootimg -> mkboot.img
### dtb.img
```
heimdall flash --RECOVERY mkboot.img
heimdall flash --RECOVERY dtb.img
```
## ติดตั้งไปใน download mode 
## เครื่องจะเข้าแต่ download mode ให้ใช้
### SAMFW.COM_SM-G928C_THL_G928CXXU5CVG4_fac.zip
https://samfw.com/firmware/SM-G928C/THL/G928CXXU5CVG4
## ใช้ odin ลงทีละ1 และ ลง 4 อย่างพร้อมกัน 
### จะกลับมาเป็น twrp-2.8.5.0 
ขั้นตอนหลักดังนี้:

    เตรียมสิ่งแวดล้อม:
        ติดตั้งแพ็กเกจที่จำเป็น: sudo apt-get install build-essential libncurses-dev bison flex libssl-dev libelf-dev

    ดาวน์โหลดเคอร์เนลซอร์ส:
        คลอนซอร์สโค้ดจาก GitHub: git clone -b twrp-6.0 https://github.com/jcadduono/android_kernel_samsung_universal7420.git
        เข้าสู่ไดเรกทอรี: cd android_kernel_samsung_universal7420

    คอนฟิกเคอร์เนล:
        ใช้คำสั่ง: make menuconfig

    คอมไพล์เคอร์เนล:
        รันคำสั่ง: make -j$(nproc)
        ติดตั้งโมดูล: sudo make modules_install

    ติดตั้งเคอร์เนล:
        คัดลอกเคอร์เนลใหม่ไปยังไดเรกทอรีบูต: sudo cp arch/arm64/boot/Image.gz /boot/vmlinuz-custom
        อัปเดต Bootloader
ขั้นตอนการติดตั้ง e/OS R และ NikGapps บน Samsung Galaxy S6 Edge+ (G928C)

    ดาวน์โหลดไฟล์ที่จำเป็น:
        e-1.15-r-20230909-UNOFFICIAL-zeroltexx.zip
        NikGapps-full-arm64-13-20240420-signed.zip
        TWRP Recovery

    ติดตั้ง TWRP Recovery:
        ใช้ Odin เพื่อแฟลช TWRP:
            เปิด Odin บนคอมพิวเตอร์ของคุณ.
            เชื่อมต่ออุปกรณ์ในโหมด Download (ปิดเครื่องแล้วกดปุ่ม Volume Down + Home + Power พร้อมกัน).
            เลือกไฟล์ .tar ภายใต้ช่อง AP ใน Odin และคลิก Start เพื่อเริ่มการแฟลช.

    เข้าสู่ TWRP Recovery:
        ปิดเครื่อง.
        เปิดเครื่องในโหมด TWRP Recovery โดยกดปุ่ม Volume Up + Home + Power พร้อมกัน.

    การ Wipe ข้อมูล:
        ใน TWRP เลือก Wipe > Advanced Wipe และเลือก Dalvik/ART Cache, System, Data, และ Cache จากนั้นเลื่อนแถบเพื่อยืนยันการลบข้อมูล.

    ติดตั้ง e/OS R ROM:
        กลับไปที่หน้าหลักของ TWRP และเลือก Install.
        เลือกไฟล์ e-1.15-r-20230909-UNOFFICIAL-zeroltexx.zip และเลื่อนแถบเพื่อยืนยันการติดตั้ง.

    ติดตั้ง NikGapps:
        กลับไปที่หน้าหลักของ TWRP และเลือก Install อีกครั้ง.
        เลือกไฟล์ NikGapps-full-arm64-13-20240420-signed.zip และเลื่อนแถบเพื่อยืนยันการติดตั้ง.

    รีบูทเครื่อง:
        เลือก Reboot > System เพื่อบูทเข้าสู่ระบบปฏิบัติการใหม่.

หมายเหตุ:

    ตรวจสอบให้แน่ใจว่าอุปกรณ์มีการชาร์จแบตเตอรี่อย่างน้อย 50% ขึ้นไป.
    สำรองข้อมูลสำคัญก่อนที่จะทำการติดตั้งเพื่อป้องกันการสูญหายของข้อมูล.
    หลังจากการติดตั้งครั้งแรก อาจใช้เวลานานกว่าปกติในการบูทเครื่อง.

หากคุณมีคำถามเพิ่มเติมหรือพบปัญหาในระหว่างการติดตั้ง คุณสามารถหาข้อมูลเพิ่มเติมหรือขอความช่วยเหลือจากชุมชนผู้ใช้และผู้พัฒนาที่ XDA Developers.
