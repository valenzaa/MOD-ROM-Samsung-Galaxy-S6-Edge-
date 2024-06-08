fastboot เป็นเครื่องมือที่ใช้ในการจัดการพาร์ติชันและแฟลชเฟิร์มแวร์บนอุปกรณ์ Android ในโหมดบูตโหลดเดอร์ นี่คือคำแปลของคำสั่งและคำอธิบายการใช้งานอย่างละเอียด:
คำสั่งพื้นฐาน:

plaintext

การใช้งาน: fastboot [ตัวเลือก...] คำสั่ง...

รายละเอียดของคำสั่งแต่ละอย่าง:
การแฟลช:

update ZIP

    แฟลชทุกพาร์ติชันจากแพ็คเกจ update.zip

flashall

    แฟลชทุกพาร์ติชันจาก $ANDROID_PRODUCT_OUT
    บนอุปกรณ์ A/B, พาร์ติชันที่แฟลชจะถูกตั้งค่าเป็นใช้งาน
    อิมเมจสำรองอาจถูกแฟลชไปยังพาร์ติชันที่ไม่ได้ใช้งาน

flash PARTITION [FILENAME]

    แฟลชพาร์ติชันที่กำหนด โดยใช้อิมเมจจาก $ANDROID_PRODUCT_OUT ถ้าไม่มีการระบุไฟล์

ตัวอย่างการใช้งาน:

bash

fastboot flash boot boot.img

คำสั่งพื้นฐาน:

devices [-l]

    แสดงรายการอุปกรณ์ในโหมดบูตโหลดเดอร์ (-l: แสดงพร้อมเส้นทางอุปกรณ์)

getvar NAME

    แสดงค่าตัวแปรบูตโหลดเดอร์ที่กำหนด

reboot [bootloader]

    รีบูตอุปกรณ์

ตัวอย่างการใช้งาน:

bash

fastboot devices
fastboot reboot bootloader

การล็อก/ปลดล็อก:

flashing lock|unlock

    ล็อก/ปลดล็อกพาร์ติชันสำหรับการแฟลช

flashing lock_critical|unlock_critical

    ล็อก/ปลดล็อกพาร์ติชัน 'critical' ของบูตโหลดเดอร์

flashing get_unlock_ability

    ตรวจสอบว่าสามารถปลดล็อกได้หรือไม่ (1: ได้, 0: ไม่ได้)

ตัวอย่างการใช้งาน:

bash

fastboot flashing unlock

คำสั่งขั้นสูง:

erase PARTITION

    ลบพาร์ติชันที่กำหนด

format[
] PARTITION

    ฟอร์แมตพาร์ติชันที่กำหนด

set_active SLOT

    ตั้งค่าสล็อตที่ใช้งาน

oem [COMMAND...]

    รันคำสั่งเฉพาะของ OEM

ตัวอย่างการใช้งาน:

bash

fastboot erase userdata
fastboot format:ext4 userdata

gsi wipe|disable

    ลบหรือปิดการใช้งาน GSI (เฉพาะ fastbootd เท่านั้น)

wipe-super [SUPER_EMPTY]

    ลบพาร์ติชัน super ซึ่งจะรีเซ็ตให้มีชุดพาร์ติชันไดนามิกว่างเปล่า

create-logical-partition NAME SIZE

    สร้างพาร์ติชันลอจิคัลด้วยชื่อและขนาดที่กำหนดในพาร์ติชัน super

delete-logical-partition NAME

    ลบพาร์ติชันลอจิคัลที่มีชื่อกำหนด

resize-logical-partition NAME SIZE

    เปลี่ยนขนาดของพาร์ติชันลอจิคัลที่ระบุ

snapshot-update cancel

    บนอุปกรณ์ที่รองรับการอัปเดตแบบ snapshot-based, ยกเลิกการอัปเดตที่กำลังดำเนินการ ซึ่งอาจทำให้อุปกรณ์ไม่สามารถบูตได้จนกว่าจะรีแฟลช

snapshot-update merge

    บนอุปกรณ์ที่รองรับการอัปเดตแบบ snapshot-based, เสร็จสิ้นการอัปเดตที่กำลังดำเนินการหากอยู่ในช่วง "merging"

fetch PARTITION OUT_FILE

    ดึงอิมเมจพาร์ติชันจากอุปกรณ์

ตัวอย่างการใช้งาน:

bash

fastboot fetch recovery recovery.img

การบูตอิมเมจ:

boot KERNEL [RAMDISK [SECOND]]

    ดาวน์โหลดและบูตเคอร์เนลจาก RAM

flash
PARTITION KERNEL [RAMDISK [SECOND]]

    สร้างอิมเมจบูตและแฟลชมัน

ตัวเลือกเพิ่มเติม:

    --dtb DTB: ระบุเส้นทางไปยัง DTB สำหรับหัวอิมเมจบูตเวอร์ชัน 2
    --cmdline CMDLINE: แทนที่บรรทัดคำสั่งของเคอร์เนล
    --base ADDRESS: ตั้งค่าที่อยู่ฐานของเคอร์เนล (ค่าปริยาย: 0x10000000)
    --kernel-offset: ตั้งค่าออฟเซ็ตของเคอร์เนล (ค่าปริยาย: 0x00008000)
    --ramdisk-offset: ตั้งค่าออฟเซ็ตของแรมดิสก์ (ค่าปริยาย: 0x01000000)
    --tags-offset: ตั้งค่าออฟเซ็ตของแท็ก (ค่าปริยาย: 0x00000100)
    --dtb-offset: ตั้งค่าออฟเซ็ตของ dtb (ค่าปริยาย: 0x01100000)
    --page-size BYTES: ตั้งค่าขนาดหน้าแฟลช (ค่าปริยาย: 2048)
    --header-version VERSION: ตั้งค่าหัวเวอร์ชันอิมเมจบูต
    --os-version MAJOR[.MINOR[.PATCH]]: ตั้งค่าเวอร์ชัน OS ของอิมเมจบูต (ค่าปริยาย: 0.0.0)
    --os-patch-level YYYY-MM-DD: ตั้งค่าระดับแพตช์ความปลอดภัยของ OS สำหรับอิมเมจบูต

ตัวอย่างการใช้งาน:

bash

fastboot boot boot.img

Android Things:

stage IN_FILE

    ส่งไฟล์ที่ระบุไปยังขั้นตอนถัดไป

get_staged OUT_FILE

    เขียนข้อมูลที่ถูกจัดเก็บโดยคำสั่งล่าสุดไปยังไฟล์

ตัวอย่างการใช้งาน:

bash

fastboot stage update.zip
fastboot get_staged update.zip

ตัวเลือก:

    -w: ลบข้อมูลผู้ใช้
    -s SERIAL: ระบุอุปกรณ์ USB
    -s tcp|udp:HOST[:PORT]: ระบุอุปกรณ์เครือข่าย
    -S SIZE[K|M|G]: แบ่งออกเป็นไฟล์ที่ไม่เกิน SIZE
    --force: บังคับให้ทำการแฟลชที่อาจไม่ปลอดภัย
    --slot SLOT: ใช้ SLOT; 'all' สำหรับทั้งสองช่อง, 'other' สำหรับช่องที่ไม่ใช่ปัจจุบัน (ค่าปริยาย: ช่องที่ใช้งานอยู่ในปัจจุบัน)
    --set-active[=SLOT]: ตั้งค่าสล็อตที่ใช้งานก่อนการรีบูต
    --skip-secondary: ไม่แฟลชช่องที่สองในการแฟลชทั้งหมด/อัปเดต
    --skip-reboot: ไม่รีบูตอุปกรณ์หลังการแฟลช
    --disable-verity: ตั้งค่า disable-verity เมื่อแฟลช vbmeta
    --disable-verification: ตั้งค่า disable-verification เมื่อแฟลช vbmeta
    --fs-options=OPTION[,OPTION]: เปิดใช้งานคุณลักษณะของระบบไฟล์. OPTION รองรับ casefold, projid, compress
    --unbuffered: ไม่บัฟเฟอร์ข้อมูลเข้าและออก
    --verbose, -v: แสดงผลอย่างละเอียด
    --version: แสดงเวอร์ชัน
    --help, -h: แสดงข้อความนี้

ตัวอย่างการใช้งาน Fastboot:

    ตรวจสอบอุปกรณ์ที่เชื่อมต่อ:

    bash

fastboot devices

แฟลชพาร์ติชัน boot ด้วยไฟล์ boot.img:

bash

fastboot flash boot boot.img

ลบพาร์ติชัน userdata:

bash

fastboot erase userdata

ฟอร์แมตพาร์ติชัน userdata:

bash

fastboot format:ext4 userdata

ตั้งค่าสล็อตที่ใช้งานเป็น slot_a:

bash

fastboot set_active a

ปลดล็อกพาร์ติชันสำหรับการแฟลช:

bash

    fastboot flashing unlock

