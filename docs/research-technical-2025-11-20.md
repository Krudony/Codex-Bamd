# Technical Research Notes (greenfield)

## Technical Question
- เลือกเฟรมเวิร์กเว็บสำหรับเว็บโรงเรียน (เว็บแนะนำโรงเรียน/ข่าวสาร) และต้องการแนะนำฟังก์ชันอื่นๆ

## Project Context
- Greenfield: เริ่มใหม่ ไม่มีระบบเดิม
- ประเภท: เว็บแนะนำโรงเรียนบ้านแม่ทราย + ข่าวสาร
- ฟังก์ชัน: เน้นเนื้อหา/ข่าวสาร และต้องการแนะนำฟีเจอร์เสริม

## Functional Requirements (to confirm)
- [x] เว็บคอนเทนต์เผยแพร่ข่าว/ประกาศโรงเรียน
- [x] หน้าแนะนำโรงเรียน ห้องเรียน/หลักสูตร/ครู
- [x] ปฏิทินกิจกรรม/ประกาศวันสำคัญ
- [x] ช่องทางติดต่อ/แผนที่/ฟอร์มติดต่อ
- [x] รองรับมือถือ (responsive)
- [ ] หลายภาษา (ไทย/อังกฤษ) — ยังไม่ยืนยัน
- [x] SEO-friendly และโหลดเร็ว
- [x] ระบบอัปเดตคอนเทนต์ง่าย (CMS/ไฟล์/หัวไร้)

## Non-Functional Requirements (to confirm)
- [x] Performance: โหลดเร็ว (LCP, FID, CLS ดี)
- [x] SEO-first
- [x] Security: HTTPS, ฟอร์มป้องกันสแปม
- [x] Availability: โฮสเสถียร ดูแลน้อย
- [x] Maintainability: งานดูแลง่าย บุคลากรทั่วไปแก้ได้
- [x] Deploy ง่าย (CI/CD หรือ deploy ปุ่มเดียว)
- [x] ต้นทุนโฮสต่ำ/ฟรี

## Constraints (to confirm)
- [x] สแต็กที่ต้องการ: Next.js + Tailwind CSS + Framer Motion (ระบุ Vite ด้วย — ต้องตรวจว่าอยากใช้ Vite + React SPA/SSR อื่น หรือยึด Next เป็นหลัก)
- [x] UI kit/component: shadcn/ui เพิ่มเติม
- [x] โฮสติ้ง: Vercel
- [x] งบประมาณ: ต่ำ/ฟรี
- [ ] ทีม: dev กี่คน ระดับไหน — ยังไม่ยืนยัน
- [ ] Timeline: มีเดดไลน์ไหม — ยังไม่ยืนยัน
- [ ] ดีไซน์เทมเพลต: ต้องการ Figma template ประกอบ (ระบุธีมหรือสไตล์ถ้ามี)

## Technology Options (offline baseline - ต้องตรวจสอบเวอร์ชันล่าสุดจากเว็บ)
- ทางเลือก A (แนะนำหลัก): Next.js (App Router, SSR/SSG/ISR) + Tailwind CSS + shadcn/ui + Framer Motion, โฮส Vercel, ใช้ Turbopack (dev/build) แทน Vite
  - เหมาะกับ SEO, ISR สำหรับข่าว/ประกาศ, ฟอร์มติดต่อใช้ API routes หรือ third-party (Formspree/Resend)
  - คอนเทนต์: MDX/Contentlayer หรือ headless CMS (Sanity/Storyblok/Notion API) ตามความถนัด
  - i18n: next-intl/next-i18next หากต้องหลายภาษา (ตอนนี้ระบุภาษาไทยอย่างเดียว)
- ทางเลือก B (เสริม/เฉพาะจุด): Vite + React + Tailwind + shadcn/ui + Framer Motion
  - ใช้เป็น playground/component preview หรือ microsite แบบ static/CSR ง่ายและเร็ว
  - หากต้อง SSG/SEO แบบ static ล้วน อาจพิจารณา Astro + React components (ยังต้องตรวจเวอร์ชันล่าสุด)
- ดีไซน์/เทมเพลต: โทนสีสันสดใส, ควรหา Figma template (school/education/bright) มาประกอบ แล้วดึง tokens/spacing ไปยัง Tailwind/shadcn
