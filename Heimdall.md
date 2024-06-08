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
