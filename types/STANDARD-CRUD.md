# STANDARD-CRUD

> สำหรับระบบ CRUD-heavy: ระบบจอง, ecommerce, ระบบบริหารทั่วไป
> **Family:** CRUD-heavy — Transaction safety > Performance, DB-first

## Architecture

### Layer Flow (บังคับ)
```
Controller (API) → Service (Business Logic) → Repository (Data Access) → Model (Schema)
```

### Layer Rules
| Layer | หน้าที่ | ห้าม |
|-------|--------|------|
| Controller | validate input, call service, return response | เรียก repository, เขียน business logic |
| Service | business logic, orchestration, transaction | import controller, รู้จัก HTTP |
| Repository | data access, query, ORM | มี business logic |
| Model | schema, relationship, index | มี logic ใดๆ |

### Dependency Injection
- constructor injection สำหรับทุก service + repository
- ห้าม `import` แล้ว instantiate เองในฟังก์ชัน
- เพื่อให้ test ได้โดยไม่ต้อง mock database จริง

### Function Size & Structure
- 20-50 บรรทัดต่อฟังก์ชัน
- docstring + type hints ทุก public function
- validate input → authorize → execute → return
- structured exception (ErrorCode + Message)

### Transaction Rules
- ทุก write operation ต้อง wrap ใน transaction
- rollback เมื่อ error — ไม่ให้ data ครึ่งๆ กลางๆ

## Coming Soon

- [ ] Folder structure มาตรฐาน
- [ ] CRUD function patterns (create/read/update/delete/search)
- [ ] Transaction patterns
- [ ] Locking & concurrency
- [ ] Soft-delete pattern
