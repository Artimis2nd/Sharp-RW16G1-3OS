# ปัญหาที่พบจากการใช้งาน

เอกสารนี้รวบรวมปัญหาที่พบจากการใช้งาน **Sharp RW-16G1 แบบ Multi-OS (3OS)**  
เน้นวิธีแก้ที่ได้ผลจริง มากกว่าทางทฤษฎีหรือหน้า Settings

---

## ปัญหาที่เจอบน Windows

### Windows 10: ภาษาเพี้ยน / ภาษาไทยซ้ำ / แสดงไม่ตรงกับ Settings

#### 🔥 อาการ (Symptoms)
- กด `Win + Space` พบภาษาไทย (TH) ซ้ำ หรือสลับภาษาแปลก
- Settings → Language → Preferred languages แสดงแค่ `English (United States)`
- ไม่สามารถลบภาษาไทยจาก Settings ได้ หรือไม่เห็นให้ลบ
- พฤติกรรมภาษาไม่ตรงกับสิ่งที่แสดงใน Settings

#### 🧪 วิธีตรวจสอบความจริง (ขั้นพิสูจน์)
เปิด **PowerShell (Run as Administrator)**

```powershell
Get-WinUserLanguageList
```
การแปลผล:
- พบ th-TH มากกว่า 1 รายการ → ภาษาไทยซ้อนจริง
- พบแค่ en-US แต่ Win + Space ยังแสดงผิด → user language profile เคยพัง / มี ghost IME
- หมายเหตุ: ข้อมูลจาก PowerShell คือข้อมูลจริงของระบบ
- หน้า Settings อาจแสดงไม่ครบ

#### 🛠 วิธีแก้ที่ได้ผล 100% (Reset + Add ใหม่)

รีเซ็ต language list ของ user แล้วเพิ่มภาษาไทยใหม่แบบสะอาด
```powershell
$LangList = Get-WinUserLanguageList
$LangList.Add("th-TH")
Set-WinUserLanguageList $LangList -Force
```
#### ✅ ผลลัพธ์ที่ถูกต้อง
- เหลือภาษา ENG / TH เท่านั้น
- ไม่มีภาษา / คีย์บอร์ดซ้ำ
- พฤติกรรม Win + Space ตรงกับ Settings
- ปัญหา ghost language ถูกล้างออกจาก user profile

---

## ปัญหาที่เจอบน rEFInd / Bootloader

### rEFInd: ตั้งค่า `refind.conf` ผิด ทำให้ไม่มีปุ่มบูต

#### 🔥 อาการ (Symptoms)
- เข้า rEFInd แล้วไม่แสดงปุ่มบูตใด ๆ
- หน้าจอว่าง หรือแสดงเฉพาะพื้นหลัง
- ไม่สามารถเลือกเข้า OS ใดได้จาก rEFInd
- เกิดหลังแก้ไข `refind.conf` ผิดพลาด

#### 🧠 สาเหตุ
- แก้ไข `refind.conf` ผิด syntax
- ตั้งค่า theme / icon / menuentry ผิด
- rEFInd โหลด config ไม่ได้ แต่ยังถูกเรียกเป็น bootloader หลัก

#### 🛠 วิธีแก้ (ใช้ Batocera เป็นเครื่องมือกู้) หาก rEFInd ยังตั้งค่าให้สแกน USB ได้อยู่
ใช้ **Batocera** เป็นระบบชั่วคราวเพื่อเข้าไปแก้ไขไฟล์ `refind.conf`

**ขั้นตอน**
1. บูตเครื่องจาก  
   - Batocera USB  
   - หรือ Batocera ที่ติดตั้งอยู่ใน SSD ของเครื่อง
2. เมื่อเข้าเมนู Batocera แล้ว กด **F1**  
   เพื่อเข้า File Manager
3. เข้าไปที่ไดรฟ์ EFI ที่เก็บ rEFInd (โดยทั่วไปคือไดรฟ์ `S:`)
4. เปิดไฟล์: S:\EFI\refind\refind.conf แล้วแก้ไขใหม่
5. แก้ไขหรือย้อนค่าที่ตั้งผิด (เช่น theme, background, menuentry)
6. บันทึกไฟล์ แล้วรีบูตเครื่อง

#### ✅ ผลลัพธ์ที่ถูกต้อง
- rEFInd กลับมาแสดงปุ่มบูตตามปกติ
- ไม่ต้องใช้ Windows หรือ Linux หลักในการกู้
- Batocera ทำหน้าที่เป็น “ระบบกู้ภัย” สำหรับ EFI

> หมายเหตุ:  
> วิธีนี้เหมาะมากสำหรับเครื่อง Multi-OS  
> เพราะไม่พึ่ง OS ใด OS หนึ่งเป็นหลัก

---
