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
* **Controller:** จอยเกมไร้สาย (เชื่อมต่อผ่าน Bluetooth หรือสาย USB)
* **Remote Input:** โทรศัพท์ Android (ใช้งานแอปจำลองคีย์บอร์ดและเมาส์ Bluetooth)
* **Accessories:** USB 3.0 Hub & 128GB MicroSD Card

## 💿 ระบบที่ใช้งาน (Triple Boot)
1. **Windows 10:** ระบบหลักสำหรับทำงานและเกม PC
2. **Bliss OS (Android 11/12):** สำหรับรันแอป Android และแก้เกม
3. **Batocera v42:** ระบบ Retro Gaming (รันผ่าน SD Card)

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

## 🛠️ ขั้นตอนการติดตั้ง (Detailed Roadmap)

### ขั้นตอนที่ 1: การเตรียมพื้นที่ SSD (Windows 10)
* เปิดโปรแกรม **Disk Management** ใน Windows เพื่อทำการ **Shrink Volume** ไดรฟ์หลัก (C:)
* แบ่งพื้นที่ออกมาประมาณ 64GB - 100GB สำหรับ Android และปล่อยไว้เป็น "Unallocated"

### ขั้นตอนที่ 2: การติดตั้ง Android (Bliss OS)
* ใช้ **Rufus** เขียนไฟล์ Bliss OS ลง USB Flash Drive
* เชื่อมต่อ USB Hub เพื่อใช้ Flash Drive พร้อมเมาส์/คีย์บอร์ด
* บูตเข้า USB เลือก **Installation** เพื่อติดตั้งลงพื้นที่ Unallocated

### ขั้นตอนที่ 3: การตั้งค่า Multi-Boot (Grub2Win)
* ติดตั้ง **Grub2Win** ในหน้า Windows และเพิ่มรายการบูตสำหรับ Bliss OS
* **สายทัชสกรีน:** เลือกใช้ Theme ปุ่มใหญ่และตั้งค่า Timeout ให้เลือก OS ได้ง่าย

### ขั้นตอนที่ 4: การจัดทำระบบเกม Retro (Batocera)
* ใช้ **Rufus** เขียน Batocera ลงใน **MicroSD Card**
* ใช้ปุ่มลัด (Volume Down + Power) เพื่อเลือกบูตจาก MicroSD Card เมื่อต้องการเล่น

### ขั้นตอนที่ 5: การตั้งค่าตัวควบคุม (Peripherals Setup)
* **จอยเกม:** เชื่อมต่อผ่าน Bluetooth ในแต่ละระบบเพื่อความสะดวกในการพกพา
* **Remote Keyboard:** ใช้โทรศัพท์ Android ผ่านแอป "Bluetooth Keyboard & Mouse" ควบคุมแทนคีย์บอร์ดจริง
* **USB Hub:** แนะนำให้ใช้สายต่อผ่าน Hub เมื่อต้องใช้อุปกรณ์หลายอย่างพร้อมกันเนื่องจากพอร์ตเครื่องจำกัด

---

## 💡 บันทึกการใช้งาน (Important Notes)
* การสลับระบบ OS อาจต้องทำการ Re-pair Bluetooth ใหม่ เนื่องจากแต่ละระบบจัดการโปรไฟล์แยกกัน
* พอร์ต USB 3.0 (สีน้ำเงิน) บน Hub ควรใช้สำหรับอุปกรณ์ที่ต้องการความเร็วหรือความเสถียรสูง
