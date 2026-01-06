# Sharp-RW16G1-Gaming-Setup
คู่มือการจัดตั้งระบบ 3 ระบบสำหรับ Sharp RW-16G1

![800-800-Web-Sharp-Tablet-RW-16G1](https://github.com/user-attachments/assets/1a0e5236-574d-4eee-958a-60cb8bca6336)
<img width="735" height="455" alt="image" src="https://github.com/user-attachments/assets/693fbb51-02c8-4d41-9040-dac5caf090a1" />
<img width="741" height="389" alt="image" src="https://github.com/user-attachments/assets/a17ec85e-f2cb-450e-8005-b82453b8249f" />
<img width="394" height="125" alt="image" src="https://github.com/user-attachments/assets/b378fc80-afa6-4b98-ae9a-19c0aa9fcf35" />


# Sharp RW-16G1 Ultimate Gaming Station 🎮

โปรเจกต์ชุบชีวิต Tablet Sharp RW-16G1 ให้กลายเป็นเครื่องเล่นเกม 3 ระบบ (Windows 10 / Android / Batocera)

## 📋 รายละเอียดอุปกรณ์ (My Setup)
* **Device:** Sharp RW-16G1 (15.6 inch Tablet)
* **Controllers:** 2x Xbox Elite Series 2 (Bluetooth Connection)
* **Input Device:** Poco X6 Pro 5G (Remote Bluetooth Keyboard/Mouse)
* **Accessories:** USB 3.0 Hub & 128GB MicroSD Card

## 💿 ระบบที่ใช้งาน (Triple Boot)
1. **Windows 10:** ระบบหลักสำหรับทำงานและเกม PC
2. **Bliss OS (Android 11/12):** สำหรับรันแอป Android และแก้เกม
3. **Batocera v42:** ระบบ Retro Gaming (รันผ่าน SD Card)

## 🛠️ ขั้นตอนการติดตั้ง (Roadmap)
- [ ] แบ่ง Partition SSD 64GB-100GB สำหรับ Android
- [ ] ติดตั้ง Grub2Win เพื่อจัดการเมนู Boot แบบ Touchscreen
- [ ] เขียนไฟล์ Batocera ลง SD Card ด้วย Rufus
- [ ] ตั้งค่า Bluetooth สำหรับจอย Elite 2 และ Poco Remote

# 📦 แหล่งดาวน์โหลดซอฟต์แวร์ (Download Resources)

รวบรวมไฟล์ที่จำเป็นทั้งหมดสำหรับการเซตอัพระบบ Triple Boot บน Sharp RW-16G1

### 🤖 ระบบปฏิบัติการ Android (Bliss OS)
* **Bliss OS 11.13 (เสถียร):** [Download Bliss-v11.13 Official](https://sourceforge.net/projects/blissos-x86/files/Official/bleeding_edge/Generic%20builds%20-%20OS11/)
    * *หมายเหตุ: ตัวนี้เหมาะสำหรับการใช้งานทั่วไปและแก้เกมได้นิ่งที่สุด*
* **Bliss OS 12.12 (เวอร์ชันพัฒนา):** [Download Bliss OS v12.12](https://sourceforge.net/projects/blissos-dev/files/yantra/Generic/)
    * *หมายเหตุ: สำหรับทดลองฟีเจอร์ใหม่ๆ ของ Android 10/11*

### 🎮 ระบบเกม Retro (Batocera)
* **Batocera.linux:** [Official Website](https://batocera.org/download)
    * *เลือกโหลดเวอร์ชัน Standard Desktop (x86_64)*

### 🛠️ เครื่องมือติดตั้ง (Utility Tools)
* **Grub2Win:** [Download from SourceForge](https://sourceforge.net/projects/grub2win/)
    * *ใช้สำหรับสร้างเมนูเลือก Boot (Windows/Android) โดยไม่ต้องพึ่งคีย์บอร์ด*
* **Rufus:** [Official Website](https://rufus.ie/)
    * *ใช้สำหรับเขียนไฟล์ ISO ลง USB Flash Drive หรือ SD Card*

---

## 💡 บันทึกเพิ่มเติมสำหรับการพกพา
1. **Poco X6 Pro 5G:** ใช้แอป *Bluetooth Keyboard & Mouse* เพื่อควบคุมแทนคีย์บอร์ดจริง
2. **Xbox Elite Series 2:** ต่อผ่าน Bluetooth ทั้ง 2 จอย (เช็คแบตเตอรี่ก่อนออกเดินทางทุกครั้ง)
3. **USB Hub:** ใช้ช่อง USB 3.0 (สีน้ำเงิน) สำหรับจอยตัวที่ 1 เพื่อความเสถียรสูงสุด
