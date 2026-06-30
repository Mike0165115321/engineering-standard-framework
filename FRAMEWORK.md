# Engineering Standard Framework (Meta-Standard)

> **Version:** 0.1 — Skeleton
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

กฎสถาปัตยกรรมของระบบนี้ — Layer flow, dependency direction, cross-cutting concerns

## 4. Function Level Standard

ทุกรอบที่ AI เขียนฟังก์ชัน ต้องมีของพวกนี้ — ดูเพิ่มที่ `function-standards/`

## 5. Definition of Done

เช็คลิสต์ก่อนบอกว่า "เสร็จ"

## 6. Agent Instructions

สิ่งที่ AI ต้องรู้ก่อนแตะโค้ด — ดูเพิ่มที่ `agent/AGENTS.md`
