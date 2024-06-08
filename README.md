# MOD-ROM-Samsung-Galaxy-S6-Edge-
MOD ROM บน Samsung Galaxy S6 Edge+ (รุ่น G928C) บน Ubuntu 22.04
แนวทางการรูทและติดตั้ง MOD ROM บน Samsung Galaxy S6 Edge+ (รุ่น G928C) บน Ubuntu 22.04:
ขั้นตอนที่ 1: ติดตั้งเครื่องมือที่จำเป็น

    อัพเดตระบบของคุณ:

    bash

sudo apt update
sudo apt upgrade

ติดตั้ง ADB และ Fastboot:

bash

sudo apt install adb fastboot

ติดตั้ง Heimdall (โปรแกรมที่ใช้แทน Odin บน Linux):

bash

sudo apt install heimdall-flash

ติดตั้งไลบรารีที่จำเป็น:

bash

    sudo apt install libusb-1.0-0

ขั้นตอนที่ 2: ปลดล็อก Bootloader

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

        bash

        adb reboot bootloader
        fastboot oem unlock

ขั้นตอนที่ 3: แฟลช Custom Recovery (TWRP)

    ดาวน์โหลด TWRP Recovery Image สำหรับ G928C:
        ไปที่เว็บไซต์ทางการของ TWRP และดาวน์โหลดไฟล์ที่เหมาะสมกับอุปกรณ์ของคุณ

    แฟลช TWRP Recovery:
        วางไฟล์ TWRP image ในไดเรกทอรีโฮมของคุณ
        รีบูตโทรศัพท์ของคุณเข้าสู่ Download mode
        ในเทอร์มินัล รันคำสั่ง:

        bash

        heimdall flash --RECOVERY twrp-image-file.img

    บูตเข้าสู่ Recovery Mode:
        หลังจากแฟลช ให้กดและถือปุ่ม Volume Up + Home + Power พร้อมกันเพื่อเข้าสู่ TWRP recovery

ขั้นตอนที่ 4: รูทอุปกรณ์

    ดาวน์โหลดไฟล์ Magisk ZIP ล่าสุด:
        จากหน้า GitHub releases ของ Magisk

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

หมายเหตุ:

    สำรองข้อมูลสำคัญ: การรูทและติดตั้ง ROM จะลบข้อมูลของคุณ ตรวจสอบให้แน่ใจว่าคุณได้สำรองข้อมูลสำคัญไว้แล้ว
    การยกเลิกประกัน: การรูทและการแฟลช ROM จะทำให้การรับประกันของคุณสิ้นสุดลง
    ทำด้วยความระมัดระวัง: ทำตามขั้นตอนอย่างระมัดระวังเพื่อหลีกเลี่ยงการทำให้โทรศัพท์ของคุณเสียหาย

  
    
# Recommendations:

    For Android versions 9.0 and above, use twrp-3.4.0-0 or twrp-3.3.1-0.
    For Android versions between 8.0 and 9.0, twrp-3.2.1-0 is suitable.
    For Android versions between 7.0 and 8.0, twrp-3.1.0-0 is suitable.
    For Android versions between 6.0 and 7.0, twrp-3.0.2-0 is suitable.
    For Android versions between 5.0 and 6.0, twrp-2.8.5.0 is suitable.
    
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
