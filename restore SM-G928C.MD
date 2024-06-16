Load https://samfw.com/firmware/SM-G928C/THL/G928CXXU5CVG4
คลายไฟล์ เปลี่ยนชื่อโฟเดอร์หลังคลายไฟล SM-G928C_THL ไม่ยาวมากจะไม่เออเร่อ
ไปหน้า ดาวโหลดโหมด
ปิดเครื่อง กด 3 ปุ่มค้างพร้อมกัน ปุ่มโฮม ปุ่มลดเสียง ปุ่มเปิด
ตัวอย่างการรีเฟิร์มแวร์โดยใช้คอมมาน
```
heimdall flash --BOOT boot.img --SYSTEM system.img --RECOVERY recovery.img --BOOTLOADER sboot.bin --CM cm.bin --RADIO modem.bin --CACHE cache.img --HIDDEN hidden.img --verbose
```
เมสเซสจากคอมมาน
```
backswv@unix-backswv:~/Desktop/Samsung_heimdall/SM-G928C_THL$ heimdall flash --BOOT boot.img --SYSTEM system.img --RECOVERY recovery.img --BOOTLOADER sboot.bin --CM cm.bin --RADIO modem.bin --CACHE cache.img --HIDDEN hidden.img --verbose
Heimdall v2.0.2
Uploading SYSTEM
100%
HIDDEN upload successful
Ending session...
Rebooting device...
Releasing device interface...

backswv@unix-backswv:~/Desktop/Samsung_heimdall/SM-G928C_THL$ 
```
การใช้สคริปจะต้องอยู่ในหน้าดาวโหลดโหมด
นี่คือสคริปต์ที่ปรับปรุงแล้ว:

```

#!/bin/bash

# Step 0: ลบโฟลเดอร์หรือเคลียร์ข้อมูลเก่า (ถ้ามี)
echo "Cleaning up old files..."
rm -rf tmp/heimdall
# rm -rf tmp
mkdir -p tmp/heimdall

# Step 1: ดาวน์โหลดไฟล์ PIT
echo "Downloading PIT file..."
heimdall download-pit --output tmp/heimdall.pit --verbose

# Step 2: ตรวจสอบพาร์ติชันใน PIT
echo "Checking PIT partitions..."
heimdall print-pit --file tmp/heimdall.pit --verbose > tmp/pit_info.txt

# Display the PIT information
cat tmp/pit_info.txt

# Step 3: สร้างโฟลเดอร์และแตกไฟล์
echo "Creating directories and extracting files..."
unzip SAMFW.COM_SM-G928C_THL_G928CXXU5CVG4_fac.zip -d tmp/

# Extract the .tar.md5 files
for file in tmp/*.tar.md5; do
    echo "Extracting $file..."
    7z x $file -o./tmp/heimdall/
done

# Step 4: รันคำสั่ง Heimdall โดยตรวจสอบค่าจาก PIT
# Display the list of extracted files
echo "Extracted files:"
ls tmp/heimdall

# Run Heimdall flash with the appropriate files
echo "Flashing device with Heimdall..."
heimdall flash \
--BOOT tmp/heimdall/boot.img \
--SYSTEM tmp/heimdall/system.img \
--RECOVERY tmp/heimdall/recovery.img \
--BOOTLOADER tmp/heimdall/sboot.bin \
--CM tmp/heimdall/cm.bin \
--RADIO tmp/heimdall/modem.bin \
--CACHE tmp/heimdall/cache.img \
--HIDDEN tmp/heimdall/hidden.img \
--verbose

echo "Flashing completed."

# Step 5: ลบทุกอย่างเมื่อเสร็จสิ้นการทำงาน
echo "Cleaning up..."
rm -rf tmp

echo "All done. Temporary files have been removed."

# End of script
```
การใช้งานสคริปต์:

    บันทึกสคริปต์นี้ในไฟล์ชื่อ flash_device.sh

    ทำให้สคริปต์สามารถรันได้:

```

chmod +x flash_device.sh
```
รันสคริปต์:

```

    ./flash_device.sh
```
หมายเหตุ:

    สคริปต์นี้จะทำการลบโฟลเดอร์ tmp/heimdall 
