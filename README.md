# Engineering Standard Framework

> Engineering Standard Framework หรือ ESF คือกรอบมาตรฐานสำหรับการออกแบบ เขียน ตรวจ และดูแลระบบซอฟต์แวร์ โดยไม่ผูกติดกับภาษา โปรแกรม หรือเครื่องมือใดเครื่องมือหนึ่ง
>
> ESF ให้ความสำคัญกับสถาปัตยกรรม ความชัดเจนของความรับผิดชอบ การบำรุงรักษาระยะยาว และการทำงานร่วมกันระหว่างมนุษย์กับ AI

## Core Idea

Language can change.  
Tools can change.  
Architecture decides whether the system survives.

## Goals

- Make software systems easier to understand
- Reduce technical debt
- Improve maintainability
- Create shared standards for humans and AI
- Prevent fast development from destroying system structure

## Structure

```
FRAMEWORK.md              ← Meta: definition ของ "1 ระบบที่ดี" (+ ปรัชญา, Architecture Rules, DoD, ADR)
types/
├── STANDARD-CRUD.md      ← มาตรฐานระบบ CRUD-heavy (booking, ecommerce)
└── STANDARD-PIPELINE.md   ← มาตรฐานระบบ Pipeline-heavy (AI agent, workflow)
function-standards/
├── FUNCTION-AUTH.md      ← มาตรฐานฟังก์ชัน authentication
├── FUNCTION-CRUD.md      ← มาตรฐานฟังก์ชัน CRUD (รวม DI pattern, function size, reason-to-change)
├── FUNCTION-SERVICE.md   ← มาตรฐาน service layer + StandardResponse format
└── FUNCTION-ERROR.md     ← มาตรฐาน error handling
templates/                ← Architecture templates (system-boundary, module-map, ADR, risk, questions)
agent/
├── AGENTS.md             ← คำสั่งสำหรับ AI agent (+ deletion test, layer violation check)
└── prompts-template.md   ← prompt templates สำหรับงานซ้ำ
modules/                  ← มาตรฐาน module ข้ามระบบ (auth, RBAC, audit)
examples/                 ← ตัวอย่างการใช้งานจริง
```

## Usage

1. อ่าน `FRAMEWORK.md` — ทำความเข้าใจปรัชญา
2. เลือก type ที่ตรงกับระบบ → `types/`
3. ใช้ function-standards กับทุกฟังก์ชัน
4. ให้ AI agent อ่าน `agent/AGENTS.md` ก่อนเขียนโค้ด

## Status

ESF is currently in early development.

Version: v0.1
