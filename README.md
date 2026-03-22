# 🏭 O.X. Factory — ระบบบันทึกการส่งงาน

Web App สำหรับโรงงานตัดเย็บ บันทึกการส่งงานช่าง เชื่อมต่อ Google Sheets แบบเรียลไทม์

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-green?style=flat-square&logo=github)](https://YOUR_USERNAME.github.io/ox-factory/)

---

## ✨ ฟีเจอร์

- 📝 **บันทึกส่งงานช่าง** — เลือกช่าง, รุ่น, วันที่, จำนวน, รูปภาพ
- 📋 **ประวัติส่งงาน** — ดูรายการย้อนหลัง กรอง Week 1 / Week 2 / Week End
- 📊 **รายงานสรุป** — ผู้จัดการดูรายงานรวมทุกช่าง (ล็อค PIN: **1125**)
- 🖼️ **รูปภาพ** — อัปโหลดรูปหลักฐาน แสดงใน App และ Google Sheets
- 🗑️ **ลบรายการ** — ลบได้ทั้งใน App และ Sheet อัปเดตทันที
- 📱 **รองรับ iOS & Android** — เปิดในเบราว์เซอร์ทุกเครื่อง
- 🔄 **เรียลไทม์** — ทุกเครื่องเห็นข้อมูลเดียวกัน

---

## 🚀 วิธีติดตั้ง

### ขั้นตอนที่ 1 — Fork & Enable GitHub Pages

1. กด **Fork** repository นี้
2. ไปที่ **Settings → Pages**
3. Source: **Deploy from a branch** → Branch: `main` → folder: `/ (root)`
4. กด **Save** → รอ 1-2 นาที
5. URL ของคุณจะเป็น: `https://YOUR_USERNAME.github.io/ox-factory/`

### ขั้นตอนที่ 2 — สร้าง Google Sheets

1. เปิด [Google Sheets](https://sheets.google.com) → สร้าง Spreadsheet ใหม่
2. จด **Spreadsheet ID** จาก URL:
   ```
   https://docs.google.com/spreadsheets/d/[SPREADSHEET_ID]/edit
   ```
3. เปิด [Google Drive](https://drive.google.com) → สร้าง Folder ใหม่ชื่อ "OX Factory Images"
4. จด **Folder ID** จาก URL ของ Folder:
   ```
   https://drive.google.com/drive/folders/[FOLDER_ID]
   ```

### ขั้นตอนที่ 3 — ติดตั้ง Google Apps Script

1. ใน Google Sheets → เมนู **Extensions → Apps Script**
2. ลบโค้ดเดิมทั้งหมด
3. Copy โค้ดจากไฟล์ `apps-script/Code.gs` ในนี้ วางลงไป
4. แก้ค่าบรรทัดแรก:
   ```javascript
   var SHEET_ID  = 'YOUR_SPREADSHEET_ID';  // ← ใส่ ID จากขั้นตอนที่ 2
   var FOLDER_ID = 'YOUR_DRIVE_FOLDER_ID'; // ← ใส่ ID จากขั้นตอนที่ 2
   ```
5. กด **Save** (Ctrl+S)
6. กด **Deploy → New deployment**
   - Type: **Web App**
   - Execute as: **Me**
   - Who has access: **Anyone**
7. กด **Deploy** → Copy **Web App URL** ที่ได้

### ขั้นตอนที่ 4 — เชื่อม App กับ Script

1. เปิด App ที่ GitHub Pages URL ของคุณ
2. กด **⚙️ ตั้งค่า URL** (ปุ่มล่างสุดในหน้าแรก)
3. วาง Web App URL → **บันทึก**
4. ✅ พร้อมใช้งาน!

---

## 📁 โครงสร้างไฟล์

```
ox-factory/
├── index.html          ← Web App หลัก (เปิดในเบราว์เซอร์ได้เลย)
├── apps-script/
│   └── Code.gs         ← โค้ดสำหรับ Google Apps Script
└── README.md
```

---

## 🔐 รหัส PIN

| บทบาท | รหัส |
|--------|-------|
| ผู้จัดการ (รายงานสรุปช่าง) | **1125** |

---

## 📊 Google Sheets Structure

Sheet จะสร้างอัตโนมัติ 2 แผ่น:

| Sheet | คอลัมน์ |
|-------|---------|
| **Records** | ID, ชื่อช่าง, ชื่อรูป/รุ่น, วันที่, จำนวน, รอบ, หมายเหตุ, รูปภาพ (URLs) |
| **Technicians** | ชื่อช่าง, วันที่เพิ่ม |

---

## ⚙️ การตั้งค่าเพิ่มเติม

### เปลี่ยน PIN ผู้จัดการ
แก้ไขในไฟล์ `index.html` บรรทัด:
```javascript
var MANAGER_PIN = '1125'; // ← เปลี่ยนตรงนี้
```

### Demo Mode
กด "ข้าม (Demo)" ในหน้าตั้งค่า URL เพื่อทดลองใช้โดยไม่ต้องมี Apps Script URL (ข้อมูลจะไม่ถูกบันทึก)

---

## 🛠️ Tech Stack

- **Frontend**: Vanilla HTML/CSS/JS (ไม่มี dependency)
- **Backend**: Google Apps Script (serverless)
- **Database**: Google Sheets
- **Storage**: Google Drive (รูปภาพ)
- **Hosting**: GitHub Pages (ฟรี)

---

## 📱 Screenshots

| หน้าแรก | บันทึกงาน | ประวัติ | รายงาน |
|---------|-----------|---------|--------|
| Role Select | Form | History | Manager |
