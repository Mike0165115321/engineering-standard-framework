# Agent Instructions — Engineering Standard Framework

> ให้ AI agent อ่านนี้ก่อนทำงานในระบบที่ใช้มาตรฐานนี้

## กฎพื้นฐาน

1. ห้ามออกแบบ architecture เอง — ต้องใช้ standard ที่กำหนด
2. ทุกฟังก์ชันต้องทำตาม function-level standards
3. ก่อนเขียน module ใหม่ → เช็ค STANDARD-CRUD.md หรือ STANDARD-PIPELINE.md
4. Error path ต้อง cover ทุกครั้ง
5. Definition of Done ผ่านก่อนบอกเสร็จ

## ไฟล์ที่ต้องอ่านก่อนทำงาน

1. `FRAMEWORK.md` — เข้าใจ meta-standard
2. `types/STANDARD-*.md` — เลือกให้ตรงกับประเภทระบบ
3. `function-standards/FUNCTION-*.md` — ใช้กับทุกฟังก์ชัน
