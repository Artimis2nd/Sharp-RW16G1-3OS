# 🪟 การติดตั้ง Windows บน Sharp RW-16G1

เอกสารนี้อธิบายขั้นตอนการติดตั้ง Windows บนเครื่อง **Sharp RW-16G1**  
ซึ่งเป็นส่วนหนึ่งของโปรเจกต์ **Sharp RW-16G1 – 3OS (Windows + Bliss OS + Batocera)**

> ⚠️ ควรอ่านเอกสาร [ข้อมูลฮาร์ดแวร์และข้อจำกัด](hardware.md)  
> และ [การจัดพาร์ทิชัน](partitioning.md) ก่อนเริ่มขั้นตอนนี้

---

## 🎯 เป้าหมายของขั้นตอนนี้

- ติดตั้ง Windows ให้เป็น **ระบบหลัก (Primary OS)**
- ใช้โหมด **UEFI**
- เตรียมระบบให้สามารถใช้งานร่วมกับ  
  - Bliss OS (Android-x86)  
  - Batocera (Linux-based)
- ไม่ให้ Windows เขียนทับ bootloader ในภายหลัง

---

## 💾 เวอร์ชัน Windows ที่แนะนำ

- ✅ **Windows 10 (64-bit)**
  - รองรับไดรเวอร์ได้ดีที่สุด
  - ทำงานเสถียรบนสเปกของ RW-16G1
- ❌ Windows 11  
  - ไม่แนะนำ (ข้อจำกัดด้าน TPM / CPU)

---

## 🧰 สิ่งที่ต้องเตรียม

- USB Flash Drive ขนาด **8 GB ขึ้นไป**
- Windows ISO (แนะนำ Windows 10 64-bit)
- โปรแกรมสร้าง USB เช่น:
  - Rufus
  - Media Creation Tool
- คีย์บอร์ด USB (แนะนำ)
- แหล่งจ่ายไฟที่เสถียร

---

## 🔧 การสร้าง USB ติดตั้ง Windows (UEFI)

### ตั้งค่าใน Rufus
- Boot selection: `Windows ISO`
- Partition scheme: `GPT`
- Target system: `UEFI (non-CSM)`
- File system: `FAT32`

> ⚠️ ห้ามใช้โหมด Legacy / MBR

---

## ⚙️ การตั้งค่า BIOS / UEFI

ก่อนเริ่มติดตั้ง Windows:

- ปิด **Secure Boot**
- เปิด **UEFI Boot**
- ปิด Legacy / CSM (ถ้ามี)
- ตั้งค่า USB Boot เป็นลำดับแรก

---

## 🚀 ขั้นตอนการติดตั้ง Windows

1. เสียบ USB Windows
2. เปิดเครื่อง → เลือก Boot จาก USB (UEFI)
3. เมื่อเข้า Windows Setup:
   - เลือกภาษา / เวลา / คีย์บอร์ด
4. กด **Install Now**
5. เลือก **Custom: Install Windows only**
6. เลือกพาร์ทิชันที่เตรียมไว้สำหรับ Windows  
   (ดูอ้างอิงจาก `partitioning.md`)
7. **ห้ามลบ EFI System Partition**
8. เริ่มการติดตั้ง และรอจนเสร็จสมบูรณ์

---

## 🔁 หลังติดตั้งเสร็จ (สำคัญมาก)

### ตรวจสอบสิ่งต่อไปนี้
- Windows บูตได้ปกติ
- มี EFI Partition อยู่
- ยังไม่มีการติดตั้ง rEFInd (ขั้นตอนถัดไป)

### สิ่งที่ “ยังไม่ต้องทำ”
- ❌ ยังไม่ต้องลง Bliss OS
- ❌ ยังไม่ต้องลง Batocera
- ❌ ยังไม่ต้องปรับ boot menu

---

## ⚠️ ข้อควรระวัง

- Windows Update บางครั้งอาจเขียนทับค่า boot
- แนะนำ:
  - ปิด Fast Startup
  - หลีกเลี่ยงการ repair boot ด้วย Windows โดยไม่จำเป็น

---

## 📌 หมายเหตุเพิ่มเติม

- Windows ควรติดตั้งเป็น **OS แรกเสมอ**
- เพื่อให้ระบบอื่นสามารถ “แทรกตัว” เข้าร่วม boot ได้ง่ายกว่า
- rEFInd จะถูกติดตั้งภายหลังเพื่อจัดการ Multi-Boot

---

## ➡️ คลิปสอนลง Windows
👉 https://youtu.be/TJnpN5N3bQo?si=UZBp_cxsbjxGOjQH

---

> Windows คือฐาน  
> Linux และ Android คือแขนง  
> ถ้าฐานมั่นคง ทั้งระบบจะอยู่ร่วมกันได้อย่างสงบ
