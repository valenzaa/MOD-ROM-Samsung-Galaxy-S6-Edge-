Heimdall เป็นเครื่องมือสำหรับแฟลชเฟิร์มแวร์ไปยังอุปกรณ์ Samsung ที่ใช้โหมดดาวน์โหลด นี่คือคำแปลของคำสั่งและคำอธิบายการใช้งานอย่างละเอียด:
คำสั่งพื้นฐาน:

plaintext

การใช้งาน: `heimdall <การกระทำ> <อาร์กิวเมนต์ของการกระทำ>`

รายละเอียดของการกระทำแต่ละอย่าง:
การกระทำ: **close-pc-screen**

อาร์กิวเมนต์:

    --verbose
    --no-reboot
    --resume
    --stdout-errors
    --usb-log-level <none/error/warning/debug>

คำอธิบาย: พยายามกำจัดหน้าจอ "connect phone to PC"
หมายเหตุ: การใช้ --no-reboot จะทำให้อุปกรณ์ยังคงอยู่ในโหมดดาวน์โหลดหลังจากการกระทำเสร็จสิ้น หากคุณต้องการดำเนินการอื่นในโหมดดาวน์โหลด คุณต้องระบุ --resume สำหรับการกระทำถัดไป
การกระทำ: detect

อาร์กิวเมนต์:

    --verbose
    --stdout-errors
    --usb-log-level <none/error/warning/debug>

คำอธิบาย: ตรวจสอบว่าอุปกรณ์ในโหมดดาวน์โหลดสามารถถูกตรวจจับได้หรือไม่

ตัวอย่างการใช้งาน:

bash

`heimdall detect --verbose`

การกระทำ: download-pit

อาร์กิวเมนต์:

    --output <filename>
    --verbose
    --no-reboot
    --stdout-errors
    --usb-log-level <none/error/warning/debug>

คำอธิบาย: ดาวน์โหลดไฟล์ **PIT** ของอุปกรณ์ที่เชื่อมต่อไปยังไฟล์ที่ระบุ
หมายเหตุ: การใช้ **--no-reboot** จะทำให้อุปกรณ์ยังคงอยู่ในโหมดดาวน์โหลดหลังจากการกระทำเสร็จสิ้น หากคุณต้องการดำเนินการอื่นในโหมดดาวน์โหลด คุณต้องระบุ **--resume** สำหรับการกระทำถัดไป

ตัวอย่างการใช้งาน:

bash

`heimdall download-pit --output my_device.pit --verbose`

การกระทำ: **flash**

อาร์กิวเมนต์:

    [--<partition name> <filename> ...]
    [--<partition identifier> <filename> ...]
    --pit <filename>
    --verbose
    --no-reboot
    --resume
    --stdout-errors
    --usb-log-level <none/error/warning/debug>

คำอธิบาย: แฟลชไฟล์เฟิร์มแวร์หนึ่งไฟล์หรือมากกว่าไปยังโทรศัพท์ของคุณ ชื่อพาร์ติชัน (หรือรหัส) สามารถหาได้โดยการรันคำสั่ง print-pit T-Flash mode ใช้เพื่อแฟลช SD-card ที่ใส่อยู่แทนที่หน่วยความจำภายใน ใช้ **--skip-size-check** เพื่อละเว้นการตรวจสอบขนาดไฟล์ว่าตรงกับพาร์ติชันที่ระบุหรือไม่

หมายเหตุ: การใช้ **--no-reboot** จะทำให้อุปกรณ์ยังคงอยู่ในโหมดดาวน์โหลดหลังจากการกระทำเสร็จสิ้น หากคุณต้องการดำเนินการอื่นในโหมดดาวน์โหลด คุณต้องระบุ **--resume** สำหรับการกระทำถัดไป
คำเตือน: หากคุณกำลัง **repartitioning** ขอแนะนำให้ระบุไฟล์ทั้งหมดที่คุณมี

ตัวอย่างการใช้งาน:

bash

`heimdall flash --RECOVERY recovery.img --no-reboot`

การกระทำ: help

คำอธิบาย: แสดงการช่วยเหลือสำหรับ Heimdall

ตัวอย่างการใช้งาน:

bash

`heimdall help`

การกระทำ: info

คำอธิบาย: แสดงข้อมูลเกี่ยวกับ Heimdall

ตัวอย่างการใช้งาน:

bash

`heimdall info`

การกระทำ: print-pit

อาร์กิวเมนต์:

    [--file <filename>]
    --verbose
    --no-reboot
    --stdout-errors
    --usb-log-level <none/error/warning/debug>

คำอธิบาย: แสดงเนื้อหาของไฟล์ PIT ในรูปแบบที่มนุษย์อ่านได้ หากไม่ได้ระบุชื่อไฟล์ Heimdall จะดึงไฟล์ PIT จากอุปกรณ์ที่เชื่อมต่อ
หมายเหตุ: การใช้ **--no-reboot** จะทำให้อุปกรณ์ยังคงอยู่ในโหมดดาวน์โหลดหลังจากการกระทำเสร็จสิ้น หากคุณต้องการดำเนินการอื่นในโหมดดาวน์โหลด คุณต้องระบุ **--resume** สำหรับการกระทำถัดไป

ตัวอย่างการใช้งาน:

bash

`heimdall print-pit --file my_device.pit --verbose`

การกระทำ: version

คำอธิบาย: แสดงหมายเลขเวอร์ชันของโปรแกรมนี้

ตัวอย่างการใช้งาน:

bash

`heimdall version`

ตัวอย่างการใช้งาน Heimdall:

    ตรวจสอบการเชื่อมต่อของอุปกรณ์ในโหมดดาวน์โหลด:

    bash

`heimdall detect --verbose`

ดาวน์โหลดไฟล์ PIT จากอุปกรณ์:

bash

`heimdall download-pit --output my_device.pit --verbose`

แฟลชไฟล์ recovery.img ไปยังพาร์ติชัน RECOVERY:

bash

`heimdall flash --RECOVERY recovery.img --no-reboot`

แสดงเนื้อหาของไฟล์ PIT:

bash

`heimdall print-pit --file my_device.pit --verbose`


(base) backswv@unix-backswv:~/Downloads$ heimdall print-pit --file my_device.pit --verbose
Heimdall v2.0.2

Copyright (c) 2010-2017 Benjamin Dobell, Glass Echidna
https://www.glassechidna.com.au/

This software is provided free of charge. Copying and redistribution is
encouraged.

If you appreciate this software and you would like to support future
development please consider donating:
https://www.glassechidna.com.au/donate/

--- PIT Header ---
Entry Count: 22
Unknown string: COM_TAR2
CPU/bootloader tag: LSI7420
Logic unit count: 4


--- Entry #0 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 80
Attributes: 2 (STL Read-Only)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 0
Partition Block Count: 1024
File Offset (Obsolete): 1
File Size (Obsolete): 0
Partition Name: BOOTLOADER
Flash Filename: sboot.bin
FOTA Filename: 


--- Entry #1 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 90
Attributes: 2 (STL Read-Only)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 0
Partition Block Count: 1024
File Offset (Obsolete): 2
File Size (Obsolete): 0
Partition Name: CM
Flash Filename: cm.bin
FOTA Filename: 


--- Entry #2 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 1
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 6
Partition Block Count: 1536
File Offset (Obsolete): 3
File Size (Obsolete): 0
Partition Name: CPEFS
Flash Filename: 
FOTA Filename: 


--- Entry #3 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 70
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 6
Partition Block Count: 2
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: PIT
Flash Filename: -
FOTA Filename: 


--- Entry #4 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 71
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 8
Partition Block Count: 256
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: MD5HDR
Flash Filename: md5.img
FOTA Filename: 


--- Entry #5 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 1
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 1024
Partition Block Count: 1024
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: BOTA0
Flash Filename: -
FOTA Filename: 


--- Entry #6 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 2
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 2048
Partition Block Count: 1024
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: BOTA1
Flash Filename: -
FOTA Filename: 


--- Entry #7 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 3
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 3072
Partition Block Count: 5120
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: EFS
Flash Filename: efs.img
FOTA Filename: 


--- Entry #8 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 4
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 8192
Partition Block Count: 2048
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: PARAM
Flash Filename: param.bin
FOTA Filename: 


--- Entry #9 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 5
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 10240
Partition Block Count: 7168
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: BOOT
Flash Filename: boot.img
FOTA Filename: 


--- Entry #10 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 6
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 17408
Partition Block Count: 8704
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: RECOVERY
Flash Filename: recovery.img
FOTA Filename: 


--- Entry #11 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 7
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 26112
Partition Block Count: 2048
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: OTA
Flash Filename: -
FOTA Filename: 


--- Entry #12 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 8
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 28160
Partition Block Count: 10752
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: RADIO
Flash Filename: modem.bin
FOTA Filename: 


--- Entry #13 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 9
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 38912
Partition Block Count: 256
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: TOMBSTONES
Flash Filename: tombstones.img
FOTA Filename: 


--- Entry #14 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 10
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 39168
Partition Block Count: 256
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: DNT
Flash Filename: dnt.ssw
FOTA Filename: 


--- Entry #15 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 11
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 39424
Partition Block Count: 192
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: PERSISTENT
Flash Filename: 
FOTA Filename: 


--- Entry #16 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 12
Attributes: 5 (Read/Write)
Update Attributes: 1 (FOTA)
Partition Block Size/Offset: 39616
Partition Block Count: 64
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: STEADY
Flash Filename: 
FOTA Filename: 


--- Entry #17 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 13
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 39680
Partition Block Count: 2304
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: PERSDATA
Flash Filename: persdata.img
FOTA Filename: 


--- Entry #18 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 14
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 41984
Partition Block Count: 1024000
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: SYSTEM
Flash Filename: system.img
FOTA Filename: 


--- Entry #19 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 15
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 1065984
Partition Block Count: 51200
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: CACHE
Flash Filename: cache.img
FOTA Filename: 


--- Entry #20 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 16
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 1117184
Partition Block Count: 38400
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: HIDDEN
Flash Filename: hidden.img
FOTA Filename: 


--- Entry #21 ---
Binary Type: 0 (AP)
Device Type: 8 (UFS)
Identifier: 17
Attributes: 5 (Read/Write)
Update Attributes: 5 (FOTA)
Partition Block Size/Offset: 1155584
Partition Block Count: 0
File Offset (Obsolete): 0
File Size (Obsolete): 0
Partition Name: USERDATA
Flash Filename: userdata.img
FOTA Filename: remained


(base) backswv@unix-backswv:~/Downloads$ 


