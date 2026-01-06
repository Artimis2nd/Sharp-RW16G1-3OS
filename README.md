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

## 🛠️ ขั้นตอนการติดตั้งอย่างละเอียด (Detailed Step-by-Step Guide)

---

### 1️⃣ ขั้นตอนที่ 1: การแบ่งพื้นที่ SSD ใน Windows 10
ก่อนจะลงระบบอื่น เราต้อง "ตัดแบ่ง" ที่ว่างจาก Windows ออกมาเตรียมไว้ก่อน
1. **เปิดเครื่องมือ:** คลิกขวาที่ปุ่ม **Start** (มุมซ้ายล่าง) แล้วเลือก **Disk Management**
2. **เลือกไดรฟ์:** คลิกขวาที่แถบของไดรฟ์ **C:** (ที่มีคำว่า Boot, Page File...)
3. **เริ่มแบ่ง:** เลือกเมนู **Shrink Volume**
4. **กำหนดขนาด:** ในช่อง *Enter the amount of space to shrink in MB* ให้ใส่ตัวเลขพื้นที่ที่ต้องการ
   - เช่น ถ้าต้องการ 64GB ให้ใส่ `65536`
   - ถ้าต้องการ 100GB ให้ใส่ `102400`
5. **ยืนยัน:** กดปุ่ม **Shrink**
6. **ตรวจสอบ:** คุณจะเห็นแถบสีดำเพิ่มขึ้นมาที่เขียนว่า **Unallocated** ให้ปล่อยทิ้งไว้แบบนั้น (ห้ามสร้าง New Volume)

---

### 2️⃣ ขั้นตอนที่ 2: การเตรียม USB และติดตั้ง Bliss OS (Android)
ขั้นตอนนี้จะทำให้เครื่อง Sharp ของคุณมีระบบ Android ไว้เล่นเกม
1. **เตรียมไฟล์:** เปิดโปรแกรม **Rufus** บน Windows
   - **Device:** เลือก USB Flash Drive ของคุณ
   - **Boot selection:** กดปุ่ม **SELECT** แล้วเลือกไฟล์ ISO ของ Bliss OS
   - **Partition scheme:** ต้องเลือกเป็น **GPT** เท่านั้น
   - **Target system:** ต้องเป็น **UEFI (non CSM)**
   - กด **START** และรอจนเสร็จ
2. **บูตเครื่อง Sharp:** เสียบ USB Hub, USB Boot และเมาส์/คีย์บอร์ด -> ปิดเครื่อง -> กด **Volume Down ค้างไว้ + Power**
3. **เลือกตัวบูต:** ในหน้า Boot Menu เลือกไปที่ชื่อ **USB Flash Drive** ของคุณ
4. **เข้าหน้าติดตั้ง:** เมื่อเห็นเมนูสีฟ้า/ดำ ให้เลือก **Installation - Install Bliss-OS to harddisk**
5. **เลือกพาร์ทิชัน:** มองหาบรรทัดที่เขียนว่า **Free Space** (พื้นที่ที่เราแบ่งไว้จากข้อ 1) แล้วกด OK
6. **การฟอร์แมต:** เลือกเป็น **ext4** และตอบ **Yes** เพื่อยืนยัน
7. **ติดตั้งตัวบูต:** ระบบจะถามว่า *Do you want to install EFI GRUB2?* ให้ตอบ **Yes**
8. **สิทธิ์การเข้าถึง:** ระบบจะถามว่า *Do you want to install /system directory as read-write?* ให้ตอบ **Yes**
9. **เสร็จสิ้น:** เมื่อเสร็จแล้วให้เลือก **Reboot** และถอด USB ออกทันที

---

### 3️⃣ ขั้นตอนที่ 3: การตั้งค่าเมนูบูตด้วย Grub2Win
ขั้นตอนนี้จะสร้างหน้าเมนูสวยๆ ให้คุณเลือกระบบตอนเปิดเครื่องด้วยการทัชสกรีน
1. **ติดตั้ง:** กลับเข้า Windows 10 แล้วรันโปรแกรมติดตั้ง **Grub2Win**
2. **หน้าหลัก:** เปิดโปรแกรมขึ้นมาแล้วกดปุ่มสีเหลือง **Manage Boot Menu**
3. **เพิ่มรายการ:** กด **Add New Item**
   - **OS Type:** เลือกเป็น **Android**
   - **Title:** พิมพ์ชื่อว่า `Bliss OS`
   - **Boot Partition:** กดปุ่มเพื่อเลือกพาร์ทิชันที่คุณเพิ่งลง Bliss OS ไป (สังเกตจากขนาด 64GB/100GB)
   - กด **Apply** และ **OK**
4. **ปรับแต่งทัชสกรีน:** ในหน้าหลักกด **Main Settings**
   - ตั้งค่า **Timeout** เป็น 10-15 วินาที
   - เลือก **Theme** ที่ชอบ (แนะนำรุ่นที่ปุ่มใหญ่ๆ เพื่อให้ใช้นิ้วจิ้มเลือก OS ได้ง่าย)
5. **บันทึก:** กด **Apply** และปิดโปรแกรม

---

### 4️⃣ ขั้นตอนที่ 4: การลงระบบเกมเก่า Batocera บน SD Card
แยกส่วนของเกม Retro ออกมาไว้ในการ์ดเพื่อให้จัดการง่าย
1. **เขียนข้อมูล:** เสียบ MicroSD Card เข้าคอม -> เปิด **Rufus**
2. **ตั้งค่า:** เลือก SD Card ของคุณ -> กด **SELECT** เลือกไฟล์ Batocera -> กด **START**
3. **ขยายพื้นที่:** เสียบการ์ดเข้าเครื่อง Sharp -> บูตเครื่องแล้วกด **Volume Down + Power** -> เลือกบูตจาก **SD Card**
4. **รอระบบ:** ครั้งแรกระบบจะใช้เวลานานหน่อยเพื่อขยายพื้นที่จนเต็มการ์ด ห้ามปิดเครื่องจนกว่าจะเห็นหน้าเมนูเกม

---

### 5️⃣ ขั้นตอนที่ 5: การเชื่อมต่ออุปกรณ์เสริม (Setup Peripherals)
1. **เชื่อมต่อจอยเกม:**
   - เข้าไปที่หน้าการตั้งค่า Bluetooth ของแต่ละ OS (Windows / Android / Batocera)
   - กดปุ่ม Pair ที่จอยเกมของคุณจนไฟกะพริบ
   - เลือกชื่อจอยบนหน้าจอเครื่อง Sharp เพื่อทำการจับคู่
2. **เชื่อมต่อโทรศัพท์ Android (Remote Keyboard):**
   - เปิดแอป **Bluetooth Keyboard & Mouse** บนโทรศัพท์
   - ทำการ Pair กับเครื่อง Sharp เหมือนการต่อจอยเกม
   - ตอนนี้คุณจะใช้หน้าจอมือถือเลื่อนเมาส์และพิมพ์แทนคีย์บอร์ดจริงได้ทันที

---

## 💡 บันทึกการใช้งาน (Important Notes)
* การสลับระบบ OS อาจต้องทำการ Re-pair Bluetooth ใหม่ เนื่องจากแต่ละระบบจัดการโปรไฟล์แยกกัน
* พอร์ต USB 3.0 (สีน้ำเงิน) บน Hub ควรใช้สำหรับอุปกรณ์ที่ต้องการความเร็วหรือความเสถียรสูง
