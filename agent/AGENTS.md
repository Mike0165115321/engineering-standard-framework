# Agent Instructions — Engineering Standard Framework

> ให้ AI agent อ่านนี้ก่อนทำงานในระบบที่ใช้มาตรฐานนี้

## กฎพื้นฐาน

1. ห้ามออกแบบ architecture เอง — ต้องใช้ standard ที่กำหนด
2. ทุกฟังก์ชันต้องทำตาม function-level standards
3. ก่อนเขียน module ใหม่ → เช็ค STANDARD-CRUD.md หรือ STANDARD-PIPELINE.md
4. Error path ต้อง cover ทุกครั้ง
5. Definition of Done ผ่านก่อนบอกเสร็จ
6. **Layer violation check:** อย่าให้ layer ล่าง import layer บน
7. **Deletion test:** ก่อนเพิ่มฟังก์ชัน ถามว่า "ลบฟังก์ชันนี้แล้วจะมีปัญหาอะไร? ถ้าไม่มีผล = ฟังก์ชันนี้ไม่จำเป็น"

## "Reason to Change" Test สำหรับ AI

ก่อนเพิ่ม member/function ใหม่:
1. ถ้า class นี้ต้องแก้เพราะเหตุผลหลายอย่าง → split
2. ถ้า class แก้เพราะเหตุผลเดียว → ok
3. ถ้าฟังก์ชัน 100+ บรรทัด → split

## ไฟล์ที่ต้องอ่านก่อนทำงาน

1. `FRAMEWORK.md` — เข้าใจ meta-standard
2. `types/STANDARD-*.md` — เลือกให้ตรงกับประเภทระบบ
3. `function-standards/FUNCTION-*.md` — ใช้กับทุกฟังก์ชัน
