Load 
https://samfw.com/firmware/SM-G928C/THL/G928CXXU5CVG4
คลายไฟล์ เปลี่ยนชื่อโฟเดอร์หลังคลายไฟล SM-G928C_THL ไม่ยาวมากจะไม่เออเร่อ
ไปหน้า ดาวโหลดโหมด detect compatible download-mode
ปิดเครื่อง กด 3 ปุ่มค้างพร้อมกัน ปุ่มโฮม ปุ่มลดเสียง ปุ่มเปิด 
เมื่อถึงหน้าจอฟ้า Warning กดปุ่มเพิ่มเสียง
ขั้นตอนเข้า download-mode นี้ เมื่อรันสคริป จะต้องเข้า 2 ครั้ง สคริปจะรอหากคุณเข้าไม่ทัน
สคริปจะคลายไฟล์ และโหลด pit จากเครื่อง คุณต้องกดเข้า download-mode อีกครั้ง กดปิดเครื่อง นั่นหล่ะ
เมื่อคุณเข้า download-mode ครั้งที่สอบ ดูว่าสคริปคลายไฟล์เสร็จหรือยัง ถ้าเสร็จแล้ว กด Enter เพื่อให้สคริปรันคำสั่งติดตั้ง
ตัวอย่างการรีเฟิร์มแวร์โดยใช้คอมมาน โดยใช้ SAMFW.COM_SM-G928C_THL_G928CXXU5CVG4_fac.zip และคริปนี้ วางไว้ตำแหน่งเดียวกัน
```
#!/bin/bash

# ฟังก์ชันสำหรับการตรวจสอบโหมดดาวน์โหลด
check_download_mode() {
  echo "Checking if the device is in download mode..."
  while true; do
    if heimdall detect; then
      echo "Device detected in download mode."
      break
    else
      echo "Device not detected. Please put the device in download mode and press Enter to retry."
      read -r
    fi
  done
}

# ฟังก์ชันสำหรับการแสดงข้อผิดพลาดและออกจากสคริปต์
error_exit() {
  echo "$1" 1>&2
  exit 1
}

MODEL="G928C"

# Step 0: ลบโฟลเดอร์หรือเคลียร์ข้อมูลเก่า (เฉพาะโฟลเดอร์ heimdall)
echo "Cleaning up old files..."
rm -rf tmp/heimdall
mkdir -p tmp/heimdall

# Step 1: ตรวจสอบโหมดดาวน์โหลดก่อนดาวน์โหลด PIT
check_download_mode

# Step 2: ดาวน์โหลดไฟล์ PIT
echo "Downloading PIT file..."
if ! heimdall download-pit --output tmp/${MODEL}_heimdall.pit --verbose; then
  error_exit "Failed to download PIT file. Ensure the device is in download mode."
fi

# Step 3: ตรวจสอบพาร์ติชันใน PIT
echo "Checking PIT partitions..."
if ! heimdall print-pit --file tmp/${MODEL}_heimdall.pit --resume --verbose > tmp/${MODEL}_pit_info.txt; then
  error_exit "Failed to print PIT file. Ensure the device is in download mode."
fi

# Display the PIT information
cat tmp/${MODEL}_pit_info.txt

# Step 4: สร้างโฟลเดอร์และแตกไฟล์
echo "Creating directories and extracting files..."
unzip -o SAMFW.COM_SM-G928C_THL_G928CXXU5CVG4_fac.zip -d tmp/ || error_exit "Failed to unzip firmware file."

# Extract the .tar.md5 files
for file in tmp/*.tar.md5; do
  echo "Extracting $file..."
  if ! 7z x "$file" -o./tmp/heimdall/; then
    error_exit "Failed to extract $file."
  fi
done

# ตรวจสอบว่าไฟล์ที่จำเป็นทั้งหมดมีอยู่หรือไม่
required_files=("boot.img" "system.img" "recovery.img" "sboot.bin" "cm.bin" "modem.bin" "cache.img" "hidden.img" "userdata.img")
for file in "${required_files[@]}"; do
  if [ ! -f "tmp/heimdall/$file" ]; then
    error_exit "Required file $file not found. Please download and extract the firmware files correctly."
  fi
done

# Display the list of extracted files
echo "Extracted files:"
ls tmp/heimdall

# Step 5: ตรวจสอบโหมดดาวน์โหลดก่อนทำการแฟลช
check_download_mode

# Step 6: รันคำสั่ง Heimdall flash
echo "Flashing device with Heimdall..."
if ! heimdall flash \
  --BOOT tmp/heimdall/boot.img \
  --SYSTEM tmp/heimdall/system.img \
  --RECOVERY tmp/heimdall/recovery.img \
  --BOOTLOADER tmp/heimdall/sboot.bin \
  --CM tmp/heimdall/cm.bin \
  --RADIO tmp/heimdall/modem.bin \
  --CACHE tmp/heimdall/cache.img \
  --HIDDEN tmp/heimdall/hidden.img \
  --USERDATA tmp/heimdall/userdata.img \
  --verbose; then
  error_exit "Flashing failed. Ensure the device is in download mode."
fi

echo "Flashing completed."

# Step 7: ลบเฉพาะโฟลเดอร์ heimdall เมื่อเสร็จสิ้นการทำงาน
echo "Cleaning up..."
rm -rf tmp/heimdall

echo "All done. Temporary files have been removed."

# End of script

```
การใช้งานสคริปต์:
    บันทึกสคริปต์นี้ในไฟล์ชื่อ flash_device.sh
    ทำให้สคริปต์สามารถรันได้:

```
chmod +x flash_device.sh
./flash_device.sh
```
หมายเหตุ:

    สคริปต์นี้จะใช้ชื่อไฟล์ tmp/${MODEL}_heimdall.pit และ tmp/${MODEL}_pit_info.txt โดยที่ ${MODEL} จะเป็นชื่อรุ่นของอุปกรณ์ (ในกรณีนี้คือ G928C)
    สคริปต์จะลบเฉพาะโฟลเดอร์ tmp/heimdall ก่อนและหลังการแฟลชเฟิร์มแวร์
    สคริปต์จะตรวจสอบโหมดดาวน์โหลดก่อนและหลังการดาวน์โหลด PIT และการแฟลช
