# Engineering Standard Framework

> มาตรฐานระบบของ Mike — สำหรับสร้างระบบคุณภาพสูงในยุค AI
>
> Framework นี้ไม่ใช่ template โค้ด แต่เป็น **มาตรฐานที่ใช้กำหนดมาตรฐานอีกรอบ** (Meta-Standard)
> เพื่อให้ทุกระบบที่สร้างมีโครงสร้าง ความคิด และคุณภาพเดียวกัน

## โครงสร้าง

```
FRAMEWORK.md              ← Meta: definition ของ "1 ระบบที่ดี"
types/
├── STANDARD-CRUD.md      ← มาตรฐานระบบ CRUD-heavy (booking, ecommerce)
└── STANDARD-PIPELINE.md   ← มาตรฐานระบบ Pipeline-heavy (AI agent, workflow)
function-standards/
├── FUNCTION-AUTH.md      ← มาตรฐานฟังก์ชัน authentication
├── FUNCTION-CRUD.md      ← มาตรฐานฟังก์ชัน CRUD
└── FUNCTION-ERROR.md     ← มาตรฐาน error handling
agent/
├── AGENTS.md             ← คำสั่งสำหรับ AI agent ก่อนแตะโค้ด
└── prompts-template.md   ← prompt templates สำหรับงานซ้ำ
modules/                  ← มาตรฐาน module ข้ามระบบ (auth, RBAC, audit)
examples/                 ← ตัวอย่างการใช้งานจริง
```

## วิธีใช้

1. อ่าน `FRAMEWORK.md` — ทำความเข้าใจปรัชญา
2. เลือก type ที่ตรงกับระบบ → `types/`
3. ใช้ function-standards กับทุกฟังก์ชัน
4. ให้ AI agent อ่าน `agent/AGENTS.md` ก่อนเขียนโค้ด
