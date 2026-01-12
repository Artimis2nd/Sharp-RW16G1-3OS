# Sharp-RW16G1-3OS-Setup
คู่มือการจัดตั้งระบบ 3 OS สำหรับ Sharp RW-16G1

![800-800-Web-Sharp-Tablet-RW-16G1](https://github.com/user-attachments/assets/1a0e5236-574d-4eee-958a-60cb8bca6336)
<img width="735" height="455" alt="image" src="https://github.com/user-attachments/assets/693fbb51-02c8-4d41-9040-dac5caf090a1" />
<img width="741" height="389" alt="image" src="https://github.com/user-attachments/assets/a17ec85e-f2cb-450e-8005-b82453b8249f" />
<img width="394" height="125" alt="image" src="https://github.com/user-attachments/assets/b378fc80-afa6-4b98-ae9a-19c0aa9fcf35" />


# Sharp RW-16G1 Ultimate Multi-OS Gaming Station

โปรเจกต์ชุบชีวิตแท็บเล็ต **Sharp RW-16G1**  
ให้กลายเป็นเครื่องเล่นเกมและใช้งานอเนกประสงค์แบบ **3 ระบบในเครื่องเดียว**

รองรับการบูต:
- Windows 10
- Bliss OS (Android-x86)
- Batocera Linux

ควบคุมการบูตทั้งหมดด้วย **rEFInd Bootloader**  
ระบบทุกตัวใช้งานได้จริงและเสถียร

---

## ✨ ภาพรวมโปรเจกต์

โปรเจกต์นี้มีเป้าหมายเพื่อยืดอายุการใช้งานอุปกรณ์ x86 รุ่นเก่า  
โดยออกแบบระบบให้แต่ละ OS ทำหน้าที่ของตัวเองอย่างชัดเจน

แทนที่จะพยายาม “ให้ OS เดียวทำทุกอย่าง”  
เราเลือกใช้ **หลาย OS ที่ถนัดงานของตัวเอง**

---

## 🎯 เป้าหมายของโปรเจกต์

- นำ Sharp RW-16G1 กลับมาใช้งานได้จริง
- ทำระบบ Multi-Boot ที่เสถียร
- รองรับจอสัมผัสอย่างเหมาะสม
- แยกบทบาทของแต่ละ OS ชัดเจน
- มีเอกสารให้ผู้อื่นทำตามได้

---

## 🖥️ ระบบปฏิบัติการที่รองรับ

| ระบบ | จุดประสงค์ | สถานะ |
|---|---|---|
| Windows 10 | เกม PC / โปรแกรมทั่วไป | ✔ ใช้งานได้ |
| Bliss OS v14 | เกม Android / จอสัมผัส | ✔ ใช้งานได้ |
| Batocera Linux | เครื่องเกม Retro | ✔ ใช้งานได้ |

---

## 🧱 ข้อมูลฮาร์ดแวร์ (Sharp RW-16G1)

| รายการ | รายละเอียด |
|---|---|
| CPU | Intel Atom x5-Z8300 |
| RAM | 4 GB |
| ที่เก็บข้อมูล | eMMC |
| หน้าจอ | 10.1 นิ้ว (Touchscreen) |
| สถาปัตยกรรม | x86_64 |
| โหมดบูต | UEFI |

---

## 🔁 ลำดับการบูตระบบ (Boot Flow)

```text
เปิดเครื่อง
   ↓
UEFI Firmware
   ↓
rEFInd Bootloader
   ↓
 ┌─────────────┬─────────────┬─────────────┐
 │ Windows 10  │ Bliss OS    │ Batocera    │
 └─────────────┴─────────────┴─────────────┘
