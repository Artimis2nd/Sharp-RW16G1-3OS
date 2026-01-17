# 🧭 การตั้งค่า rEFInd Bootloader (ศูนย์กลางของระบบ 3 OS)

เอกสารนี้อธิบายการตั้งค่า **rEFInd** เพื่อใช้เป็นตัวกลางจัดการการบูตของระบบ:

- Windows
- Bliss OS (Android-x86)
- Batocera Linux

บนเครื่อง **Sharp RW-16G1**

---

## 🎯 แนวคิดหลักของการใช้ rEFInd

- rEFInd ทำหน้าที่ **แสดงทางเลือกการบูต**
- ไม่ลบ bootloader ของระบบใด
- ไม่บังคับลำดับใคร
- ทุกระบบยังคงโครงสร้างของตัวเอง
---

## 🧠 โครงสร้างที่ทำทั้งหมด ก่อนติดตั้ง rEFInd

### 🖥 Windows
- ติดตั้ง Windows เป็นลำดับแรก
- เมื่อติดตั้งเสร็จ จะมี Windows Boot Manager อยู่แล้ว
- อยู่ใน EFI System Partition

### 🤖 Bliss OS
- ติดตั้ง Bliss OS แบบ **ไม่ใช้ GRUB**
- ระหว่างการติดตั้ง ให้เลือกตามมนี้:
  - Install GRUB? → **NO**
  - Install EFI GRUB? → **NO**
- เมื่อติดตั้งเสร็จ จะยังไม่มี boot entry ของตัวเอง
- ต้องให้ rEFInd ช่วยชี้ไฟล์ kernel

### 🎮 Batocera
- ติดตั้งแบบ **Copy Partition**
- เมื่อติดตั้งเสร็จ จะมี boot file ของตัวเองครบ
- rEFInd ตรวจพบอัตโนมัติได้ทันที

---

## 🚀 ขั้นตอนการติดตั้ง rEFInd
### 💾 เครื่องมือที่ใช้

  1. โปรแกรม Explorer++ Version 1.4.0 หรือใหม่กว่า (แบบที่เป็น 64Bit) จากหน้าเว็บทางการ

https://explorerplusplus.com/ 👈 โหลดที่ลิ้งค์นี้

<img width="480" height="300" alt="image" src="https://github.com/user-attachments/assets/b59d2f6f-7964-4256-a7e2-e4f009b6fa63" />


  2. ไฟล์ติดตั้ง rEFInd 0.14.2 หรือใหม่กว่า (แบบที่เป็น binary zip) จากหน้าเว็บทางการ

https://sourceforge.net/projects/refind/files/0.14.2/ 👈 โหลดที่ลิ้งค์นี้

<img width="640" height="380" alt="image" src="https://github.com/user-attachments/assets/670d3c5d-2ee7-4043-a8f2-dd464d71dac1" />

### ขั้นตอนที่ 2: เตรียมไฟล์ rEFInd
แตกไฟล์ rEFInd 0.14.2 ออกมา คุณจะเห็นโฟลเดอร์ที่ชื่อ refind (ข้างในจะมีไฟล์ refind_x64.efi และอื่นๆ)

### ขั้นตอนที่ 3: เปิดพาร์ทิชันระบบ (EFI)
เนื่องจาก Windows ล็อกพาร์ทิชันนี้ไว้ เราต้องใช้คำสั่งเรียกมันออกมา:

กดปุ่มแว่นขยาย พิมพ์ CMD คลิกขวาเลือก Run as Administrator

พิมพ์คำสั่ง: mountvol S: /S แล้วกด Enter (ตอนนี้พาร์ทิชัน EFI จะถูกจำลองเป็นไดรฟ์ S: ในระบบ)

### ขั้นตอนที่ 4: ก๊อปปี้ไฟล์ลงไป (ใช้ Explorer++)
Windows Explorer ปกติจะเข้าไดรฟ์ S: ไม่ได้ ต้องใช้ตัวช่วย:

เปิดโปรแกรม Explorer++ ด้วยการ คลิกขวา เลือก Run as Administrator

ไปที่ไดรฟ์ S: แล้วเข้าไปในโฟลเดอร์ EFI

สร้างโฟลเดอร์ใหม่ชื่อว่า refind (ถ้ามีของเก่าอยู่แล้ว ให้ลบทิ้งแล้วสร้างใหม่ได้เลย)

copy ไฟล์จากเครื่องเรา (จากขั้นตอนที่ 2) ทั้งหมดในโฟลเดอร์ refind ไปวางไว้ที่ S:\EFI\refind\

### ขั้นตอนที่ 5: ตั้งชื่อไฟล์คอนฟิก (จุดที่คนมักลืม)
ในหน้า Explorer++ (ที่อยู่ในไดรฟ์ S:) ให้มองหาไฟล์ชื่อ refind.conf-sample

คลิกขวาแล้ว Rename (เปลี่ยนชื่อ) ให้เหลือแค่ refind.conf เท่านั้น (ไฟล์นี้จะเป็นตัวเก็บ Code บูต 3 ระบบที่เราเขียนกันครับ)

### ขั้นตอนที่ 6: สั่งให้คอมพิวเตอร์รู้จัก rEFInd (จดทะเบียนบูต)
กลับไปที่หน้า CMD (Admin) ที่เปิดค้างไว้ แล้วพิมพ์คำสั่งนี้:

    bcdedit /set "{bootmgr}" path \EFI\refind\refind_x64.efi

กด Enter ถ้าขึ้นว่า The operation completed successfully แสดงว่าไบออสจะรู้จักเมนูนี้แล้ว

### ขั้นตอนที่ 7: เขียน Code บูต 3 ระบบ
เปิดไฟล์ S:\EFI\refind\refind.conf (ผ่าน Explorer++ และเปิดด้วย Notepad) แล้วเลื่อนไปล่างสุด ก๊อปปี้ Code นี้ไปวาง

    # --- ตั้งค่าการสแกน EFI (แสกนและแสดงปุ่มตามนี้ external=อุปกรณ์ต่อพ่วงจาก USB ,optical=CD,manual=คำสั่งเมนูที่เราเขียน ตามลำดับ)
    scanfor external,optical,manual
    
    # --- ตั้งค่าปุ่มเครื่องมือ (BIOS) --- (จะแสดง reboot=ปุ่มรีสตาร์ท,shutdown=ชัทดาว์น,firmware=ไบออส ตามลำดับ)
    showtools reboot, shutdown, firmware
    
    # --- โค้ดสั่งให้โชว์เมนู Windows 10 --- (จะขึ้นเป็นลำดับที่1)
    menuentry "Windows 10" {
        icon \EFI\refind\icons\os_win10.png
        loader \EFI\Microsoft\Boot\bootmgfw.efi
    }
    
    # --- โค้ดสั่งให้โชว์เมนู Bliss OS --- (จะขึ้นเป็นลำดับที่2)
    menuentry "Bliss OS 14" {
        icon \EFI\refind\icons\os_gg.png
        loader \EFI\Bliss14\kernel
        initrd \EFI\Bliss14\initrd.img
        options "root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/android-2024-10-12"
    }
    
    # --- โค้ดสั่งให้โชว์เมนู Batocera --- (จะขึ้นเป็นลำดับที่3)
    menuentry "Batocera" {
        icon \EFI\refind\icons\os_game.png
        volume "Batocera"
        loader \EFI\batocera\grubx64.efi
    }

---

## 📝 สรุปโค้ด refind.conf ด้านบน แบบเข้าใจง่าย แบ่งเป็น 3 ส่วนหลักครับ:

### 1. การควบคุมหน้าตาเมนู (บรรทัดบนสุด)
**scanfor external,optical,manual**: สั่งให้ rEFInd โชว์ไอคอนเฉพาะ:
- แฟลชไดรฟ์ที่เสียบใหม่ (external)
- แผ่น CD (optical)
- เมนูที่เราเขียนเองด้านล่าง (manual)
ผลลัพธ์: จะไม่มีไอคอนขยะที่ระบบสแกนเจอเองโผล่มาให้รกตา

**showtools reboot, shutdown, firmware**: โชว์ปุ่มทางลัดด้านล่าง ได้แก่ ปุ่มรีสตาร์ท, ปิดเครื่อง และปุ่มกดเข้าหน้า BIOS (Firmware)

### 2. รายละเอียดปุ่มบูต (Menu Entry)
ในแต่ละส่วนจะมีโครงสร้างเหมือนกันคือ:
- **menuentry**: ชื่อที่จะโชว์บนหน้าจอ
- **icon**: รูปไอคอนที่จะใช้ (ต้องระบุที่อยู่ไฟล์รูปให้ถูก)
- **loader**: ไฟล์หลักที่ใช้ในการรันระบบนั้นๆ
- **initrd**: ไฟล์เริ่มต้นระบบ (เฉพาะ Android/Linux)
- **options**: คำสั่งพิเศษ (เช่น การตั้งค่าหน้าจอหรือสิทธิ์ Root)

### ⚠️ จุดสำคัญที่ต้องระวัง (อาจทำให้บูตไม่ติด):
- เครื่องหมาย Slash (\ vs /):

  ในโค้ดของคุณใช้ \ (Backslash) ซึ่งบางเวอร์ชันของ rEFInd อาจจะอ่านไม่ออก
  
  แนะนำให้เปลี่ยนเป็น / (Forward Slash) ทั้งหมด เพื่อความชัวร์ (เช่น /EFI/refind/icons/...)

- ที่อยู่ไฟล์ (Path):
  
  **Bliss OS**: ตรวจดูว่าโฟลเดอร์ชื่อ Bliss14 จริงหรือไม่ (โฟลเดอร์จริงอาจชื่อ android-2024-10-12)
  
  **Batocera**: ตรวจดูว่าในพาร์ทิชัน Batocera ของคุณ มีไฟล์ตามที่ระบุจริงไหม
  
  **เลข Volume**: ถ้าใส่ชื่อ volume "Batocera" แล้วไม่ติด ให้ลองเปลี่ยนเป็นเลขพาร์ทิชันแทน เช่น volume 6 (ตามลำดับ Batocera ใน Disk Management)

---

## ➡️ ขั้นตอนถัดไป

เมื่อ rEFInd ทำงานครบทั้ง 3 OS แล้ว:

👉 [แก้ปัญหาเบื้องต้น](troubleshooting.md)  
👉 [บทเรียนที่ได้จากโปรเจกต์](lessons-learned.md)

---
