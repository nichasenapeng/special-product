[README.md](https://github.com/user-attachments/files/28426158/README.md)
# 📊 Special Products Dashboard

Dashboard ติดตามยอดขายสินค้า Special Products (ตลาดญี่ปุ่น) แบบ Real-time
ดึงข้อมูลจาก Google Sheets แสดงผลผ่านหน้าเว็บหน้าเดียว ไม่ต้องมี Backend

🔗 **Live Demo:** https://nichasenapeng.github.io/special-product/

---

## ✨ ฟีเจอร์หลัก

- 📈 **Real-time Sync** — ดึงข้อมูลสดจาก Google Sheets ทุกครั้งที่เปิดหน้า
- 🏆 **Priority Matrix** — จัดอันดับลูกค้า TOP 10 อัตโนมัติจากยอดจริง
- 🔥 **TOP 5 Focus** — TOP 5 ลูกค้าแต่ละสินค้า เรียงอัตโนมัติ
- 📊 **Monthly Trend** — กราฟรายเดือนเปรียบเทียบ 3 ปี (2024/2025/2026)
- 👥 **หน้าลูกค้ารายตัว** — แบ่งกลุ่ม Star / Growth / Watch / Activate
- 🎯 **Capacity Tracking** — ติดตาม % การใช้กำลังการผลิตเทียบเป้าหมาย

---

## 🚀 การใช้งาน

1. เปิด [Live Demo](https://nichasenapeng.github.io/special-product/) — ระบบดึงข้อมูลอัตโนมัติทันที
2. กดปุ่ม **🔄 ดึงข้อมูลใหม่จาก Sheets** เพื่อโหลดข้อมูลล่าสุด
3. คลิกชื่อลูกค้าใน sidebar เพื่อดูรายละเอียด

> **ทุกตัวเลขมาจาก Google Sheets** — แก้ยอดใน Sheet แล้วกด refresh ทุกอย่างอัปเดต + จัดอันดับใหม่อัตโนมัติ

---

## 🛠️ เทคโนโลยี

| ส่วน | เทคโนโลยี |
|---|---|
| โครงสร้าง | HTML5 + CSS + Vanilla JavaScript |
| กราฟ | [Chart.js](https://www.chartjs.org/) 4.4.1 + datalabels |
| ฟอนต์ | IBM Plex Sans Thai / IBM Plex Mono |
| แหล่งข้อมูล | Google Sheets (export CSV) |

ทุก library โหลดจาก CDN — เปิดไฟล์ได้เลยไม่ต้องติดตั้งอะไร

---

## ⚙️ การตั้งค่า

ค่า config สำคัญอยู่ช่วงต้นของ `<script>` ใน `index.html`

```javascript
// Spreadsheet ID และแท็บ (gid) ของแต่ละสินค้า
var SID='1arsUj_szRLUAn6uxaKYRy7Q9xfueAd7zUZXBbazN-ug';
var GIDS={ytr:'820992683',mar:'153991926',ivqf:'2045781807',fur:'355730483'};

// เป้าหมาย Capacity และสีประจำสินค้า
var CFG={
  ytr: {n:'YTR',     cap:1200,mo:100,c:'#0d9488', ...},
  mar: {n:'Marinade',cap:4560,mo:380,c:'#2563eb', ...},
  ...
};
```

### ⚠️ สำคัญ — สิทธิ์ Google Sheet
ต้องตั้งค่า **Share → Anyone with the link → Viewer**
ถ้าเป็น Private ระบบจะดึงข้อมูลไม่ได้

### เพิ่มลูกค้าใหม่
เพิ่ม mapping ชื่อ → key ใน `N2K`
```javascript
var N2K={
  'OKAYA (Kanematsu)':'okaya_kan',
  'ชื่อลูกค้าใหม่':'key_ใหม่',
  ...
};
```

---

## 📦 Deploy (GitHub Pages)

1. อัปโหลดไฟล์ `index.html` ขึ้น repo
2. ไปที่ **Settings → Pages → Source: main branch**
3. รอ ~1 นาที จะได้ URL `https://{username}.github.io/{repo}/`

---

## 🐛 Troubleshooting

| อาการ | วิธีแก้ |
|---|---|
| ข้อมูลไม่ขึ้น / ค้างค่า default | ตั้ง Share Sheet เป็น Anyone with link (Viewer) |
| ลูกค้าใหม่ไม่ปรากฏ | เพิ่ม mapping ใน `N2K` |
| ขึ้น "⚠️ บางส่วน" | เปิด Console (F12) ดู error ของแต่ละ gid |
| กราฟไม่แสดง | ตรวจการเชื่อมต่ออินเทอร์เน็ต (CDN) |

---

## 📁 โครงสร้าง

```
special-product/
├── index.html      # ไฟล์หลัก (HTML + CSS + JS ทั้งหมด)
├── README.md       # เอกสารนี้
└── handoff.md      # เอกสารส่งต่องานแบบละเอียด
```

ดูรายละเอียดเชิงลึกได้ที่ [`handoff.md`](./handoff.md)

---

## 👥 ทีม

NICHA (ผจก) • NET • KAN • EMMA
