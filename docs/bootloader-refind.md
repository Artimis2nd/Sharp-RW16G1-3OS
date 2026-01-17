# 🧭 การตั้งค่า rEFInd Bootloader (ศูนย์กลางของระบบ 3 OS)

เอกสารนี้อธิบายการตั้งค่า **rEFInd**  
เพื่อใช้เป็นตัวกลางจัดการการบูตของระบบ:

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

## 🧠 โครงสร้างก่อนติดตั้ง rEFInd

ณ จุดนี้ ระบบมีสถานะดังนี้:

### 🪟 Windows
- ติดตั้งก่อน
- มี Windows Boot Manager อยู่แล้ว
- อยู่ใน EFI System Partition
- จึงปรากฏเป็นรายการแรกโดยธรรมชาติ

### 🤖 Bliss OS
- ติดตั้งแบบ **ไม่ใช้ GRUB**
- ระหว่างติดตั้งตอบ:
  - Install GRUB? → **NO**
  - Install EFI GRUB? → **NO**
- ยังไม่มี boot entry ของตัวเอง
- ต้องให้ rEFInd ช่วยชี้ไฟล์ kernel

### 🎮 Batocera
- ติดตั้งแบบ **Copy Partition**
- มี boot file ของตัวเองครบ
- rEFInd ตรวจพบอัตโนมัติได้ทันที

---

## 💾 เครื่องมือที่ใช้

- rEFInd (เวอร์ชันเสถียร)
- Windows (สำหรับติดตั้ง rEFInd)

---

## 🚀 ขั้นตอนการติดตั้ง rEFInd

### 1️⃣ ติดตั้ง rEFInd บน Windows


---

## 📂 โครงสร้าง EFI หลังติดตั้ง บนวินโดว์

---

## 🪟 โค้ดที่ใส่เพิ่ม ใน rEFInd

    # --- ตั้งค่าการสแกน EFI 
    scanfor external,optical,manual
    
    # --- ตั้งค่าปุ่มเครื่องมือ (BIOS) ---
    showtools reboot, shutdown, firmware
    
    # --- โค้ดสั่งให้โชว์เมนู Windows 10 ---
    menuentry "Windows 10" {
        icon \EFI\refind\icons\os_win10.png
        loader \EFI\Microsoft\Boot\bootmgfw.efi
    }
    
    # --- โค้ดสั่งให้โชว์เมนู Bliss OS ---
    menuentry "Bliss OS 14" {
        icon \EFI\refind\icons\os_gg.png
        loader \EFI\Bliss14\kernel
        initrd \EFI\Bliss14\initrd.img
        options "root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/android-2024-10-12"
    }
    
    # --- โค้ดสั่งให้โชว์เมนู Batocera ---
    menuentry "Batocera" {
        icon \EFI\refind\icons\os_game.png
        volume "Batocera"
        loader \EFI\batocera\grubx64.efi
    }

---

## 🤖 การเพิ่ม Bliss OS เข้า rEFInd (ไม่มี GRUB)

เนื่องจาก Bliss OS ไม่มี GRUB  
ต้องเพิ่ม entry แบบ manual

### แนวคิด
- ชี้ตรงไปที่ kernel ของ Bliss OS
- ระบุ initrd และพาร์ทิชันให้ถูกต้อง
- ไม่สร้าง GRUB ใหม่

### ตัวอย่างแนวทาง (conceptual)

- Kernel อยู่ในพาร์ทิชัน Bliss OS
- ใช้ `menuentry` ใน `refind.conf`
- ระบุ:
  - volume
  - kernel
  - initrd
  - options

> 📌 จุดสำคัญ  
> rEFInd สามารถบูต Linux / Android ได้โดยตรง  
> **ไม่จำเป็นต้องมี GRUB**

---

## 🎮 การตรวจพบ Batocera

- Batocera มี boot file ครบถ้วน
- rEFInd ตรวจพบโดยอัตโนมัติ
- ไม่ต้องเขียน config เพิ่ม

---

## ⚠️ สิ่งที่ “ไม่ทำ” โดยตั้งใจ

- ❌ ไม่ลบ Windows Boot Manager
- ❌ ไม่ลบ GRUB (ถ้ามีจากระบบอื่น)
- ❌ ไม่แก้ EFI ของระบบใดโดยไม่จำเป็น
- ❌ ไม่ตั้ง rEFInd ให้ override ใครถาวร

---

## 🧠 บทเรียนสำคัญจากการใช้งานจริง

- Multi-Boot ที่ดี ไม่ควรมี “ผู้ชนะ”
- การไม่ลบของเดิม = เสถียรกว่า
- rEFInd ทำงานได้ดีที่สุด เมื่อ:
  - OS แต่ละตัวดูแลตัวเอง
  - rEFInd แค่เชื่อม

---

## 🔁 การจัดลำดับการบูต

- ค่าเริ่มต้น:
  1. Windows
  2. Bliss OS
  3. Batocera

- สามารถเปลี่ยนลำดับภายหลังได้  
  โดยไม่กระทบระบบใด

---

## ➡️ ขั้นตอนถัดไป

เมื่อ rEFInd ทำงานครบทั้ง 3 OS แล้ว:

👉 [แก้ปัญหาเบื้องต้น](troubleshooting.md)  
👉 [บทเรียนที่ได้จากโปรเจกต์](lessons-learned.md)

---
