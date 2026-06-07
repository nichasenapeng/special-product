# 📊 Special Products Dashboard — เอกสารส่งต่องาน (Handoff)

> ระบบ Dashboard ติดตามยอดขายสินค้า Special Products (ตลาดญี่ปุ่น)
> ดึงข้อมูล Real-time จาก Google Sheets แสดงผลผ่านหน้าเว็บ HTML หน้าเดียว

🔗 **Live:** https://nichasenapeng.github.io/special-product/
📁 **Repo:** https://github.com/nichasenapeng/special-product

---

## 1. ภาพรวมระบบ (Architecture)

ระบบนี้เป็น **HTML ไฟล์เดียว** ไม่มี Backend ไม่มี Database ไม่มี Server

```
Browser (Chrome/Safari)
      ↓ ดึงตรง (fetch CSV)
Google Sheets (Export URL)
      ↓ คำนวณใน
JavaScript ในไฟล์ index.html
      ↓ แสดงผล
หน้าจอ Dashboard
```

**ข้อดี:** ไม่ต้องดูแล server, ไม่มีค่าใช้จ่าย, deploy ง่าย
**ข้อจำกัด:** ทำ Login / บันทึกข้อมูลถาวรไม่ได้ (เป็น read-only จาก Sheets)

---

## 2. เทคโนโลยีที่ใช้

| ส่วน | เทคโนโลยี |
|---|---|
| โครงสร้าง | HTML5 + CSS + Vanilla JavaScript (ไม่มี framework) |
| กราฟ | Chart.js 4.4.1 + datalabels plugin (โหลดจาก CDN) |
| ฟอนต์ | IBM Plex Sans Thai + IBM Plex Mono (Google Fonts) |
| แหล่งข้อมูล | Google Sheets (export CSV) |

ทุก library โหลดจาก CDN — ไม่ต้องติดตั้งอะไรเพิ่ม แค่เปิดไฟล์ก็ใช้ได้

---

## 3. การเชื่อมต่อ Google Sheets

ข้อมูลทั้งหมดมาจาก Google Sheet เดียว แยกเป็น 4 แท็บ (gid)

**Spreadsheet ID:** `1arsUj_szRLUAn6uxaKYRy7Q9xfueAd7zUZXBbazN-ug`

| สินค้า | Key | gid (แท็บ) |
|---|---|---|
| YTR (Yakitori) | `ytr` | 820992683 |
| Marinade | `mar` | 153991926 |
| IVQF | `ivqf` | 2045781807 |
| Further | `fur` | 355730483 |

**สูตร URL ที่ดึงข้อมูล:**
```
https://docs.google.com/spreadsheets/d/{SID}/export?format=csv&gid={GID}
```

### ⚠️ สำคัญ — สิทธิ์การเข้าถึง
Google Sheet ต้องตั้งค่า **Share → Anyone with the link → Viewer**
ถ้าตั้งเป็น Private ระบบจะดึงข้อมูลไม่ได้

---

## 4. การ Config (แก้ตรงไหน)

ค่า config สำคัญอยู่ช่วงต้นของ `<script>` ในไฟล์ `index.html`

### เปลี่ยน Spreadsheet / แท็บ
```javascript
var SID='1arsUj_szRLUAn6uxaKYRy7Q9xfueAd7zUZXBbazN-ug';
var GIDS={ytr:'820992683',mar:'153991926',ivqf:'2045781807',fur:'355730483'};
```

### เปลี่ยน Capacity เป้าหมาย (T/mo) และสี
```javascript
var CFG={
  ytr: {n:'YTR',     cap:1200,mo:100,c:'#0d9488', ...},  // mo = เป้า/เดือน
  mar: {n:'Marinade',cap:4560,mo:380,c:'#2563eb', ...},
  ivqf:{n:'IVQF',    cap:4200,mo:350,c:'#e07b39', ...},
  fur: {n:'Further', cap:4200,mo:350,c:'#7c3aed', ...}
};
```
- `cap` = capacity ทั้งปี (T)
- `mo` = เป้าต่อเดือน (T) — เส้นประสีเหลืองในกราฟ
- `c` = สีประจำสินค้า

### Mapping ชื่อลูกค้า → Key (N2K)
ถ้า Google Sheet เขียนชื่อลูกค้าหลายแบบ ให้ map เข้า key เดียวกัน
```javascript
var N2K={
  'OKAYA (Kanematsu)':'okaya_kan',
  'OKAYA (KS FRONTIER)':'okaya_kan',   // ชื่อต่างกันแต่ลูกค้าเดียวกัน
  'HANWA (SKYLARK)':'hanwa',
  ...
};
```
**เมื่อมีลูกค้าใหม่ใน Sheet:** เพิ่มชื่อใน N2K เพื่อให้ระบบรู้จัก

---

## 5. ส่วนประกอบหน้าจอ

หน้า Dashboard มีส่วนหลักดังนี้ (เรียงจากบนลงล่าง):

1. **Overview Cards** — สรุป Capacity Utilization 4 สินค้า (% ของเป้า)
2. **Priority Matrix** — จัดอันดับลูกค้า TOP 10 อัตโนมัติ
3. **Monthly Trend** — กราฟรายเดือน 4 สินค้า (แท่ง 2026 + เส้น 2024/2025 + เส้นเป้า)
4. **ยอดรวมรายปี** — กราฟเปรียบเทียบ 4 สินค้า 3 ปี
5. **TOP 5 Focus** — TOP 5 ลูกค้าแต่ละสินค้า (เรียงอัตโนมัติ)
6. **Sidebar** — รายชื่อลูกค้าแบ่งกลุ่ม (Star / Growth / Watch / Activate)
7. **หน้าลูกค้ารายตัว** — กดที่ชื่อลูกค้าใน sidebar เพื่อดูรายละเอียด

---

## 6. ⭐ จุดสำคัญ — ข้อมูลทุกอย่าง Auto-compute

> **ไม่มีข้อมูล hard-code อีกต่อไป** — ทุกตัวเลขมาจาก Google Sheets

| ส่วน | คำนวณยังไง |
|---|---|
| **Priority Matrix** | Score = (Growth × 2) + ยอด 2026 → เรียง TOP 10 |
| **TOP 5 Focus** | แต่ละสินค้า: Score = (ยอด2026 × 2) + Growth → เรียง TOP 5 |
| **Overview / กราฟ** | Sum ยอดรายเดือนจาก Sheet ตรงๆ |
| **หน้าลูกค้า** | แสดงยอด 24/25/26 + YoY ของลูกค้านั้น |

**ผลลัพธ์:** แก้ยอดใน Google Sheets → กดปุ่ม refresh → ทุกอย่างอัปเดต+เรียงลำดับใหม่เองทันที

---

## 7. วิธีใช้งาน

1. เปิดหน้า Dashboard — ระบบ **ดึงข้อมูลอัตโนมัติทันที**
2. กดปุ่ม **🔄 ดึงข้อมูลใหม่จาก Sheets** มุมขวาบน เพื่อดึงข้อมูลล่าสุด
3. คลิกชื่อลูกค้าใน sidebar เพื่อดูรายละเอียดรายลูกค้า

---

## 8. การ Deploy (GitHub Pages)

> ✅ ระบบ deploy แล้วที่ https://nichasenapeng.github.io/special-product/

ขั้นตอน deploy (สำหรับครั้งต่อไป / repo ใหม่):

1. สร้าง repo ใหม่บน GitHub
2. อัปโหลดไฟล์ (เปลี่ยนชื่อเป็น `index.html`)
3. ไปที่ **Settings → Pages → Source: main branch**
4. รอ ~1 นาที จะได้ URL: `https://{username}.github.io/{repo-name}/`
5. แชร์ URL ให้ทีมเปิดผ่าน browser ได้เลย

**การอัปเดตในอนาคต:** แก้ไฟล์ `index.html` แล้ว commit + push ขึ้น branch `main`
GitHub Pages จะอัปเดตหน้าเว็บอัตโนมัติภายใน ~1 นาที

---

## 9. การแก้ปัญหาเบื้องต้น (Troubleshooting)

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---|---|---|
| ข้อมูลไม่ขึ้น / ค้างที่ค่า default | Sheet เป็น Private | ตั้ง Share เป็น Anyone with link (Viewer) |
| ลูกค้าใหม่ไม่ปรากฏ | ชื่อยังไม่อยู่ใน N2K | เพิ่ม mapping ใน `N2K` |
| ตัวเลขเพี้ยน | format ใน Sheet เปลี่ยน (เพิ่ม/ลบ column) | ตรวจ logic ใน `parseSheet()` |
| กราฟไม่แสดง | CDN โหลดไม่ได้ / ไม่มีเน็ต | ตรวจการเชื่อมต่ออินเทอร์เน็ต |
| ขึ้น "⚠️ บางส่วน" | บางแท็บดึงไม่สำเร็จ | เปิด Console (F12) ดู error ของแต่ละ gid |

---

## 10. โครงสร้างไฟล์ภายใน (สำหรับ Developer)

ไฟล์เดียว `index.html` แบ่งเป็น 3 ส่วน:

```
<style>...</style>        → CSS ทั้งหมด
<body>...</body>          → โครงสร้าง HTML (header, sidebar, panels)
<script>...</script>      → Logic ทั้งหมด:
    - CONFIG (SID, GIDS, CFG, N2K)
    - DEFAULT DATA (ข้อมูลสำรองตอนยังโหลดไม่เสร็จ)
    - parseCSV / parseSheet  → แปลง CSV จาก Sheet
    - doFetch / onDone        → ดึงข้อมูล + render ใหม่
    - renderChart / renderAllChart → กราฟ
    - renderPriorityMatrix    → Priority Matrix (auto)
    - renderTop5              → TOP 5 (auto)
    - buildCustHTML           → หน้าลูกค้ารายตัว
    - goPan / togGrp          → navigation
```

### ฟังก์ชันที่ควรรู้
- `parseSheet(csv)` — หัวใจการอ่านข้อมูล รองรับ 2 รูปแบบ Sheet (wide / long)
- `computePriorityMatrix()` — สูตรจัดอันดับลูกค้า แก้ score ที่นี่
- `renderTop5()` — สูตรเรียง TOP 5 แก้ score ที่นี่

---

*เอกสารนี้สร้างขึ้นเพื่อส่งต่องาน — หากแก้ไขระบบเพิ่มเติม ควรอัปเดตเอกสารนี้ตามไปด้วย*
