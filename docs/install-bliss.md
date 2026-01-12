# 🤖 การติดตั้ง Bliss OS (Android-x86) บน Sharp RW-16G1

เอกสารนี้อธิบายขั้นตอนการติดตั้ง **Bliss OS (Android-x86)**  
เพื่อใช้งานเป็นระบบ Android ควบคู่กับ Windows และ Batocera  
ในโปรเจกต์ **Sharp RW-16G1 – 3OS**

> ⚠️ ต้องติดตั้ง Windows เสร็จแล้วก่อน  
> ดูเอกสาร: [ติดตั้ง Windows](install-windows.md)

---

## 🎯 เป้าหมายของขั้นตอนนี้

- ติดตั้ง Android แบบ **Native (ไม่ใช่ Emulator)**
- ใช้งานร่วมกับ Windows ได้
- แยกพาร์ทิชันชัดเจน ไม่รบกวนกัน
- เตรียมระบบให้ใช้ rEFInd เป็นตัวเลือกบูตภายหลัง

---

## 🧠 ทำไมเลือก Bliss OS v14

- รองรับ Android 11 (เสถียร)
- รองรับอุปกรณ์จอสัมผัสได้ดี
- มีชุมชนและเอกสารค่อนข้างครบ
- ทำงานร่วมกับ UEFI ได้ดีกว่า Android-x86 รุ่นเก่า

> ❌ ไม่แนะนำ LineageOS / PhoenixOS สำหรับเครื่องรุ่นนี้  
> เนื่องจากปัญหาไดรเวอร์และการอัปเดต

---

## 💾 เวอร์ชันที่แนะนำ

- **Bliss OS v14.x (x86_64)**
- Variant: `GMS` (ถ้าต้องการ Play Store)
- Kernel มาตรฐาน (ไม่ต้อง custom)

---

## 🧰 สิ่งที่ต้องเตรียม

- USB Flash Drive ≥ 8 GB
- Bliss OS ISO
- โปรแกรมสร้าง USB (แนะนำ Rufus)
- คีย์บอร์ด USB

---

## 🔧 การสร้าง USB ติดตั้ง Bliss OS

### ตั้งค่าใน Rufus
- Boot selection: `Bliss OS ISO`
- Partition scheme: `GPT`
- Target system: `UEFI (non-CSM)`
- File system: `FAT32`

> ⚠️ ห้ามใช้โหมด Legacy / MBR

---

## ⚙️ การตั้งค่า BIOS / UEFI (ย้ำอีกครั้ง)

- Secure Boot: ❌ ปิด
- Boot Mode: ✅ UEFI
- Legacy / CSM: ❌ ปิด

---

## 🚀 ขั้นตอนการติดตั้ง Bliss OS

1. เสียบ USB Bliss OS
2. บูตจาก USB (UEFI)
3. เลือกเมนู  
   **Installation – Install Bliss OS to harddisk**
4. เลือกดิสก์ที่ติดตั้ง (ตรวจสอบให้ถูกลูก)
5. เลือกพาร์ทิชันที่เตรียมไว้สำหรับ Bliss OS  
   (ดู `partitioning.md`)
6. เลือก **Do not format**  
   (หรือ format เป็น ext4 หากพาร์ทิชันว่าง)
7. ตอบ:
   - Install GRUB? → **No**
   - Install EFI GRUB? → **No**
8. เลือก **Read/Write** (RW)

---

## 🔁 หลังติดตั้งเสร็จ

- รีสตาร์ทเครื่อง
- ตรวจสอบว่า:
  - Bliss OS เข้าได้
  - หน้าจอสัมผัสทำงาน
  - Wi-Fi / เสียง ทำงาน (บางจุดอาจต้องปรับภายหลัง)

---

## ➡️ ขั้นตอนถัดไป

เมื่อติดตั้ง Bliss OS เรียบร้อยแล้ว  
ให้ไปต่อที่:

👉 [ติดตั้ง Batocera](install-batocera.md)

---
