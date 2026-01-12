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
| Windows 10-11 | เกม PC / โปรแกรมทั่วไป | ✔ ใช้งานได้ |
| Bliss OS v14 | เกม Android / จอสัมผัส | ✔ ใช้งานได้ |
| Batocera Linux | เครื่องเกม Retro | ✔ ใช้งานได้ |

---

## 🧱 ข้อมูลฮาร์ดแวร์ (Sharp RW-16G1)

| รายการ | รายละเอียด |
|---|---|
| หน้าจอ | 15.6 นิ้ว ความละเอียด 3200 × 1800 (WQHD) แบบ IGZO (ความคมสูง) |
| ซีพียู | Intel Core i5-4200U (Haswell, 2 คอร์ 4 เธรด, 1.6 – 2.6 GHz) |
| กราฟิก | Intel HD Graphics 4400 (ในตัว) |
| แรม | 4 GB DDR3(L) |
| พื้นที่เก็บข้อมูล | 128 GB SSD (mSATA/SSD) |
| ระบบสัมผัส | จอ หลายจุด (10-point) touch + stylus รองรับแรงกด |
| การเชื่อมต่อ | Wi-Fi, Bluetooth 4.0, NFC, USB 3.0 ×3, HDMI, Mini DisplayPort, SD card slot |
| กล้องหน้่า | 2 MP Webcam |
| แบตเตอรี่ | ~9 ชั่วโมง (JEITA) |
| น้ำหนัก | ~1.25 kg |
| โหมดบูต | UEFI (รองรับ multi-boot) — จำเป็นสำหรับหลายระบบ |

---

## 📚 คู่มือการติดตั้ง
- [ภาพรวมการเตรียมเครื่อง](docs/overview.md)
- [ข้อมูลฮาร์ดแวร์และข้อจำกัด](docs/hardware.md)
- [การจัดพาร์ทิชัน](docs/partitioning.md)
- [ติดตั้ง Windows](docs/install-windows.md)
- [ติดตั้ง Bliss OS](docs/install-bliss.md)
- [ติดตั้ง Batocera](docs/install-batocera.md)
- [ตั้งค่า rEFInd](docs/bootloader-refind.md)
- [แก้ปัญหาเบื้องต้น](docs/troubleshooting.md)
- [บทเรียนที่ได้จากโปรเจกต์](docs/lessons-learned.md)

---
