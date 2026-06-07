---
name: Special Products Dashboard
description: แดชบอร์ดติดตามยอดขายสินค้า Special Products (ตลาดญี่ปุ่น) แบบ real-time
colors:
  ink: "#0f1f3d"
  slate: "#3d5277"
  muted: "#8fa3bf"
  body-bg: "#eef2f7"
  surface: "#ffffff"
  border-hard: "#d4dce8"
  border-soft: "#d0dcea"
  ytr-teal: "#0d9488"
  ytr-teal-tint: "#ccfbf1"
  marinade-blue: "#2563eb"
  marinade-blue-tint: "#dbeafe"
  ivqf-orange: "#e07b39"
  ivqf-orange-tint: "#fff0e6"
  fur-purple: "#7c3aed"
  fur-purple-tint: "#ede9fe"
  status-red: "#c0392b"
  status-red-tint: "#fde8e6"
  status-amber: "#b45309"
  status-amber-tint: "#fef3c7"
  status-green: "#0d6e4f"
  status-green-tint: "#d1fae5"
typography:
  display:
    fontFamily: "IBM Plex Mono, ui-monospace, monospace"
    fontSize: "32px"
    fontWeight: 700
    lineHeight: 1
    letterSpacing: "-1px"
  headline:
    fontFamily: "IBM Plex Sans Thai, sans-serif"
    fontSize: "20px"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "-0.4px"
  title:
    fontFamily: "IBM Plex Sans Thai, sans-serif"
    fontSize: "13px"
    fontWeight: 600
    lineHeight: 1.4
    letterSpacing: "normal"
  body:
    fontFamily: "IBM Plex Sans Thai, sans-serif"
    fontSize: "13px"
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: "normal"
  metric:
    fontFamily: "IBM Plex Mono, ui-monospace, monospace"
    fontSize: "20px"
    fontWeight: 600
    lineHeight: 1
    letterSpacing: "-0.5px"
  label:
    fontFamily: "IBM Plex Sans Thai, sans-serif"
    fontSize: "10px"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "0.07em"
rounded:
  sm: "8px"
  md: "12px"
  lg: "16px"
  pill: "20px"
spacing:
  xs: "6px"
  sm: "10px"
  md: "12px"
  lg: "18px"
  xl: "22px"
components:
  button-primary:
    backgroundColor: "{colors.marinade-blue}"
    textColor: "{colors.surface}"
    rounded: "{rounded.sm}"
    padding: "7px 14px"
  card:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.lg}"
    padding: "18px"
  nav-item:
    textColor: "{colors.slate}"
    rounded: "{rounded.sm}"
    padding: "6px 12px"
  nav-item-active:
    backgroundColor: "{colors.marinade-blue}"
    textColor: "{colors.surface}"
    rounded: "{rounded.sm}"
  tag-pill:
    rounded: "{rounded.pill}"
    padding: "2px 8px"
    typography: "{typography.label}"
---

# Design System: Special Products Dashboard

## 1. Overview

**Creative North Star: "The Frosted Glass Cockpit"**

นี่คือห้องนักบินโปร่งแสง: แผงควบคุมที่ลอยอยู่บนพื้นฟ้าหม่นนุ่ม ๆ ทุกพื้นผิวเป็นกระจกฝ้า (backdrop-blur) ที่ปล่อยให้สีพื้นเรือง ๆ ลอดผ่านได้ ไม่ทึบตัน ตัวเลขทุกตัวคมชัด เรียงด้วยฟอนต์ monospace เหมือนหน้าจอเครื่องมือระดับมืออาชีพ ความรู้สึกโดยรวมคือ "แพง สงบ และเชื่อถือได้" ผู้ใช้เปิดมาแล้วรู้สึกว่ากำลังมองแดชบอร์ดที่ผ่านการออกแบบมาอย่างประณีต ไม่ใช่สเปรดชีตที่ถูกแต่งหน้า

ระบบนี้สื่อสารด้วยลำดับชั้นและความสงบ ไม่ใช่ด้วยเส้นกรอบหนาหรือสีจัด พื้นหลังฟ้าอมเทา (#eef2f7) มี radial gradient จาง ๆ สามจุดให้มิติ การ์ดสีขาวลอยขึ้นมาด้วยเงานุ่มสีกรมท่า ส่วน header กับ sidebar เป็นกระจกฝ้ากึ่งโปร่งใส สีประจำสินค้าสี่ตัว (teal / blue / orange / purple) ทำหน้าที่เป็นรหัสสีนำทาง ไม่ใช่ของตกแต่ง ทุกครั้งที่เห็นสีหนึ่ง มันหมายถึงสินค้าตัวเดียวกันเสมอ

ระบบนี้ปฏิเสธอย่างชัดเจน: หน้าตาแบบ Excel หรือตารางดิบที่ตัวเลขเรียงทึบไร้ลำดับ, template สำเร็จรูป (Bootstrap default / AI dashboard ทั่วไป), และการยัดทุกอย่างลงหน้าเดียวจนรก สีเทาอ่อนเพื่อ "ความหรู" จนอ่านไม่ออกก็เป็นสิ่งต้องห้าม

**Key Characteristics:**
- ตัวเลขเป็น monospace เสมอ คมชัด อ่านง่าย ดูแม่นยำ
- พื้นผิวกระจกฝ้าโปร่งแสง (backdrop-blur) บน header และ sidebar
- เงานุ่มสีกรมท่า ไม่ใช่เงาดำ ให้การ์ดลอยอย่างสุภาพ
- สีประจำสินค้าสี่ตัวเป็นรหัสนำทางที่คงที่ทั้งระบบ
- พื้นที่ว่างและลำดับชั้น แทนเส้นกรอบหนาและสีจัด

## 2. Colors

พาเลตต์เป็นโทนฟ้า-กรมท่าเย็น สงบและเป็นมืออาชีพ โดยมีสีประจำสินค้าสี่ตัวเป็นจุดสีที่ใช้เพื่อสื่อความหมาย ไม่ใช่ตกแต่ง

### Primary
- **Marinade Blue** (#2563eb): สีแอ็กชันหลักของระบบ ใช้กับปุ่ม refresh, รายการ sidebar ที่ active และเป็นสีประจำสินค้า Marinade ปรากฏน้อยแต่เด่นชัด นำสายตาไปที่สิ่งที่กดได้
- **Navy Ink** (#0f1f3d): สีตัวอักษรหลักและหัวข้อ เป็นจุดที่มืดและหนักที่สุดของพาเลตต์ ใช้กับทุกข้อความสำคัญและตัวเลข

### Secondary (สีประจำสินค้า — รหัสนำทาง)
- **YTR Teal** (#0d9488 / tint #ccfbf1): สินค้า YTR และกลุ่มลูกค้า Star
- **IVQF Orange** (#e07b39 / tint #fff0e6): สินค้า IVQF
- **FUR Purple** (#7c3aed / tint #ede9fe): สินค้า FUR

### Tertiary (สถานะ)
- **Status Green** (#0d6e4f / tint #d1fae5): ถึงเป้า / เติบโตบวก
- **Status Amber** (#b45309 / tint #fef3c7): ต้องเฝ้าดู (กลุ่ม Watch)
- **Status Red** (#c0392b / tint #fde8e6): ต้องกระตุ้น / ติดลบ (กลุ่ม Activate)

### Neutral
- **Body Sky** (#eef2f7): พื้นหลังหน้าจอ ฟ้าอมเทาอ่อน มี radial gradient จาง ๆ ให้มิติ
- **Surface White** (#ffffff): พื้นการ์ดและแผงทั้งหมด
- **Slate** (#3d5277): ข้อความรอง คำอธิบาย
- **Muted** (#8fa3bf): label เล็ก ๆ และค่าที่ไม่ใช่จุดเด่น **ห้ามใช้กับเนื้อหาที่ต้องอ่านยาว**
- **Border Soft** (#d0dcea) / **Border Hard** (#d4dce8): เส้นกรอบการ์ดและตัวคั่น บาง 1px เสมอ

### Named Rules
**The Color-Means-Product Rule.** สีประจำสินค้าทั้งสี่ (teal / blue / orange / purple) ผูกกับสินค้าตัวเดียวกันเสมอทั้งระบบ ห้ามนำไปใช้เป็นสีตกแต่งทั่วไป เห็นสีไหน = สินค้านั้น

**The Tinted-Shadow Rule.** เงาทุกอันใช้สีกรมท่าโปร่งแสง `rgba(15,31,61,...)` ไม่ใช่สีดำ เงาดำจะทำให้งานดูถูกและขัดกับโทนฟ้าเย็น

## 3. Typography

**Display / Metric Font:** IBM Plex Mono (fallback ui-monospace, monospace)
**Body & Heading Font:** IBM Plex Sans Thai (fallback sans-serif)

**Character:** การจับคู่นี้แยกหน้าที่ชัดเจน — ตัวเลขทุกตัวเป็น monospace ทำให้เรียงตรงเป็นคอลัมน์และดูแม่นยำน่าเชื่อถือ ส่วนข้อความและหัวข้อภาษาไทยใช้ IBM Plex Sans Thai ที่อ่านง่ายและสะอาดตาในขนาดเล็ก คอนทราสต์ระหว่าง "ตัวอักษร humanist" กับ "ตัวเลข mechanical" คือเอกลักษณ์ของระบบ

### Hierarchy
- **Display / Metric** (Mono 700, 32px, line-height 1, letter-spacing -1px): ตัวเลขเด่นที่สุด เช่นยอดรวมใน status card ตัวเลขที่ใช้ตัดสินใจ
- **Headline** (Sans Thai 600, 20px, letter-spacing -0.4px): หัวข้อ panel
- **Metric** (Mono 600, 20–23px): ตัวเลขสรุปใน stat box และ overview card
- **Title** (Sans Thai 600, 13px): ชื่อหัวข้อการ์ด ชื่อลูกค้าในตาราง
- **Body** (Sans Thai 400, 13px, line-height 1.55): เนื้อหาทั่วไป
- **Label** (Sans Thai 600, 9–11px, letter-spacing 0.07em, UPPERCASE): label หมวด, หัวคอลัมน์ตาราง ใช้กับข้อความสั้น ≤4 คำเท่านั้น

### Named Rules
**The Mono-For-Numbers Rule.** ทุกตัวเลขในระบบ (ยอด, %, อันดับ, ปี) ใช้ IBM Plex Mono เสมอ ห้ามใช้ฟอนต์ sans กับตัวเลข เพราะ monospace คือสิ่งที่ทำให้แดชบอร์ดดูแม่นยำและเป็นมืออาชีพ

## 4. Elevation

ระบบนี้ใช้ "เงานุ่มสีกรมท่า + กระจกฝ้า" เป็นภาษาความลึก ไม่ใช่เส้นกรอบหนา การ์ดลอยขึ้นมาจากพื้นฟ้าด้วยเงาฟุ้งสองชั้น (ambient + contact) ทุกเงาใช้ `rgba(15,31,61,...)` สีกรมท่า ส่วน header และ sidebar เป็นกระจกฝ้า (`backdrop-filter: blur`) ที่ปล่อยให้พื้นหลังเรืองลอดผ่าน สร้างความรู้สึกเป็นชั้น ๆ แบบห้องนักบิน

### Shadow Vocabulary
- **Card resting** (`box-shadow: 0 4px 18px rgba(15,31,61,.09), 0 1px 5px rgba(15,31,61,.05)`): เงาพักของการ์ดและแผงทั่วไป
- **Card elevated** (`box-shadow: 0 5px 22px rgba(15,31,61,.10), 0 1px 5px rgba(15,31,61,.06)`): การ์ด overview ที่เด่นขึ้นเล็กน้อย
- **Card hover** (`box-shadow: 0 12px 36px rgba(15,31,61,.15), 0 2px 8px rgba(15,31,61,.07)` + `translateY(-3px)`): ตอบสนองเมื่อ hover ยกตัวขึ้น
- **Action glow** (`box-shadow: 0 2px 12px rgba(30,87,153,.3)`): เงาเรืองสีน้ำเงินใต้ปุ่มหลักและรายการ active
- **Glass surface** (`backdrop-filter: blur(18–20px)` + `background: rgba(255,255,255,.65–.78)`): header และ sidebar

### Named Rules
**The Lift-On-Hover Rule.** การ์ดที่กดได้จะยกตัว (`translateY(-3px)`) พร้อมเงาเข้มขึ้นเมื่อ hover ส่วนการ์ดข้อมูลเฉย ๆ ไม่ยก เงาบอกว่า "อันนี้โต้ตอบได้"

## 5. Components

### Buttons
- **Shape:** มุมโค้งนุ่ม (8px radius)
- **Primary:** พื้น Marinade Blue (#2563eb) ตัวอักษรขาว padding 7px 14px พร้อม action glow ใต้ปุ่ม font-weight 500
- **Hover / Focus:** คงสีน้ำเงิน เงาเรืองชัดขึ้น สถานะ disabled ลด opacity เหลือ .55
- **Icon + label:** ปุ่มหลักมักมีอีโมจิ/ไอคอนนำหน้าข้อความ จัด flex gap 6px

### Tags / Badges
- **Style:** pill (20px radius) ขนาดเล็ก font 9–10px weight 500–600 พื้นใช้ tint ของสีที่สื่อ (เช่น สถานะเขียว/เหลือง/แดง) ตัวอักษรใช้สีเข้มของ hue เดียวกัน
- **Badge ตัวเลข:** ใช้ฟอนต์ Mono เสมอ

### Cards / Containers
- **Corner Style:** การ์ดหลัก 16px, status card 12px
- **Background:** ขาวล้วน (#fff)
- **Shadow Strategy:** ดู Elevation — resting เป็นค่าเริ่มต้น, hover ยกตัวเฉพาะการ์ดที่กดได้
- **Border:** บาง 1px สี #d0dcea เสมอ ห้ามหนากว่านี้
- **Internal Padding:** 16–18px

### Navigation (Sidebar)
- **Style:** กระจกฝ้า (`rgba(255,255,255,.65)` + blur 20px) กว้าง 210px sticky เต็มความสูง
- **รายการ (.ni):** radius 8px มี dot สีประจำสินค้า/สถานะนำหน้า + ชื่อ + ค่ายอด (Mono) ด้านขวา
- **Default / Hover / Active:** hover พื้นฟ้าจาง `rgba(30,87,153,.07)`; active พื้น Marinade Blue ตัวอักษรขาว + action glow
- **กลุ่ม:** หัวกลุ่มเป็น label uppercase พับเก็บได้ (accordion) มีลูกศรหมุน 90°

### Status Card (Signature Component)
การ์ด 2×2 ต่อสินค้า: หัวการ์ดมี dot สีสินค้า + ชื่อสินค้า uppercase; ฝั่งซ้ายเป็นตัวเลขหลัก 32px Mono + แถบ progress เทียบเป้า; ฝั่งขวาเป็นแถวเทรนด์รายปี (bar + ค่า) การ์ดที่ไม่มีข้อมูลใช้ `.dim` (opacity .32) แทนการซ่อน เพื่อคงโครงสร้าง

## 6. Do's and Don'ts

### Do:
- **Do** ใช้ IBM Plex Mono กับตัวเลขทุกตัว (ยอด, %, อันดับ, ปี) เสมอ
- **Do** ผูกสีประจำสินค้า (teal/blue/orange/purple) กับสินค้าตัวเดิมทั้งระบบ ใช้สีเป็นรหัสนำทาง
- **Do** ใช้เงาสีกรมท่าโปร่งแสง `rgba(15,31,61,...)` กับทุกพื้นผิวที่ลอย
- **Do** ใช้เส้นกรอบบาง 1px (#d0dcea) และพื้นที่ว่างเพื่อแบ่งส่วน แทนเส้นหนาหรือสีจัด
- **Do** ยกการ์ดที่กดได้ขึ้นเมื่อ hover (`translateY(-3px)`) เพื่อบอกว่าโต้ตอบได้
- **Do** ทำให้สถานะภาพรวมเห็นได้ทันทีที่ first paint รายละเอียดค่อยเจาะผ่าน sidebar

### Don't:
- **Don't** ทำให้หน้าตาเหมือน Excel หรือตารางดิบ — ตัวเลขเรียงทึบเป็นแถวไร้ลำดับความสำคัญทางสายตา
- **Don't** ทำให้ดูเหมือน template สำเร็จรูป (Bootstrap default, AI dashboard ทั่วไป) ที่ใครก็ทำได้
- **Don't** ยัดทุกอย่างลงหน้าเดียวจนรกหรือซับซ้อนเกินไป — เบาแต่ไม่ขาด
- **Don't** ใช้สี Muted (#8fa3bf) กับเนื้อหาที่ต้องอ่านยาว ใช้ได้เฉพาะ label เล็ก ๆ (เสี่ยงคอนทราสต์ต่ำกว่า 4.5:1)
- **Don't** ใช้เงาสีดำ — ขัดกับโทนฟ้าเย็นและทำให้ดูถูก
- **Don't** สื่อสถานะด้วยสีอย่างเดียว ต้องมีตัวเลข ป้าย หรือไอคอนกำกับ (เผื่อ color blindness)
- **Don't** ใช้กรอบหนากว่า 1px หรือ border-left สีเป็นแถบบนการ์ด
