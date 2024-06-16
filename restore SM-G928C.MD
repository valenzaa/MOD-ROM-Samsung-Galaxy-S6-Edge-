Load https://samfw.com/firmware/SM-G928C/THL/G928CXXU5CVG4
คลายไฟล์ เปลี่ยนชื่อโฟเดอร์หลังคลายไฟล SM-G928C_THL ไม่ยาวมากจะไม่เออเร่อ
ไปหน้า ดาวโหลดโหมด
ปิดเครื่อง กด 3 ปุ่มค้างพร้อมกัน ปุ่มโฮม ปุ่มลดเสียง ปุ่มเปิด
ตัวอย่างการรีเฟิร์มแวร์โดยใช้คอมมาน
```
heimdall flash --BOOT boot.img --SYSTEM system.img --RECOVERY recovery.img --BOOTLOADER sboot.bin --CM cm.bin --RADIO modem.bin --CACHE cache.img --HIDDEN hidden.img --verbose
```
เมสเซสจากคอมมาน
backswv@unix-backswv:~/Desktop/Samsung_heimdall/SM-G928C_THL$ heimdall flash --BOOT AP_G928C/boot.img --SYSTEM AP_G928C/system.img --RECOVERY AP_G928C/recovery.img --BOOTLOADER BL_G928C/sboot.bin --CM BL_G928C/cm.bin --RADIO CP_G928F/modem.bin --CACHE CSC_OLB_G928C/cache.img --HIDDEN CSC_OLB_G928C/hidden.img --verbose
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
      Manufacturer: "SAMSUNG"
           Product: "Gadget Serial"

            length: 18
      device class: 2
               S/N: 0
           VID:PID: 04E8:685D
         bcdDevice: 021B
   iMan:iProd:iSer: 1:2:0
          nb confs: 1

interface[0].altsetting[0]: num endpoints = 1
   Class.SubClass.Protocol: 02.02.01
       endpoint[0].address: 83
           max packet size: 0010
          polling interval: 09

interface[1].altsetting[0]: num endpoints = 2
   Class.SubClass.Protocol: 0A.00.00
       endpoint[0].address: 81
           max packet size: 0200
          polling interval: 00
       endpoint[1].address: 02
           max packet size: 0200
          polling interval: 00
Claiming interface...
Initialising protocol...
Resetting device...
Protocol initialisation successful.

Beginning session...

Some devices may take up to 2 minutes to respond.
Please be patient!

Session begun.

Downloading device's PIT file...
WARNING: Empty bulk transfer after receiving packet failed. Continuing anyway...
PIT file download successful.

Uploading BOOT
0%
4%

8%

12%

16%

20%

24%

28%

32%

36%

40%

44%

48%

53%

57%

61%

65%

69%

73%

77%

81%

85%

89%

93%

97%

100%
BOOT upload successful

Uploading SYSTEM
0%
1%

2%

3%

4%

5%

6%

7%

8%

9%

10%

11%

12%

13%

14%

15%

16%

17%

18%

19%

20%

21%

22%

23%

24%

25%

26%

27%

28%

29%

30%

31%

32%

33%

34%

35%

36%

37%

38%

39%

40%

41%

42%

43%

44%

45%

46%

47%

48%

49%

50%

51%

52%

53%

54%

55%

56%

57%

58%

59%

60%

61%

62%

63%

64%

65%

66%

67%

68%

69%

70%

71%

72%

73%

74%

75%

76%

77%

78%

79%

80%

81%

82%

83%

84%

85%

86%

87%

88%

89%

90%

91%

92%

93%

94%

95%

96%

97%

98%

99%

100%
SYSTEM upload successful

Uploading RECOVERY
0%
3%

7%

10%

14%

17%

21%

24%

28%

31%

35%

38%

42%

45%

49%

52%

56%

59%

63%

66%

70%

73%

77%

80%

84%

87%

91%

94%

98%

100%
RECOVERY upload successful

Uploading BOOTLOADER
0%
64%

100%
BOOTLOADER upload successful

Uploading CM
0%
49%

99%

100%
CM upload successful

Uploading RADIO
0%
2%

5%

8%

11%

13%

16%

19%

22%

24%

27%

30%

33%

35%

38%

41%

44%

46%

49%

52%

55%

57%

60%

63%

66%

68%

71%

74%

77%

79%

82%

85%

88%

90%

93%

96%

99%

100%
RADIO upload successful

Uploading CACHE
0%
1%

2%

3%

4%

5%

6%

7%

8%

9%

10%

11%

12%

13%

14%

15%

16%

17%

18%

19%

20%

21%

23%

24%

25%

26%

27%

28%

29%

30%

31%

32%

33%

34%

35%

36%

37%

38%

39%

40%

41%

42%

43%

45%

46%

47%

48%

49%

50%

51%

52%

53%

54%

55%

56%

57%

58%

59%

60%

61%

62%

63%

64%

65%

67%

68%

69%

70%

71%

72%

73%

74%

75%

76%

77%

78%

79%

80%

81%

82%

83%

84%

85%

86%

87%

89%

90%

91%

92%

93%

94%

95%

96%

97%

98%

99%

100%
CACHE upload successful

Uploading HIDDEN
0%
1%

2%

3%

4%

6%

7%

8%

9%

11%

12%

13%

14%

15%

17%

18%

19%

20%

22%

23%

24%

25%

27%

28%

29%

30%

31%

33%

34%

35%

36%

38%

39%

40%

41%

42%

44%

45%

46%

47%

49%

50%

51%

52%

54%

55%

56%

57%

58%

60%

61%

62%

63%

65%

66%

67%

68%

69%

71%

72%

73%

74%

76%

77%

78%

79%

81%

82%

83%

84%

85%

87%

88%

89%

90%

92%

93%

94%

95%

96%

98%

99%

100%
HIDDEN upload successful

Ending session...
Rebooting device...
Releasing device interface...

backswv@unix-backswv:~/Desktop/Samsung_heimdall/SM-G928C_THL$ 

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
