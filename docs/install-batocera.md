# 🎮 การติดตั้ง Batocera บน Sharp RW-16G1 (วิธี Copy Partition)

เอกสารนี้อธิบายขั้นตอนการติดตั้ง **Batocera Linux**  
บนเครื่อง **Sharp RW-16G1** โดยใช้วิธี  
**Copy Partition จาก USB มายัง SSD ปลายทาง**

วิธีนี้ถูกเลือกใช้เพื่อ:
- ความเสถียรของระบบ Multi-Boot
- ไม่กระทบ Windows และ Bliss OS
- จัดการไฟล์ ROM / BIOS ผ่าน Windows ได้สะดวก

---

## ⚠️ ข้อกำหนดก่อนเริ่ม

ต้องดำเนินการตามขั้นตอนเหล่านี้แล้ว:
- ติดตั้ง Windows เรียบร้อย
- ติดตั้ง Bliss OS เรียบร้อย
- วางแผนพาร์ทิชันสำหรับ Batocera ไว้แล้ว

อ้างอิง:
- [การจัดพาร์ทิชัน](partitioning.md)

---

## 🎯 แนวคิดของวิธีนี้ (สำคัญ)

Batocera **ไม่ถูกติดตั้งแบบ Installer** ลง SSD โดยตรง  
แต่ใช้แนวคิด:

- พาร์ทิชันระบบ → คัดลอกตรงจาก USB
- พาร์ทิชันข้อมูลผู้ใช้ → สร้างใหม่เอง (exFAT)

ผลลัพธ์:
- ระบบเหมือน Batocera บน USB ทุกประการ
- USERDATA อ่าน/เขียนได้จาก Windows ทันที

---

## 💾 เวอร์ชัน Batocera ที่ใช้

- Batocera Linux (x86_64 – Stable)
- Image ทางการ (.img.gz)
- โหมด UEFI

---

## 🧰 เครื่องมือที่ใช้

- USB Flash Drive ≥ 16 GB
- Batocera Image
- โปรแกรมเขียน Image:
  - balenaEtcher หรือ Rufus (DD mode)
- **MiniTool Partition Wizard (บน Windows)**

---

## 🔧 เตรียม USB Batocera

1. ใช้ balenaEtcher หรือ Rufus (DD mode)
2. เขียน Batocera Image ลง USB
3. เสร็จแล้ว **ไม่ต้องแก้ไขพาร์ทิชันใด ๆ บน USB**

---

## 🚀 ขั้นตอนการติดตั้ง Batocera ลง SSD

---

### 1️⃣ บูตจาก USB Batocera

- เสียบ USB Batocera
- เปิดเครื่อง และเลือก Boot แบบ **UEFI**
- รอจนเข้าเมนูหลักของ Batocera ได้

> ขั้นตอนนี้เพื่อยืนยันว่า  
> USB Batocera ทำงานถูกต้องก่อนคัดลอก

---

### 2️⃣ ตรวจสอบพาร์ทิชัน Batocera บน USB

บน USB จะมีพาร์ทิชันหลัก 2 ส่วน:
- `BATOCERA` → พาร์ทิชันระบบ (BOOT)
- `BATOCERA_DATA` → พาร์ทิชันข้อมูลผู้ใช้

---

### 3️⃣ คัดลอกพาร์ทิชันระบบ BATOCERA ไปยัง SSD

ใช้ **MiniTool Partition Wizard** บน Windows

1. เปิด MiniTool Partition Wizard
2. เลือกไดรฟ์ USB ที่มี Batocera
3. เลือกพาร์ทิชัน:
   - ชื่อ: `BATOCERA`
4. เลือกเมนู **Copy Partition Wizard**
5. เลือกปลายทางเป็น:
   - พื้นที่ว่างสุดท้ายของ SSD Sharp RW-16G1
6. ยืนยันการ Copy และ Apply

📌 วิธีนี้จะคัดลอก:
- โครงสร้างระบบทั้งหมด
- Boot flag และ label เดิม
- ค่า filesystem โดยไม่เปลี่ยนแปลง

> ⚠️ ห้าม format ใหม่  
> ⚠️ ห้ามเปลี่ยนชื่อพาร์ทิชัน `BATOCERA`

---

### 4️⃣ สร้างพาร์ทิชัน USERDATA บน SSD Sharp

เพื่อความสะดวกในการจัดการไฟล์ผ่าน Windows:

1. ใช้ MiniTool Partition Wizard
2. สร้างพาร์ทิชันใหม่ในพื้นที่ถัดจาก `BATOCERA`
3. ตั้งค่า:
   - File system: **exFAT**
   - Label: `USERDATA` (หรือ `BATOCERA_DATA`)
4. Apply การเปลี่ยนแปลง

📌 เหตุผลที่เลือก exFAT:
- Windows อ่าน/เขียนได้ทันที
- ไม่ต้องบูต Linux เพื่อย้ายไฟล์
- เหมาะกับไฟล์ ROM จำนวนมาก

---

### 5️⃣ คัดลอกข้อมูล USERDATA จาก USB

1. เปิดพาร์ทิชัน `BATOCERA_DATA` บน USB
2. คัดลอกไฟล์และโฟลเดอร์ทั้งหมด
3. วางทับลงในพาร์ทิชัน USERDATA บน SSD Sharp

โฟลเดอร์สำคัญ:
- `/roms`
- `/bios`
- `/saves`
- `/screenshots`

---

### 6️⃣ ทดสอบการบูต Batocera จาก SSD

- รีสตาร์ทเครื่อง
- เลือกบูต Batocera
- ตรวจสอบว่า:
  - ระบบเข้าได้ปกติ
  - ROM ถูกตรวจพบ
  - ไม่มี error เรื่อง BIOS

---

## ⚠️ ข้อควรระวังสำคัญ

- ❌ ห้ามใช้ Batocera Installer ลง SSD โดยตรง
- ❌ ห้ามเปลี่ยนชื่อพาร์ทิชัน `BATOCERA`
- ❌ ห้ามให้ Windows สร้าง EFI ใหม่ทับของเดิม

---

## 🧠 หมายเหตุจากการใช้งานจริง

> วิธีนี้อาจดูเหมือน “อ้อม”  
> แต่ให้ผลลัพธ์ที่เสถียรที่สุด  
> สำหรับระบบที่ต้องอยู่ร่วมกับหลาย OS

---

## ➡️ ขั้นตอนถัดไป

เมื่อ Batocera ทำงานเรียบร้อยแล้ว  
ให้ไปต่อที่:

👉 [ตั้งค่า rEFInd](bootloader-refind.md)
