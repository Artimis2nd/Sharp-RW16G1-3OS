# การใช้งาน rEFInd Theme & Background

เอกสารนี้อธิบายการใช้งาน **Theme ของ rEFInd**  
รวมถึงการแก้ไข **Background image และ Icon** อย่างถูกต้อง  
สำหรับเครื่องที่ใช้ rEFInd เป็น Boot Manager

อ้างอิง:
- rEFInd Official Guide คู่มือจากเวปหลัก
  https://www.rodsbooks.com/refind/
- rEFInd-minimal Theme ตัวอย่าง ธีม
  https://github.com/EvanPurkhiser/rEFInd-minimal

---

## 🧠 สรุปแนวคิดสำคัญ (เข้าใจให้ตรงก่อน)
- rEFInd **ไม่ได้ใช้ background image เดี่ยว ๆ**
- ภาพพื้นหลัง, ไอคอน, ฟอนต์ → เป็นส่วนหนึ่งของ **Theme**
- ถ้าใช้ Theme → การเปลี่ยนภาพ = แก้ไฟล์ใน Theme นั้น

> ถ้าพยายามตั้ง `background` ใน `refind.conf`  
> แต่ Theme ถูกเปิดใช้งานอยู่  
> → ค่าใน Theme จะถูกใช้แทนเสมอ

---

## 📦 การติดตั้ง Theme: rEFInd-minimal

### 1️⃣ ดาวน์โหลด Theme
ดาวน์โหลดจาก:
https://github.com/EvanPurkhiser/rEFInd-minimal

แตกไฟล์ จะได้โฟลเดอร์:rEFInd-minimal


---

### 2️⃣ คัดลอก Theme ไปไว้ใน rEFInd
คัดลอกโฟลเดอร์ `rEFInd-minimal` ไปไว้ที่: EFI\refind\themes\


โครงสร้างที่ถูกต้อง:
```
EFI
└── refind
├── refind.conf
└── themes
└── rEFInd-minimal
├── theme.conf
├── background.png
├── icons
└── fonts
```

---

### 3️⃣ เปิดใช้งาน Theme
แก้ไขไฟล์:EFI\refind\refind.conf

เพิ่มบรรทัดนี้เข้าไปในส่วนท้ายสุด:
```
include themes/rEFInd-minimal/theme.conf
```
บันทึกไฟล์ แล้วรีบูต

---

### 4️⃣ การปรับแต่ง Theme
### 🖼 การเปลี่ยน Background Image
- แทนที่ภาพด้วยไฟล์ชื่อเดียวกันคือ:background.png
- อยู่ในโฟลเดอร์:EFI\refind\themes\rEFInd-minimal\
- ไม่ต้องแก้ refind.conf เพิ่ม เพราะ Theme จะโหลด background นี้โดยอัตโนมัติ
### 🎨 การแก้ไขไอคอน (Icons)
- ไอคอนทั้งหมดอยู่ที่:EFI\refind\themes\rEFInd-minimal\icons\
- หลักการเดียวกับ background.png คือการแทนที่ไฟล์ด้วยชื่อไฟล์ต้องตรงกับของเดิม
- แนะนำให้ใช้ไฟล์ .png ขนาดควรใกล้เคียงกับของเดิม เพื่อไม่ให้ UI เพี้ยน

ตัวอย่าง
```
icons
├── os_windows.png
├── os_linux.png
├── os_mac.png
└── tool_shell.png
```
แค่แทนที่ไฟล์ → รีบูต → เห็นผลทันที

### ⚠ ข้อควรระวัง
- แก้ไฟล์ผิด → rEFInd อาจไม่แสดงเมนู
- ควรมี Batocera / Live USB เป็นทางกู้เสมอ
- ถ้าเข้า rEFInd ไม่ได้: บูตจาก Batocera กด F1 เข้า EFI แล้วแก้ refind.conf หรือ Theme ได้ทันที

---

