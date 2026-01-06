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

## 💻 ระบบที่ใช้งาน (Triple Boot)
1. **Windows 10:** ระบบหลักสำหรับทำงานและเกม PC
2. **Bliss OS (Android 11/12):** สำหรับรันแอป Android และ Mobile Gaming
3. **Batocera:** ระบบ Retro Gaming (ติดตั้งลง SSD โดยตรงเพื่อความเร็วสูงสุด)

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

## 🛠️ ขั้นตอนการติดตั้งอย่างละเอียด (Detailed Step-by-Step Guide)

---

### 1️⃣ ขั้นตอนที่ 1: การแบ่งพื้นที่ SSD ใน Windows 10 (3 Partitions)
เราจะตัดแบ่งเค้ก (SSD) ออกเป็น 3 ส่วนเพื่อรองรับ 3 ระบบปฏิบัติการ
1. **เปิดเครื่องมือ:** คลิกขวาที่ปุ่ม **Start** แล้วเลือก **Disk Management**
2. **แบ่งพื้นที่ก้อนที่ 1 (สำหรับ Android):**
   - คลิกขวาที่ไดรฟ์ **C:** เลือก **Shrink Volume**
   - ใส่ตัวเลข `32768` (สำหรับ 32GB) หรือ `65536` (สำหรับ 64GB) แล้วกด **Shrink**
3. **แบ่งพื้นที่ก้อนที่ 2 (สำหรับ Batocera):**
   - คลิกขวาที่ไดรฟ์ **C:** อีกครั้ง เลือก **Shrink Volume**
   - ใส่ตัวเลข `32768` (สำหรับ 32GB) แล้วกด **Shrink**
4. **ตรวจสอบ:** คุณต้องเห็นแถบสีดำ **Unallocated** 2 ก้อนเตรียมไว้ (ห้ามสร้าง New Volume)

---

### 2️⃣ ขั้นตอนที่ 2: การติดตั้ง Bliss OS (Android)
1. **เตรียม USB:** ใช้ **Rufus** เขียนไฟล์ Bliss OS ลง USB (เลือก Partition scheme: **GPT** / Target: **UEFI**)
2. **บูตเครื่อง:** เสียบ USB Hub + เมาส์ + USB Boot -> ปิดเครื่อง -> กด **Volume Down ค้างไว้ + Power**
3. **เริ่มติดตั้ง:** เลือกเมนู **Installation - Install Bliss-OS to harddisk**
4. **เลือกเป้าหมาย:** มองหาพาร์ทิชันที่เขียนว่า **Free Space** (ก้อนที่ 1) แล้วกด OK
5. **Format:** เลือกเป็น **ext4** และตอบ **Yes** เพื่อยืนยัน
6. **ยืนยันการบูต:** ระบบถาม *Install EFI GRUB2?* ตอบ **Yes** / ถาม *Install /system as read-write?* ตอบ **Yes**
7. **เสร็จสิ้น:** เลือก **Reboot** และถอด USB ออก

---

### 3️⃣ ขั้นตอนที่ 3: การติดตั้ง Batocera ลง SSD (Internal)
1. **เตรียม USB:** ใช้ **Rufus** เขียนไฟล์ Batocera ลง USB อีกครั้ง
2. **บูตเข้า USB:** ทำเหมือนขั้นตอนที่ 2 แต่เลือกบูตจาก USB Batocera
3. **ติดตั้งลง SSD:** เมื่อเข้าหน้าเมนู Batocera ให้กด **Start** > **System Settings** > **Install Batocera on a New Disk**
   - **Target Device:** เลือก SSD ภายในเครื่อง Sharp (ระวังอย่าเลือกผิดตัว)
   - **Target Architecture:** เลือก **X86_64**
   - **Confirm:** พิมพ์คำว่า `YES` (ตัวใหญ่) เพื่อยืนยันการติดตั้ง
4. **เปลี่ยนระบบไฟล์ (เพื่อให้ Windows มองเห็น):** หลังติดตั้งและรีบูตเข้า Batocera อีกครั้ง
   - ไปที่ **System Settings** > **Frontend Developer Options** > **Format a Drive**
   - เลือกพาร์ทิชันข้อมูล (Share) แล้วเลือก File System เป็น **EXFAT**
   - กดตกลงและ Restart

---

### 4️⃣ ขั้นตอนที่ 4: การรวมทุกระบบด้วย Grub2Win (Triple Boot Menu)
ทำให้หน้าจอตอนเปิดเครื่องมี 3 ปุ่มให้เลือกทัชสกรีนได้เลย
1. **ติดตั้ง:** กลับเข้า Windows 10 และรันโปรแกรม **Grub2Win**
2. **ตั้งค่าเมนู:** กดปุ่ม **Manage Boot Menu** -> **Add New Item**
   - **รายการที่ 1 (Android):** เลือก Type: **Android** / Title: `Bliss OS` / ชี้ไปที่พาร์ทิชัน Android
   - **รายการที่ 2 (Retro):** เลือก Type: **Linux** / Title: `Batocera` / ชี้ไปที่พาร์ทิชัน Batocera
3. **ปรับแต่งหน้าตา:** กด **Main Settings** เลือก Theme ที่ปุ่มใหญ่ๆ เพื่อให้ใช้นิ้วจิ้มเลือกได้ง่าย
4. **บันทึก:** กด **Apply** ตอนนี้คุณจะได้เมนู Triple Boot บน SSD ที่สมบูรณ์แบบ

### 💡 ทริคการตั้งค่า Grub2Win สำหรับ Sharp RW-16G1
* **Default Boot:** แนะนำให้ตั้งเป็น Windows 10 เผื่อกรณีที่คุณเปิดเครื่องทิ้งไว้แล้วเดินไปหยิบน้ำ ระบบจะเข้า Windows ให้เองอัตโนมัติ
* **Timeout:** ตั้งไว้ประมาณ 10-15 วินาที
* **Interaction:** หากคุณแตะหน้าจอในขณะที่เวลากำลังถอยหลัง ระบบจะหยุดเวลา (Pause) และรอให้คุณเลือก OS โดยไม่จำกัดเวลา ช่วยให้ใช้งานแบบ Tablet ได้สะดวกมาก

---

### 5️⃣ ขั้นตอนที่ 5: การจัดการไฟล์เกมผ่าน Windows
1. ในหน้า Windows 10 ให้เปิด **File Explorer**
2. คุณจะพบไดรฟ์ใหม่ที่ชื่อว่า **SHARE** (หรือชื่อที่ Batocera ตั้งไว้ที่เป็น EXFAT)
3. เข้าไปที่โฟลเดอร์ `roms` คุณสามารถก๊อปปี้เกมจากคอมพิวเตอร์มาวางในโฟลเดอร์แยกตามเครื่องเกม (เช่น `ps1`, `sfc`, `gba`) ได้ทันที

---

## 💡 บันทึกการใช้งาน (Important Notes)
* การสลับระบบ OS อาจต้องทำการ Re-pair Bluetooth ใหม่ เนื่องจากแต่ละระบบจัดการโปรไฟล์แยกกัน
* พอร์ต USB 3.0 (สีน้ำเงิน) บน Hub ควรใช้สำหรับอุปกรณ์ที่ต้องการความเร็วหรือความเสถียรสูง
