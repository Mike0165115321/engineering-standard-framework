# Engineering Standard Framework (Meta-Standard)

> **Version:** 0.2 — +ปรัชญา +Architecture Rules +DoD +ADR
> **Owner:** Mike
> **Philosophy:** แม่แบบสำคัญมากในยุค AI — Template มีไว้ช่วย AI ไม่ให้เดา

## 1. System Identity

ระบบทุกระบบต้องมี identity ชัดเจน:

```
SYSTEM_NAME:
SYSTEM_FAMILY:    CRUD-heavy | Pipeline-heavy | Hybrid
SCOPE:            Internal / External / Multi-tenant
BASE_STACK:
CRITICAL_RULES:
```

## 2. Structure Standard

โครงสร้างตายตัวที่ AI ต้องเดินตาม — ดูเพิ่มที่ `types/`

## 3. Architecture Rules

### Evidence-First
- ห้ามออกแบบก่อน inspect โค้ด/ระบบจริง
- ห้ามแก้โค้ดก่อนเข้าใจ architecture ที่เกี่ยวข้อง
- แยกให้ชัด: **Confirmed facts / Reasonable inferences / Proposed / Assumptions / Open questions / Risks / Decisions**
- อย่าเดา — ถ้าไม่รู้ ให้ถามก่อน

### Depth Over Shallowness
- **Deep module** = interface เล็ก แต่ behavior เยอะ (leverage สูง)
- **Shallow module** = interface เกือบเท่า implementation (ผ่านข้อมูลเฉยๆ)
- **Deletion test:** ลบ module นี้แล้ว complexity หายไปรึเปล่า? ถ้าหาย = pass-through
- ออกแบบให้ deep — อย่าสร้าง pass-through layers

### Layer Flow (CRUD)
```
Controller → Service → Repository → Model
API layer   → Service layer → Data layer
```
- **ห้าม:** controller เรียก repository ตรง, service เรียก service อื่นข้าม layer
- **ห้าม:** layer ล่าง import layer บน

### Cross-Cutting Concerns
- Auth, audit, logging — ผ่าน middleware / decorator / interceptor
- ห้ามเขียน auth logic ในทุกฟังก์ชันซ้ำๆ

## 4. Function-Level Standard

ทุกรอบที่ AI เขียนฟังก์ชัน ต้องมีของพวกนี้ — ดูเพิ่มที่ `function-standards/`

**กติกาพื้นฐาน:**
- 1 ฟังก์ชัน = 1 หน้าที่ (Single Responsibility)
- 20-50 บรรทัดต่อฟังก์ชัน
- docstring + type hints ทุก public function
- validate input → authorize → execute → return standard response
- structured exception (ไม่ใช่ raise Exception เปล่า)
- log entry + exit ทุก service function

## 5. Definition of Done

เช็คลิสต์ก่อนบอก "เสร็จ" — ใช้ Checkpoint Gates:

- **Structure gate:** โค้ดตรง structure standard ไหม?
- **Function gate:** function-level standards ครบไหม?
- **Error gate:** error path cover? (not found, conflict, unauthorized, validation)
- **Safety gate:** transaction safety cover? (ถ้าเป็น CRUD)
- **Regression gate:** no regression?
- **Agent gate:** AGENTS.md อัปเดต? (ถ้ามี decision ใหม่)

ผ่านทุก gate ก่อนบอกเสร็จ

## 6. Decision Records (ADR)

ทุก decision ที่มีผลต่อ architecture ต้องบันทึก:

```
# ADR-{number}: {title}
Context:    สถานการณ์ / ปัญหา
Decision:   เลือกอะไร
Consequence: ดี / เสีย อะไรบ้าง
Status:     Proposed | Accepted | Deprecated
```

ป้องกัน AI กลับคำหรือเปลี่ยน architecture โดยไม่รู้

## 7. Agent Instructions

สิ่งที่ AI ต้องรู้ก่อนแตะโค้ด — ดูเพิ่มที่ `agent/AGENTS.md`
